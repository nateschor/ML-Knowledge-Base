- logr [vignette](https://cran.r-project.org/web/packages/logr/vignettes/logr.html)

```r
path_log_file <- here("file_path_to_where_you_want_to_make_the_log.log"))
log_file <- log_open(path_path_log_file, autolog = TRUE, show_notes = FALSE)

# keep logging your code 

sep("This creates a header in the log")

# send output to the log with `put()`

df %>%
	as_tibble() %>%
	put()

log_close()


```

`autolog = TRUE` gives automatic integration with [[tidylog]]
`show_notes = FALSE` removes extra information around the log, like run time for every single command (which can crowd the log)