
- Combines `install.packages` and `library` into a single step and works with [[renv]]
- allows you to separate packages with commas
- automatically installs a package if the user does not already have it installed
- vignette [here](http://trinker.github.io/pacman/vignettes/Introduction_to_pacman.html)

```R
pacman::p_load(
	tidyverse,
	tidylog,
	here
)

```