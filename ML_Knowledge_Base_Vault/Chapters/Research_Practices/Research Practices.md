
### Knowing the level of your data

- always know the level of the data you are working with (is it unique at the date level? The person-date level? Something else?)

Use `group_by()` to quickly check if the variables you think uniquely identify observations actually do

```R

df %>%
	group_by(variable1, variable2)

```

If the number of groups from the above step is equal to the number of observations in `df`, then those variables are unique identifiers

### Checking for missing values or duplicate unique ids before joining

- Joining datasets when there are `NAs` or duplicate ids can cause the dimensions of your dataset to explode
- use [[tidylog]] to make sure there are no duplicated observations when you join, and that the dimensions for x and y make sense
- quickly check the number of `NAs` for each variable with

```R

df_missing <- df %>%
	map_dfr(., ~ sum(is.na(.)))

df_missing %>% 
	pivot_longer(., everything(), names_to = "variable", values_to = "number_missing")



```

### Using explicit function arguments

In the example below, the second function omits `df` even though it is used by `Calculate_Mean`. This is a bad practice because:
1. It makes the code harder to follow, since function arguments + function = function output
2. Changes to `df` outside of `Calculate_Mean` can lead to unintended behavior

```R

# good

Calculate_Mean <- function(df, column)

	df %>%
		pull(column) %>%
		mean()

# bad

Calculate_Mean <- function(column)

	df %>%
		pull(column) %>%
		mean()



```

General reserarch project advicein in [Jesse Shapiro Practitioner's Guide](https://web.stanford.edu/~gentzkow/research/CodeAndData.pdf) 