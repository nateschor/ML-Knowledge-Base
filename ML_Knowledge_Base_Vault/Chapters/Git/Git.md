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

### Using Git to Debug Code
-   Use `git blame filename` to look at who modified each [individual line](https://git-scm.com/book/en/v2/Git-Tools-Debugging-with-Git) within a file
	- Helpful when used in conjunction with [[#Show changes over time for specific file]]
-   When you introduced a bug but don't know where, use `git bisect` to [search]([https://git-scm.com/book/en/v2/Git-Tools-Debugging-with-Git](https://git-scm.com/book/en/v2/Git-Tools-Debugging-with-Git)) between commits A and Z to try to figure out where it might be 

### Going Back to Previous Code State
-  use `git checkout commit_hash file_name` to get an older version of `file_name`
	-  Even works if you modified multiple files within the same commit!
	-   Example in [dangit, git](https://dangitgit.com/en)
-   Use `git reflog` to figure out the HEAD name shortcuts

### "Saving" work without commiting it
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

#### Take Stock of your Repo's State
![[view_file_on_another_branch.png]]

![[branches_upsteams_last_commits.png]]

- `git checkout issue5_create_outcome -- code/pipeline/00_run_pipeline.R` to update the `00_run_pipeline.R` script you have on your current branch with the version that is on branch `issue5_create_outcome`. This is helpful if, for example, you and someone else are both trying to work on the same file in different branches to try two different approaches and then you converge on an approach.

#### Push Empty Folders to Repo Using .gitkeep Placeholder 
Helpful if you create a folder structure but don't yet have any files saved within the folders. Since git doesn't track empty folders, you need to put "something" in the folder for git to be aware of the folder and to be able to push it. The "something" is a placeholder file called [.gitkeep](https://www.theserverside.com/blog/Coffee-Talk-Java-News-Stories-and-Opinions/gitkeep-push-empty-folders-git-commit#:~:text=The%20purpose%20of%20the%20.,gitkeep%20in%20it.)

To put place holder files in all of the empty directories that are children of your current working directory, run the following [[Shell]] code:

`for path in $(find . -type d -empty); do touch $path/.gitkeep; done;`

`find . -type d -empty` searches for empty directories. The `$()` expands the code within side so that the directories can be looped over. `touch $path/.gitkeep` creates a .gitkeep file in each empty directory. 
