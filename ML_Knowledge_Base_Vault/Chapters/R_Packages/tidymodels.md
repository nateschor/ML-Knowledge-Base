Just like the [[tidyverse]] is a collection of packages that work together for data manipulation tasks, `tidymodels` is a collection of packages that work together for [modeling tasks](obsidian://open?vault=ML_Knowledge_Base_Vault&file=Chapters%2Ffigures%2Fmodeling_process.png)

- tidymodels [book](https://www.tmwr.org/)
- tidymodels cocreator Julia Silge's [blog](https://juliasilge.com/blog/) showcasing tidymodels
- R's equivalent of Python's [sklearn](https://scikit-learn.org/stable/) where steps that are common to all models regardless of the model type use the same syntax (e.g., fitting a model, performing cross-validation, selecting models based on a given metric)
	- see [parsnip](https://www.tidyverse.org/blog/2018/11/parsnip-0-0-1/)



### Example of using recipes

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