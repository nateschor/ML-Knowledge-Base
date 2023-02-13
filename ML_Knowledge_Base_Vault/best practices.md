
### Knowing the level of your data

- always know the level of the data you are working with (is it unique at the date level? The person date level? Something else?)

Use `group_by()` to quickly check if the variables you think uniquely identify observations actually do

```R

df %>%
	group_by(variable1, variable2)

```

If the number of groups from the above step is equal to the number of observations in `df`, then those variables are unique identifiers

### Checking for missing values before joining

- Joining datasets when there are `NAs` can cause the dimensions of your dataset to explode
- quickly check the number of `NAs` for each variable with

```R

df_missing <- df %>%
	map_dfr(., ~ sum(is.na(.)))

df_missing %>% 
	pivot_longer(., everything(), names_to = "variable", values_to = "number_missing")



```

