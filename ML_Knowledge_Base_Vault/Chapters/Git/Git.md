### Resources
- Recommended starting point is this tutorial from [software carpentry](https://swcarpentry.github.io/git-novice/)
-   a more comprehensive resource is the [git book](https://git-scm.com/book/en/v2)
-   for when you inevitably make mistakes, [dangitgit](https://dangitgit.com/en) has solutions for helping with common errors
- [Tips and tricks](https://github.com/git-tips/tips#show-a-git-logical-variable)


#### Git's Relationship to your Working Directory
 ![[three_trees.png]]
 ![[three_trees_arrows.png]]

#### Git Terminology with Diagrams

- [git for computer scientists](https://eagain.net/articles/git-for-computer-scientists/)
![[git_terminology.png]]

### Debugging
-   Use `git blame filename` to look at who modified each [individual line](https://git-scm.com/book/en/v2/Git-Tools-Debugging-with-Git) within a file
	- Helpful when used in conjunction with [[#Show changes over time for specific file]]
-   When you introduced a bug but don't know where, use `git bisect` to [search]([https://git-scm.com/book/en/v2/Git-Tools-Debugging-with-Git](https://git-scm.com/book/en/v2/Git-Tools-Debugging-with-Git)) between commits A and Z to try to figure out where it might be 

### Going Back to Previous Code State
-  use `git checkout commit_hash file_name` to get an older version of `file_name`
	-  Even works if you modified multiple files within the same commit!
	-   Example in [dangit, git](https://dangitgit.com/en)
-   Use `git reflog` to figure out the HEAD name shortcuts

### "Saving" working without commiting it
-  use [git stash](https://bluecast.tech/blog/git-stash/) to keep a copy of your current state without commiting it
- helpful for switching to another branch when you still have uncommitted changes


### Breaking up a larger commit into smaller commits
- helpful if you have a number of edits on the same file, but they don't go together logically
	- example: you experiment with [[Parallel Processing]] and [[data.table]] in different parts of the same script, so you may want to commit those parts of the script separately

![[chunk_file_commits.png]]
- Manual editing if git doesn't get the chunking right for you 
![[manually_chunk_file_commits.png]]

### Searching all files in repo for a particular string
- `git grep -n --heading --break string` for nicely printed console output for each script where `string` occurs, plus the line number
- `git grep -C 5 string` for 5 lines of **C**ontext around `string` (can change the value of 5)


### See what has changed within a given time period
- helpful if you've been away from a project and want to see what has changed recently
 ![[log_in_time_range.png]]
![[logs_between_date_range.png]]

### Show changes over time for specific file
- `git log -p file_name`
- Works well with `git blame` from [[#Debugging]]

#### Helpful for Taking Stock of your Repo's State
![[view_file_on_another_branch.png]]

![[branches_upsteams_last_commits.png]]


