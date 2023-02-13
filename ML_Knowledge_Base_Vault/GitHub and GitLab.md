[Tips and tricks](https://github.com/git-tips/tips#show-a-git-logical-variable)

Debugging

-   Using git to look at who modified each individual line within a file and when with <git blame filename> [https://git-scm.com/book/en/v2/Git-Tools-Debugging-with-Git](https://git-scm.com/book/en/v2/Git-Tools-Debugging-with-Git)
-   When you introduced a bug but don't know where, use git bisect to search between commits A and Z to try to figure out where it might be [https://git-scm.com/book/en/v2/Git-Tools-Debugging-with-Git](https://git-scm.com/book/en/v2/Git-Tools-Debugging-with-Git)
- Going back to previous state

-   git reset --hard <commit_hash> [https://git-scm.com/book/en/v2/Git-Tools-Reset-Demystified](https://git-scm.com/book/en/v2/Git-Tools-Reset-Demystified)

-   Example in [git practice](file:///C:/Users/c1nhs01/Documents/Git%20Practice/git_reset_soft)

-   git checkout <hash/HEAD@{index}> <file.txt>

-   Example in [dangit, git](https://dangitgit.com/en)
-   Even works if you modified multiple files within the same commit!

-   Use git reflog to figure out the HEAD name shortcuts
-   [git stash](https://bluecast.tech/blog/git-stash/)
- ![[Pasted image 20230213134711.png]]
- ![[Pasted image 20230213134723.png]]
- [https://eagain.net/articles/git-for-computer-scientists/](https://eagain.net/articles/git-for-computer-scientists/)
- ![[Pasted image 20230213134759.png]]
- Breaking up a larger commit into smaller commits
- ![[Pasted image 20230213134816.png]]
- ![[Pasted image 20230213134825.png]]
- git grep -n --heading --break for nicely printed console output
- [GitLab markdown](https://docs.gitlab.com/ee/user/markdown.html)
-   [Cool flowcharts](https://about.gitlab.com/handbook/tools-and-tips/mermaid/)
- ![[Pasted image 20230213134908.png]]
- ![[Pasted image 20230213134913.png]]
- Add something that looks like a key, showoff the color with a hex code, and also make longer comments collapsable to have less clutter
- ![[Pasted image 20230213134934.png]]
- ![[Pasted image 20230213134940.png]]
- ![[Pasted image 20230213135000.png]]
- ![[Pasted image 20230213135008.png]]
- Show changes over time for specific file

git log -p <file_name>
![[Pasted image 20230213135035.png]]
![[Pasted image 20230213135043.png]]
![[Pasted image 20230213135055.png]]
![[Pasted image 20230213135104.png]]
![[Pasted image 20230213135110.png]]