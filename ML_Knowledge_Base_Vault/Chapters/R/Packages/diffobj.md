- creates [[Git]] diff style files between 2 R objects to show where they differ
- vignette [here](https://cran.r-project.org/web/packages/diffobj/vignettes/diffobj.html)

### Example

Running the code below:

```R
edited_mtcars <- mtcars
edited_mtcars[2, 3] <- 4

diffPrint(target=mtcars, current=edited_mtcars)
```

produces the following output in the RStudio help/plot pane:

![[diffobj_example.png]]