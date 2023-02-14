- book on [ggplot](https://ggplot2-book.org/)

Common tweaks for ggplots below:

```R

ggplot(data = plotting_data, aes(x = x_aesthetic, y = y_aesthetic)) +
ggthemes::scale_color_ptol() + # nice color scheme https://jrnold.github.io/ggthemes/reference/scale_ptol.html
scale_x_continuous(breaks = expand(expansion = 0, 0)) + # remove extra space on ggplot axis
theme_minimal() + 
theme(
	panel.grid = element_blank()
	text = element_text(family = "Avenir", size = 20)
)


```

Can wrap all of your common ggplot elements using [theme_set](https://ggplot2.tidyverse.org/reference/theme_get.html)