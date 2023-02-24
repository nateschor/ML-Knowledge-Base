
### Nathan TODO:
Put references git steps under one header with links (in the end is good) like below
- add a section in coding practices about saving intermediate data, models et (the more the better, though space is somewhat a concern too). Discuss underlying plot data. If making plots involves a lot of computations, we don't want to be redoing the computations just to change plot labels. So saving the smallest dataset preceding a plot and then doing plot itself in a separate script is a good practive.

# Git steps reference
[[Quick Steps for Pulling a Branch]]
[[Quick Steps for Pushing to a Branch]]

# Project Steps
1. [[Planning a Project]] 
	- [[Creating a Coding Pipeline]]
2. Creating a GitHub/GitLab repository
	- new project in [GitLab](https://docs.gitlab.com/ee/user/project/)
	- new project in [GitHub](https://docs.github.com/en/issues/organizing-your-work-with-project-boards/managing-project-boards/creating-a-project-board)
3. Setting up [[renv]] with [[Setting up a Project with Renv]]
4. Creating an issue and its accompanying branch for analysis
	- [[Planning New Analyses]]
	- [[One Branch for One Issue Workflow]]
5. Coding
	- what level to save data at in [[Many small data files is better than one huge one]]
	- coding checklist in [[Data Reasoning Checklist]] and things to think about with some examples in [[Reasoning About your Data]] 
	- [[Quick Steps for Pulling a Branch]] 
	- [[Quick Steps for Pushing to a Branch]] 
6. Vitaly signing off on the analysis in [[Having Vitaly Sign Off on the Analyses]]
7. Merging your branch into main in [[GitHub and GitLab#Merge Request Workflow]]

# Preparing the Paper

## LaTeX 
Cover latex options here. Texmaker, overleaf. Overleaf ideal, but can't always be used based on data.  Crucially, cover how we save files and load them in latex. Let's add our templates

- tables and figures should be created programatically in code
	- use [[kableExtra]] for generating `.tex` files
	- use [[ggplot]] for generating the `.png` output

## Editing
Discuss (briefly) how we talk to other economists and iterate on their feedback.  

# Resources

## Git
- [[Git]]
- [[GitHub and GitLab]]
-  [[GitHub and GitLab#Merge Request Workflow]] (Nathan TODO: make all headers explicit so it's very easy to see what things are covered, this section is intended for rapid lookup not in depth reading)

- [[One Branch for One Issue Workflow]]
- [[Quick Steps for Pulling a Branch]]
- [[Quick Steps for Pushing to a Branch]]

## Coding Style
- [[naming conventions]]
- [[vim]]
- [[formatting]]

## Tools 

## Shell 
- [[Shell]]

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



























