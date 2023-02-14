### GitHub shortcuts

- press y to grab a [stable link](https://docs.github.com/en/repositories/working-with-files/using-files/getting-permanent-links-to-files)
- hightlight a comment and press r to quote that comment in a new reply
- copy the link to a comment or a commit and it will format it nicely when you paste it in a new comment
- Ctrl + k for hyperlinking
- Ctril + e for adding code 
-  [GitLab markdown](https://docs.gitlab.com/ee/user/markdown.html)
-   [Cool flowcharts](https://about.gitlab.com/handbook/tools-and-tips/mermaid/)
- ![[Pasted image 20230213134908.png]]
- ![[Pasted image 20230213134913.png]]
- Add something that looks like a key, showoff the color with a hex code, and also make longer comments collapsable to have less clutter
- ![[Pasted image 20230213134934.png]]
- ![[Pasted image 20230213134940.png]]
- ![[Pasted image 20230213135000.png]]
- Add collapsible sections like below for displaying long blocks of code or large figures
<details>
  <summary>Code</summary>
`print("This is collapsed, and is helpful for not crowding the text with code and figures")``

</details>


### Project Workflow

#### Creating an issue and its associated branch in the repo
1. Create an issue
2. In the opening comment to that issue, create tasks to complete using `- [ ]`  
3. Create a branch for that issue
	- if the issue is called "Create Outcome Variable" and it is issue #4, create a branch called issue4_create_outcome_variable


#### Working locally
1.  Get the repositorie's HTTPS  from GitLab under Clone --> Clone with HTTPS
2. In the RStudio terminal, clone repo using `git clone HTTPS`
3.  Run `git pull` and then `git switch issue4_create_outcome_variable`. If continually prompted for your password when using `git pull` or `git push`, reach out to Research IT/Kellen
4.  In the same directory as your local git repo, click on Create Project --> Existing Directory. Browse to the folder that was created in step 1 and click Create Project
5.  Run `renv::init()` followed by `renv::snapshot()`
    -   note that in order for `renv::snapshot()` to "see" the package, it must be called using either `library(package_name)` or [[pacman]]`::p_load(package_name)` in a **saved script**. `renv::snapshot()` will not be able to find the package if it only lives in an untitled.R script
6.  `git add .Rprofile renv.lock renv/activate.R`
7.  `git commit -m "Adding initial packages #X"`, where X is replaced with the issue number from (4 in the example)
8.  `git push`
9.  Update packages with `renv::update("package_name_as_string")`
10.  After you update or install new packages, `renv::snapshot()`
11.  `git add renv.lock`
12.  `git commit -m "Update package(s) XYZ #X"`
    -   if you want to revert back to an earlier version of the package, use `renv::revert("commit_hash_for_package_version_I_want")` followed by `renv::restore()`
13.  `git push`
14.  Open a merge request, and after all the changes are agreed upon, close issue X by commenting with a [stable link](https://docs.github.com/en/repositories/working-with-files/using-files/getting-permanent-links-to-files) to the issue branch. See section on [[#Merge Request Workflow]] for more details.
15.  [squash and merge](https://docs.gitlab.com/ee/user/project/merge_requests/squash_and_merge.html) and delete the source branch.
16.  `git switch main` followed by `git branch -D issue4_create_outcome_variable`

**THE ONLY WAY CODE IS ADDED TO MAIN IS VIA PULL REQUEST. DO NOT MODIFY MAIN DIRECTLY**

### Merge Request Workflow

1.  Make comments in review, make changes.
    
2.  Grab a [stable link](https://docs.github.com/en/repositories/working-with-files/using-files/getting-permanent-links-to-files) to the issue branch, which you can use in your summary comment. (In branches where we have issue-specific folders, we grab a stable link to the issue sub as well, and remove the issue sub before the next step.)
    
3.  [Squash and merge](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/incorporating-changes-from-a-pull-request/about-pull-request-merges#squash-and-merge-your-commits).
    
4.  Remove the issue branch.
    
5.  Post a summary comment under the issue thread, include the stable link to the issue branch (also to the issue sub, but this is not always applicable). Include the hash of the commit where the changes were merged into main.
    
6.  Link to that comment under the thread for the pull request.
    

Workflow from Jesse Shapiro and based off of [gslab manual](https://github.com/gslab-econ/lab-manual/wiki/Introduction)







