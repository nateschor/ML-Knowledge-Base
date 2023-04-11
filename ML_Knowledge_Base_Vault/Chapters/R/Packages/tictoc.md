- documentation  [here](https://cran.r-project.org/web/packages/tictoc/tictoc.pdf)

Function for taking `tictoc` timing log and turning it into a `tibble`:

```R

df_timing_log <- tic.log() %>% 
  unlist() %>%
  tibble(
	  Process = str_extract(., pattern = ".+(?=:)"),
      Time = str_extract(., pattern = "(?<=: ).+")
  ) %>% 
  select(Process, Time)
  
```

- See [[RegEx]] for info on the meaning of the symbols used to extract `Process` and `Time` 