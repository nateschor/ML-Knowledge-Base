This package is helpful for debugging a series of pipes. Placing `print_pipe_steps()` at the end of a piping chain will print the results of each intermediate step to the console. You can specify how you would like to print the results, such as using `glimpse()`. It has a nice synergy with [[tidylog]]. 

Below is an example:

```R
pacman::p_load(
  tidyverse,
  tidylog,
  ViewPipeSteps
)

pipe_msg <- c(
  "message(title);",
  "dplyr::glimpse(x = ps%d)" # ps%d = PowerShell command
)

mtcars %>%
  filter(cyl == 4) %>%
  group_by(carb) %>%
  summarize(
    mean_mgp = mean(mpg)
 ) %>%
  print_pipe_steps(pipe_msg, all = TRUE)
```
