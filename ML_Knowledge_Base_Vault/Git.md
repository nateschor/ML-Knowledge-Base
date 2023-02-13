-   Recommended starting point is this tutorial from [software carpentry](https://swcarpentry.github.io/git-novice/)
-   a more comprehensive resource is the [git book](https://git-scm.com/book/en/v2)
-   for when you inevitably make mistakes, [dangitgit](https://dangitgit.com/en) has solutions for helping with common errors
### Merge Request Workflow

1.  Make comments in review, make changes.
    
2.  Grab a stable link to the issue branch, which you can use in your summary comment. (In branches where we have issue-specific folders, we grab a stable link to the issue sub as well, and remove the issue sub before the next step.)
    
3.  Squash and merge.
    
4.  Remove the issue branch.
    
5.  Post a summary comment under the issue thread, include the stable link to the issue branch (also to the issue sub, but this is not always applicable). Include the hash of the commit where the changes were merged into main.
    
6.  Link to that comment under the thread for the pull request.
    

Workflow from Jesse Shapiro and based off of [gslab manual](https://github.com/gslab-econ/lab-manual/wiki/Introduction)

When wrapping up a merge request and closing an issue, go to the last file on the branch that was modified. Press y to get a permanent link