#### Resources

- software carpentry [tutorial](https://swcarpentry.github.io/shell-novice/)
- extra shell [material](https://carpentries-incubator.github.io/shell-extras/)
- Website for understanding the components of a shell command [here](https://explainshell.com/)

#### Common Functions
- `cd` for **c**handing **d**irectory, `cd -` to go back to most recent directory
-  `wc` to get line count, word count, and character count
- `mkdir` for creating folders
	- helpful to use with the `-p` option for creating parents as necessary, for example:
	 `mkdir -p code data/raw data/intermediate paper/figures paper/tables`
- `|` is the shell pipe and is used for chaning commands similar to `%>%` in [[tidyverse]]
-   Using [find and grep](https://swcarpentry.github.io/shell-novice/07-find/index.html)
	- `find` for finding files within your project
	- `grep` for finding lines of text within files. This is a version of `git grep` described in [[Git#Searching all files in repo for a particular string]] that works outside of git repositories 
-   Use `sed "s\current\replace\g"` to do replacement either for file names or for content in files, use -i argument in sed to actually do the replacement (otherwise you just show the change without making the change)
- `seq 10` to print out 1:10
- use `{1..10..3}` or `{a..e}` as shorthand for creating lists, helpful for creating folders or for selecting only certain files to stage when using [[Git]]
- `diff file1 file2` to see what is different between them, similar to a non-[[Git]] version of `git diff HEAD` shown in [[#Adding Aliases]]
-  [paste](https://datascienceatthecommandline.com/2e/list-of-command-line-tools.html#paste) things together like 1+2+3+4+5+6 using `seq 6 | paste -sd+`
-   `echo $?` gives the [exit status](https://www.gnu.org/software/bash/manual/html_node/Exit-Status.html#:~:text=The%20exit%20status%20of%20an,also%20limited%20to%20this%20range.) of the last command you ran, can be helpful for conditional logic if a command/script fails
- Efficiently search your command history with `Ctrl + R`
- Use `time` to get how long it takes commands to execute
- [xargs](https://www.howtoforge.com/tutorial/linux-xargs-command/) to search for multiple file extensions simultaneously (e.g. .txt and .csv and .pdf)
- Rerun a different command with the same arguments as the previous command with `!$` 
![[shell_rerun_command.png]]
- [tr](https://unix.stackexchange.com/questions/427940/main-difference-between-tr-translate-to-sed-and-awk#:~:text=tr%20works%20on%20characters%20(changes,or%20inserts%20or%20deletes%20lines).) command for doing string replacements
Example using `tr` and `sed`
![[shell_tr_and_sed.png]]

### Opening files

```bash
for dict in dict1.pdf dict2.pdf dict3.pdf;
do start $dict;
done
```

Save the script as `your_script_name.sh` and call it from the shell with `bash your_script_name.sh`

#### Adding Aliases

- shortcuts for commonly used commands
- below are some examples for quickly changing directory or shortening your commonly used [[Git]] commands
- to create a new alias, type `alias your_alias_name='shell_command_for_alias'`

![[shell_aliases.png]]

Logical flags

![[shell_logical_flags.png]]

#### Creating Files from a `.csv` Column

- imagine you have the following table `fruit.csv` and want to create a file `fruit.txt` for each of the fruits:

**Fruit**
Apple
Banana
Cherry
Date

You can do this programatically with `for fruit in $(tail -n+2 fruit.csv); do touch ${fruit}.txt; done;`

#### Syntax for Nested Loop

```Shell
for i in 1 2 3
do 
	for j in A B C
	do 
		echo "$i$j"
	done
done
```











 
