Just like the [[tidyverse]] is a collection of packages that work together for data manipulation tasks, `tidymodels` is a collection of packages that work together for modeling

![[modeling_process.png]]

- tidymodels [book](https://www.tmwr.org/)
- tidymodels cocreator Julia Silge's [blog](https://juliasilge.com/blog/) showcasing tidymodels
- R's equivalent of Python's [sklearn](https://scikit-learn.org/stable/) where steps that are common to all models regardless of the model type use the same syntax (e.g., fitting a model, performing cross-validation, selecting models based on a given metric)
	- see [parsnip](https://www.tidyverse.org/blog/2018/11/parsnip-0-0-1/)

## Tuning Model

### Using Recipes

```R
f_xgb_dummies_ <- df_training %>% 
  select(personid, date, all_of(v_lasso_vars)) %>% 
  names() %>% 
  reformulate(termlabels = ., response = "outcome")

xgb_dummies_recipe <- recipe(formula = f_xgb_dummies_, data = df_training) %>% 
  update_role("personid", "date", new_role = "id") %>% # keep ID vars, but don't use them for modeling
  step_novel(all_nominal_predictors()) %>% 
  step_dummy(all_nominal_predictors(), one_hot = FALSE) %>% # make categorical variables into dummy variables
  step_intercept() %>% 
  prep(., strings_as_factors = FALSE) # do not treat string variables as factors

df_training_baked <- bake(xgb_dummies_recipe, df_training)
df_validation_baked <- bake(xgb_dummies_recipe, df_validation) # apply training steps to validation

```

### Creating Training/Validation Split

```R

df_all_baked <- bind_rows(df_training_baked, df_validation_baked) %>% 
  mutate(
    row_id = row_number()
  )

v_training <- df_all_baked %>% 
  filter(qtr == training_qtrs) %>% 
  pull(row_id)

v_validation <- df_all_baked %>% 
  filter(qtr == validaton_qtrs) %>% 
  pull(row_id)

df_split <- validation_split(df_all_baked)

splits_plucked <- df_split %>% 
  pull(splits) %>% 
  pluck(1)

splits_plucked$in_id <- v_training
splits_plucked$out_id <- v_validation

df_split$splits[[1]] <- splits_plucked

f_xgb <- df_training_baked %>% 
  select(contains("attr")) %>% 
  names() %>% 
  reformulate(termlabels = ., response = "outcome")

xgb_spec <- boost_tree(
  trees = tune(),
  tree_depth = tune(), 
  min_n = tune(), 
  loss_reduction = tune(),                    
  sample_size = tune(), 
  mtry = tune(),         
  learn_rate = tune(),
  stop_iter = tune()
) %>% 
  set_engine("xgboost",
             event_level = "second",
             validation = .2) %>% 
  set_mode("classification")

xgb_grid <- read_csv(here("values used min and max values for hyperparameters"))

xgb_wf <- workflow() %>%
  add_formula(f_xgb) %>%
  add_model(xgb_spec)

cl <- makeCluster(3)
registerDoParallel(cl)

tic(msg = "Tuning Grid")
xgb_res <- tune_grid(xgb_wf,
                     grid = xgb_grid,
                     resamples = df_split,
                     control = control_grid(save_pred = TRUE, verbose = TRUE))
toc(log = TRUE)
stopCluster(cl)

best_model <- select_best(xgb_res, MODEL_METRIC)
write_csv(best_model, here("optimal_hyperparameters.csv"))
```


## Training Final Model

### Using Recipes

```R
xgb_recipe <- recipe(outcome ~ ., data = df_training) %>%
	update_role(personid, date, new_role = "id") %>% # keep ID vars, but don't use them for modeling
	step_discretize_xgb(all_of(v_vars_to_discretize_and_dummy)) %>%
	step_novel_all(all_of(v_vars_to_discretize_and_dummy)) %>% # make levels of categorical variables in validation but not training into a column called "other"
	step_dummy(all_of(v_vars_to_discretize_and_dummy)) %>% # make categorical variables into dummy variables
	step_intercept() %>%
	prep(., strings_as_factors = FALSE) # do not treat string variables as factors

df_training_baked <- bake(xgb_recipe, df_training)
df_validation_baked <- bake(xgb_recipe, df_validation) # apply training steps to validation


```

### Fitting Final Model

```R

xgb_formula <- df_training_baked %>% 
  select(contains("attr")) %>% 
  names() %>% 
  reformulate(termlabels = ., response = "outcome")

xgb_spec <- boost_tree(
  trees = tune(),
  tree_depth = tune(), 
  min_n = tune(), 
  loss_reduction = tune(),                    
  sample_size = tune(), 
  mtry = tune(),         
  learn_rate = tune(),
  stop_iter = tune()
) %>% 
  set_engine("xgboost",
             event_level = "second",
             validation = .2) %>% 
  set_mode("classification")


best_model <- read_csv(here("optimal_hyperparameters.csv"))

xgb_wf <- workflow() %>%
  add_formula(xgb_formula) %>%
  add_model(xgb_spec)

print("Fitting XGB final model")

tic(msg = "Fitting Final Model")

fit_xgb <- xgb_wf %>%
  finalize_workflow(best_model) %>% 
  fit(df_training_baked)

toc(log = TRUE)
```