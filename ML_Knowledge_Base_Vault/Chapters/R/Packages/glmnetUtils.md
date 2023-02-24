- [vignette](https://cran.r-project.org/web/packages/glmnetUtils/vignettes/intro.html)


### Extracting variables chosen for each $\lambda$


```R

pacman::p_load(
	tidyverse,
	tidylog,
	glmnetUtils
)

model_lasso <- glmnet(outcome_var ~ ., data = df_training, alpha = 1) 

mx_coefs <- coef(model_lasso)

df_vars_selected_for_each_lambda <- tidy(mx_coefs) %>%
	rename(
		variable = row,
		lambda_index = column,
		coefficient = value
	) %>%
	filter(variable != "(Intercept)") %>%
	select(variable, lambda_index) %>%
	group_by(lambda_index) %>%
	mutate(
		selected_vars = list(variable)
	) %>%
	distinct(lambda_index, .keep_all = TRUE)

```