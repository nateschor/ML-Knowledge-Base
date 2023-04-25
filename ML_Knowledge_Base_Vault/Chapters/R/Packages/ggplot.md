- book on [ggplot](https://ggplot2-book.org/)

Common tweaks for ggplots below:

```R

ggplot(data = plotting_data, aes(x = x_aesthetic, y = y_aesthetic)) +
ggthemes::scale_color_ptol() + # nice color scheme https://jrnold.github.io/ggthemes/reference/scale_ptol.html
scale_x_continuous(breaks = expand(expansion = 0, 0)) + # remove extra space on ggplot axis
theme_minimal() + 
theme(
	panel.grid = element_blank()
	text = element_text(family = "AvenirNextforSAS", size = 20)
)


```

Can wrap all of your common ggplot elements using [theme_set](https://ggplot2.tidyverse.org/reference/theme_get.html)

If you're getting the warning `font family not found in Windows font database` you can use the following script as an example for how to install more fonts:

```R
pacman::p_load(
  tidyverse,
  extrafont
)

font_import() # only need to run the first time, takes about 5 minutes

loadfonts(device = "win")
windowsFonts()

ggplot(mtcars, aes(x = wt, y = mpg)) +
  geom_point() +
  labs(
    title = "Here is a title"
  ) +
  theme(
    text = element_text(family="AvenirNextforSAS")
  )

```

Note that the font you include for `family` needs to be one of the (many) fonts listed when running `windowsFonts()`

See this [post](https://stackoverflow.com/questions/34522732/changing-fonts-in-ggplot2) for more information
More information on color schemes in the `khroma` package described [here](https://cran.r-project.org/web/packages/khroma/vignettes/tol.html)

