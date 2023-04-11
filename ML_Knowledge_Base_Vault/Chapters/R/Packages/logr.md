Sends console output to a `.log` file that can be reviewed during a [[GitHub and GitLab]] pull request to check some of the topics mentioned in [[Reasoning About your Data]]. Some ideas for things to log are:
- any tibble you load, create, or save
- means of outcome variable
- tables of frequency and % for categorical variables of interest

For more details, see logr [vignette](https://cran.r-project.org/web/packages/logr/vignettes/logr.html)

```r
path_log_file <- here("file_path_to_where_you_want_to_make_the_log.log"))
log_file <- log_open(path_path_log_file, autolog = TRUE, show_notes = FALSE)

# keep logging your code 

sep("This creates a header in the log")

# send output to the log with `put()`

df %>%
	as_tibble() %>%
	put()

sep("Table of states for loans originated between 2000-2005")

log_tbl <- df %>%
	pull("state") %>%
	table(.)

put(log_tbl)


log_close()


```

### Explanation of `log_open` arguments

- `autolog = TRUE` gives automatic integration with [[tidylog]]
- `show_notes = FALSE` removes extra information around the log, like run time for every single command (which can crowd the log)