
# Planning a project

## Nathan TODO

1. thought about what aspects of previous projects we wanted to improve on
	- folder structure
		- folder structure led to our use of [[here]] for file paths, creating an `.RProject` at the root of the repo, and thinking about what kind of folders we would need [[Creating a Coding Pipeline#Automate Folder Generation]]
	- how we do Pull Requests
		- thinking about improving Pull Requests led to googling where [[tidylog]] was discovered, and we paired it with [[logr]] for review during pull requests
2. created the folder structure and wrote skeleton code for the pipeline script
	- We also thought about what kind of tasks needed to be completed and how to logically break them up into multiple scripts, and what the main pipeline script should look like (see [[Creating a Coding Pipeline#Separating Code into Multiple Scripts]])
3. determined what code could be reused
	- thinking about how this project would be different from CS made us realize that we'd have fewer variables in the model and that we should explore the data more, leading to us using/discovering the packages in [[EDA]]


Do a brain dump about how we planned CRISM project. With CS we didn't do it, so we made a great progress on this in a year.

# Starting a new project or managing an existing one in Git

- new project in [GitLab](https://docs.gitlab.com/ee/user/project/)
- new project in [GitHub](https://docs.github.com/en/issues/organizing-your-work-with-project-boards/managing-project-boards/creating-a-project-board)



### [[Git]]

### [[GitHub and GitLab]]

# Planning the new analyses

## Nathan TODO:

1. Chat with Vitaly, and take notes on what should be accomplished
2. Create an [Issue](https://docs.github.com/en/issues/tracking-your-work-with-issues/about-issues) for addressing the task
	1. Give a title for the issue. For example,  "Create outcome variable for defaulting"
3. In the body of the issue, create tasks to complete using `- [ ]` 
4. Send a screenshot of the issue to Vitaly, who will give edits/commits if needed

Describe the process of preparing an issue. Chat with Vitaly, take notes about what we want to do. Then create an issue based on the notes. Vitaly looks at the issue and edits/comments if needed. You plan the scripts (how do you do that, btw, Nathan, I have no idea). T

## Research Practices
- [[Reasoning About your Data]]
- [[Creating a Coding Pipeline]]


# Executing the analyses: writing new scripts or editing existing ones

#### renv

- see [[renv]] for more information about the process

1.  Get the repositorie's HTTPS  from GitLab under Clone --> Clone with HTTPS (or GitHub CLI on GitHub)
2. In the RStudio terminal, clone repo using `git clone HTTPS`. Talk with your organization's IT if getting errors at this step
3. Run `renv::init()` followed by `renv::snapshot()`
    -   note that in order for `renv::snapshot()` to "see" the package, it must be called using either `library(package_name)` or [[pacman]]`::p_load(package_name)` in a **saved script**. `renv::snapshot()` will not be able to find the package if it only lives in an untitled.R script
4.  `git add .Rprofile renv.lock renv/activate.R`
5.  `git commit -m "Adding initial packages #X"`, where X is replaced with the issue number (4 in the example)
	1. See [here](https://cbea.ms/git-commit/) for suggestions on how to write a comit message
6.  `git push`. If continually prompted for your password when using `git push` or `git pull`, talk with your organization's IT
7.  Update packages with `renv::update("package_name_as_string")`
8.  After you update or install new packages, `renv::snapshot()`
9.  `git add renv.lock`
10.  `git commit -m "Update package(s) XYZ #X"`
    - if you want to revert back to an earlier version of the package, use `renv::revert("commit_hash_for_package_version_I_want")` followed by `renv::restore()`

#### writing code

1. Create a branch that is linked to the issue. For example, if the GitHub/GitLab assigned number to the issue Create outcome variable for defaulting is 4, the name of the branch should be issue4_create_outcome_variable_for_defaulting
2. `git pull` to make your local setup synced with the repo, and then `git switch issue4_create_outcome_variable_for_defaulting` to switch to the new branch
3. Write code, committing and pushing as you make changes
	1. make sure all of your commit messages on these branch include `#4`, so that when you push the commit message and associated changes show up in the issue
	2. if you want to write a longer message, use `git commit`. It will then open up a [[vim]] editor for your commit message

## Coding Style
- [[Naming Conventions]]
- [[vim]]
- [[Formatting]]
## Tools 

## Shell 
[[Shell]]
# R

### Packages
- [[logr]]
- [[pacman]]
- [[tidymodels]]
- [[tidyverse]]
- [[tidylog]]
- [[glmnetUtils]]
- [[ggplot]]
- [[renv]]
- [[fst]]
- [[kableExtra]]
- [[lubridate]]
- [[slider]]
- [[tsibble]]
- [[data.table]]
- [[here]]
- [[fs]]
- [[tictoc]]

### Concepts
- [[EDA]]
- [[Parallel Processing]]

## RStudio
[[Shortcuts]]

## Regex
[[RegEx]]

# Having Vitaly sign off on the analyses
How does Vitaly sign off the code. Sharing screen while vitaly looks at logs and diffs. Cover pull requests (or just link the git resources again)

1. After you have checked of all boxes created in [[#Planning the new analyses]], open a [Pull Request](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests)
2. Screenshare with Vitaly while Vitaly looks at the [[logr]] logs and diffs
3. Make any changes suggested, repeating step 2 as needed
4. After getting Vitaly's approval, follow [[GitHub and GitLab#Merge Request Workflow]]
5. Start again with [[#Planning the new analyses]]

# Preparing the paper

## LaTeX 
Cover latex options here. Texmaker, overleaf. Overleaf ideal, but can't always be used based on data.  Crucially, cover how we save files and load them in latex. Let's add our templates

- tables and figures should be created programatically in code
	- use [[kableExtra]] for generating `.tex` files
	- use [[ggplot]] for generating the `.png` output

# Editing
Discuss (briefly) how we talk to other economists and iterate on their feedback.  











