### Project Workflow

[See Getting Started with Git](https://docs.github.com/en/get-started/getting-started-with-git/setting-your-username-in-git) for more help and information. If GitHub prompts you to authenticate, follow the instructions given. You may need to consult with your organization's IT support

Add instructions on how to set up a git repo

#### Creating an issue and its associated branch in the repo
1. Create an issue
2. In the opening comment to that issue, create tasks to complete using `- [ ]`  
3. Create a branch for that issue directly on GitHub/GitLab
	- if the issue is called "Create Outcome Variable" and it is issue #4, create a branch called issue4_create_outcome_variable

#### Working locally
1.  Get the repositorie's HTTPS  from GitLab under Clone --> Clone with HTTPS (or GitHub CLI on GitHub)
2. In the RStudio terminal, clone repo using `git clone HTTPS`
3.  Run `git pull` and then `git switch issue4_create_outcome_variable`. If continually prompted for your password when using `git pull` or `git push`, reach out to Research IT/Kellen
4.  In the same directory as your local git repo, click on Create Project --> Existing Directory. Browse to the folder that was created in step 1 and click Create Project
5.  
    - if you want to write a longer message, use `git commit`. It will then open up a [[vim]] editor for your commit message
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


### GitHub shortcuts

- press y to grab a [stable link](https://docs.github.com/en/repositories/working-with-files/using-files/getting-permanent-links-to-files)
- hightlight a comment and press r to quote that comment in a new reply
- copy the link to a comment or a commit and it will format it nicely when you paste it in a new comment
- Ctrl + k for hyperlinking
- Ctril + e for adding code 
-  [GitLab markdown](https://docs.gitlab.com/ee/user/markdown.html)
-   [Cool flowcharts](https://about.gitlab.com/handbook/tools-and-tips/mermaid/)
- ![[mermaid_markdown.png]]
- ![[mermaid_rendered.png]]
The screnshots below give examples of how to:
- add a keyboard key in markdown
- showoff the color with a hex code
- make longer comments collapsable to have less clutter (especially usefor for long blocks of code or large figures)
![[markdown_color_samples.png]]
![[rendered_color_samples.png]]
<details>
  <summary>Code</summary>
`print("This is collapsed, and is helpful for not crowding the text with code and figures")``

</details>
- press `/` to easily create a code block, collapsable details, saved replies, or a table









