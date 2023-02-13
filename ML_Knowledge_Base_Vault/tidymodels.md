- tidymodels [book](https://www.tmwr.org/)
- tidymodels cocreator Julia Silge's [blog](https://juliasilge.com/blog/) showcasing tidymodels

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