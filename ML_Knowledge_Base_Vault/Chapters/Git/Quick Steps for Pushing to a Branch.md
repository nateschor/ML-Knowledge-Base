1. `git status` so that you know what files you changed
2. `git diff HEAD` to see the line-by-line changes you made in all files
	- `git diff file1` to see the line-by-line changes you made in a particular file
	- press `q` to exit out of the commit viewer
	- see [[Shell#Adding Aliases]] for creating shortcuts for your commonly used git commands
3. `git add file1 file2 file3` 
	- `git add .` to add all files
	- `git add -i` to open up interacting mode. Type 2 to update, then `1,2,5` to update the files that are listed as 1,2,5
		- press enter to exit out of interacted mode, and then 7 to quit
4. `git commit -m "Informative commit message here #branch_number"`
	- see [How to Write a Git Commit Message](https://cbea.ms/git-commit/)
	- if you are in the middle of a [pull request](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests), also include `#pull_request_number` in addition to `#branch_number` in your commit message
	- use the `#branch_number` so that when you push, the commit shows up in the appropriate issue
5. `git push`