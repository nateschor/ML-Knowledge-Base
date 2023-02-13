- use [`glimpse()`](https://dplyr.tidyverse.org/reference/glimpse.html) when reading in a dataset to get a view of the first few rows for all columns
- can be used in middle of a pipe, like below

```R
df <- read_fst("path_to_file.fst") %>%
	glimpse() %>%
	select("relevant_columns")

```

- Put function arguments in a new line to improve readability (such as `mutate` and `summarize`)

```R
mtcars %>%
	group_by(cyl)
	mutate(
		mean_mpg = mean(mpg),
		mean_wt = mean(wt)	
	)


```