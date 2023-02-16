### Separating Code into Multiple Scripts

Large projects can require thousands of lines of code. Keeping all code for a project in a single file would quickly become unweildy, as you would have to search through thousands of lines for a single line. It makes more sense to break up the code into separate scripts. This begs the question: How should I decide what to put in each script?

- each script should accomplish a single task (similar to an issue as described in  [[GitHub and GitLab#Creating an issue and its associated branch in the repo]]) and use the imperative (command) form
- use sequential numbering to make it clear which order the scripts should be run in
	- an added benefit is that the scripts will be displayed in order in your file system
- call all scripts from a single script, often prefixed with `00`
	- you only need to manually open and run this *single* script, instead of opening and running each individual script
- use [[pacman]] to load all of the packages used in a given script
	- this introduces some redundancy since the some packages will be attached in different scripts, but it makes it clear which packages are used in each script

#### Example

Running all of the scripts from a file called `00_run_pipeline.R` might look like:

```R
source("code/01_download_mortgages.R")
source("code/02_remove_outliers_and_investigate_missings.R")
source("code/03_perform_EDA.R")
source("code/04_train_xgb_model.R")
source("code/05_get_xgb_fitted_values.R")
source("code/06_plot_roc_auc_over_time.R")
```

- create [[logr]] files as part of a given script, for example, a log for `code/02_remove_outliers_and_investigate_missings.R` so that we have a record of how many observations were removed during this step


### Automate Folder Generation

#### Motivation

Automatically creating folders to store data, plots (such as [[ggplot]]s), and tables will allow you to run experiments more easily and more quickly. Examples of experiments include:

- Data
	- different data slices for training/validation/test
	- different filtering steps (only including a certain type of loan, a loan that was originated after a certain date)
- Model type and its hyperparameters (see [[tidymodels]])
- Method for selecting variables (manually choosing, automated with something like [[glmnetUtils]], or a combination)

#### Practical Steps

##### Packages
- use [[here]] to ensure that all file paths are relative and will work when other users run the code
- use [[fs]] for generating folders

1. In your `00_` pipeline script, create variables for capturing your important script hyperparameters
2. Assign a "Special Suffix" to a given run of the model
	1. this is important because there will likely be too many different script parameters to include all of them in the name. This makes sure that running 2 experiments that are similar along many (but not all ) dimensions are saved in different folders.

Example of automated folder creation

```R

LOAN_TYPE <- "jumbo"
SPECIAL_SUFFIX <- paste0("xgboost_early_stopping",
						 LOAN_TYPE, collapse = "_")

path_special_suffix <- here(SPECIAL_SUFFIX)

if (!dir_exists(path_special_suffix)) {

	dir_create(path_special_suffix)
}

path_plots <- here(path_special_suffix, "path_plots")

if (!dir_exists(path_plots)) {

	dir_create(path_plots)
}




```


### Putting it Together

Here is how `00_run_pipeline.R` might look with both running [[#Separating Code into Multiple Scripts]] and [[#Automate Folder Generation]]:


```R

# ----- Packages -------

pacman:p_load(
	fs
)

# ---------- Folder Hyperparameters --------------

LOAN_TYPE <- "jumbo"
SPECIAL_SUFFIX <- paste0("xgboost_early_stopping",
						 LOAN_TYPE, collapse = "_")

path_special_suffix <- here(SPECIAL_SUFFIX)

if (!dir_exists(path_special_suffix)) {

	dir_create(path_special_suffix)
}

path_plots <- here(path_special_suffix, "path_plots")

if (!dir_exists(path_plots)) {

	dir_create(path_plots)
}

# ------------- Running Pipeline ----------------

source("code/01_download_mortgages.R")
source("code/02_remove_outliers_and_investigate_missings.R")
source("code/03_perform_EDA.R")
source("code/04_train_xgb_model.R")
source("code/05_get_xgb_fitted_values.R")
source("code/06_plot_roc_auc_over_time.R")


```






