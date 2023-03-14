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

When giving feedback, rather than talk about what you would like changed, explain the reasoning behind the change and then *make* the change. For example, if a sentence is "models have lower predictive power in the minority group", example of an edit would be:

We should specify which models we are referring to (do all models have less predictive power? Just some of them?), what we mean by predictive power, and what we mean by minority group. Suggested change:

"both XGBoost and Logistic regression had lower ROC AUC for all years in the low-income group compared to the high-income group"

## Presenting
- if a slide contains a link, have a backup slide that with a screenshot that shows the content you wanted to display from the link
- for sections with a lot of information, include an overview slide that helps orient the audience to what they'll be seeing
- ensure the font is legible
	- the font may be large enough when everyone is sitting in front of their own computer screen, but will it be large enough for people who decide to project your talk in a conference room?

# Resources

## Git
- [[Git]]
	- [[Git#Resources]]
	- [[Git#Git's Relationship to your Working Directory]]
	- [[Git#Git Terminology with Diagrams]]
	- [[Git#Using Git to Debug Code]]
	- [[Git#Going Back to Previous Code State]]
	- [[Git#"Saving" work without commiting it]]
	- [[Git#Breaking up a larger commit into smaller commits]]
	- [[Git#Searching all files in repo for a particular string]]
	- [[Git#See what has changed within a given time period]]
	- [[Git#Show changes over time for specific file]]
	- [[Git#Take Stock of your Repo's State]]
	- [[Git#Push Empty Folders to Repo Using .gitkeep Placeholder]]
- [[GitHub and GitLab]]
	- [[GitHub and GitLab#Project Workflow]]
	- [[GitHub and GitLab#Creating an issue and its associated branch in the repo]]
	- [[GitHub and GitLab#Working locally]]
	- [[GitHub and GitLab#Merge Request Workflow]]
	- [[GitHub and GitLab#GitHub shortcuts]]
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
	- [[Shell#Resources]]
	- [[Shell#Common Functions]]
	- [[Shell#Opening files]]
	- [[Shell#Adding Aliases]]
	- [[Shell#Creating Files from a `.csv` Column]]
	- [[Shell#Syntax for Nested Loop]]

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
- [[lobstr]]
- [[butcher]]

### Concepts
- [[EDA]]
- [[Parallel Processing]]

## RStudio
[[Shortcuts]]

## Regex
[[RegEx]]



























