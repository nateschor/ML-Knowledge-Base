- [datapasta](https://github.com/MilesMcBain/datapasta) function for copy-pasting tables (Excel, html, LaTeX) and lists as data frames and vectors into R

Example: New York Yankees World Series table from [wikipedia](https://en.wikipedia.org/wiki/New_York_Yankees)

![[nyy_world_series_table.png]]

![[nyy_world_series_table_highlighted.png]]
1. Highlight the text you want to copy-paste
2. Copy the text
3. In RStudio, write `datapasta::df_paste()` and run the line of code

The R script will populate with the table's contents

![[datapasta_code.png]]
![[datapasta_dataframe.png]]


- After you've installed `datapasta`, a shorcut is also available via "Addins" that replaces the step of writing `datapasta::df_paste()` and running the code
	- you can copy-paste vectors, as well as other data types (see the list in "Addins")

![[datapasta_shortcut.png]]

