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
