
- prefix tibbles, vectors, plots, and matrices as below:

```r
df_descriptive_name
v_descriptive_name
p_descriptive_name
mat_descriptive_name

```

- Use `_` as a suffix for the variable you are using for iteration, as in `state_` in the example below:
- For debugging, choose a value from the object you are iterating through and assign it above the for loop. You can then run the rest of the loop for a specific value without having to change the loop
- use [tictoc](https://cran.r-project.org/web/packages/tictoc/tictoc.pdf) for timing your code, and include comments that specify how long the code will take to run
	- **REMEMBER TO `rm(state_)` and either remove the debugging line or comment it out**

```R
# state_ <- "Pennsylvania"
tic(msg = "starting loop") # Takes 15 seconds to run for each state
for (state_ in v_states) {
	print(state_)
	tic()


	toc()

}
toc()
```