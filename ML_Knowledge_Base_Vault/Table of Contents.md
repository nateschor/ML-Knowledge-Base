# Project Stages
1. [[Planning a Project]] **(Nathan TODO: Do a brain dump about how we planned CRISM project. With CS we didn't do it, so we made a great progress on this in a year.**
	- [[Creating a Coding Pipeline]]
2. Creating a GitHub/GitLab repository
	- new project in [GitLab](https://docs.gitlab.com/ee/user/project/)
	- new project in [GitHub](https://docs.github.com/en/issues/organizing-your-work-with-project-boards/managing-project-boards/creating-a-project-board)
3. Setting up [[renv]] with [[Setting up a Project with Renv]]
4. Creating an issue and its accompanying branch for analysis **(Nathan TODO: Make the below more descriptive by adding examples at every step. Example of notes of what V says during meeting, example of a todo N makes based on the notes, example of issue. Describe the process of preparing an issue. Chat with Vitaly, take notes about what we want to do. Then create an issue based on the notes. Vitaly looks at the issue and edits/comments if needed. You plan the scripts (how do you do that, btw, Nathan, I have no idea). T)**
	- [[Planning New Analyses]]
	- [[Branch and Issue Workflow]]
5. Coding
	- what level to save data at in [[Data File Separation]] (**Nathan TODO: Add discussion of keeping data files separate by time and/or some unit identifiers when the dataset is large)**
	- coding checklist in [[Data Reasoning Checklist]] and things to think about in [[Reasoning About your Data]] **(Nathan TODO: Can you add an actionable checklist?)**
	- [[Quick Steps for Pulling a Branch]] **(Nathan TODO: Make the same thing as "Starting a new project" just for quick steps to pull the branch of interest)**
	- [[Quick Steps for Pushing to a Branch]] (**Nathan TODO: Discuss git add and git push, put this in a separate note)**
6. Vitaly signing off on the analysis in [[Having Vitaly Sign Off on the Analyses]] **(Nathan TODO: How does Vitaly sign off the code. Sharing screen while vitaly looks at logs and diffs. Cover pull requests (or just link the git resources again))**
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
- [[Branch and Issue Workflow]]
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



























