### [furrr](https://furrr.futureverse.org/)

```R

number_workers <- 4
plan(multisession, workers = number_workers)

options(future.globals.maxSize= 10 * 1073741824) # increase allotted RAM

tic()
df_sims <- future_map_dfr(variable_mapping_over, ~ Function_for_mapping(.)) %>%
toc()

```

### [doParallel and foreach](https://cran.r-project.org/web/packages/doParallel/vignettes/gettingstartedParallel.pdf)

```R
tic()
num_cores <- 8
CL <- makeCluster(num_cores)
registerDoParallel(CL)

foreach(i = 1:NUM_MODELS, .packages = c("tidyverse", # each worker needs access to packages
                                        "fst",
                                        "tidymodels",
                                        "doParallel",
                                        "tictoc",
                                        "lubridate",
                                        "logr",
                                        "glmnet",
                                        "glmnetUtils",
                                        "fs"), 
        .export = c("SPECIAL_SUFFIX",  # global variables workers need access to
                    "CONSUMER_GROUP",
                    "NUM_MODELS",
                    "MODEL_METRIC",
                    "RAND_NO_CID",
                    "V_POTENTIAL_MODELS"), .verbose = TRUE) %dopar% { # change to %do% for sequential loop
                      
                      print(paste("Running model", i))
   
}

stopCluster(CL)
toc()
```

### Check that your parallel processing is working

- do mini [[tictoc]] experiments to confirm you are getting a speedup by taking a small sample of the data and confirm that parallelizing leads to less computation time than doing it sequentially
	- there is a startup cost to parallelizng, so make sure you use enough observations in your experiment to ensure that the parallelization speedup overcomes this hump
- If you are using *n* workers,  go to Task Manager --> Processes --> Background processes and confirming that you see *n* sessions
- if you are using a computing cluster, sign in with [PuTTY](https://www.ssh.com/academy/ssh/putty/download), `ssh where_you_are_working` and then `htop` to [monitor](https://support.cloudways.com/en/articles/5120765-how-to-monitor-system-processes-using-htop-command#:~:text=The%20htop%20is%20a%20command,different%20sections%20one%20by%20one.) that you see *n* sessions