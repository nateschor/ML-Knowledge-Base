Every time you create a new dataframe:
- [ ] Check if there are any duplicates at the level of analysis
Every time you do a filter:
- [ ] Look at tidylog output and ask yourself whether you understand why the observations are removed. If you're not 100% sure, look at individual examples that are removed 
Every time you create a new column by doing calculations with `mutate` or `summarize`
- [ ] Sanity check your results. If you're calculating % of people who default or prepay, can you find a paper that uses similar data to get an estimate? If you're creating groups of people, can you see if your % breakdown is similar to what is in the Census?
Every time you `pivot_longer` or `pivot_wider`
 - [ ] did you introduce any missing values? Are any observations now list-columns? If so, address them
Every time you do a complex operation (like ones involving [[data.table]] rolling sums or using [[slider]])
- [ ] pick a couple of individuals and use `View()` to confirm that your operation worked as expected
- [ ] Look at the names of the columns. Are they descriptive enough that you know what they are measuring without having to look at the code that created them? Will they become confusing after you do more, similar operations? Will you know what the columns are measuring when you return to the analysis 6 months from now? If the answer is "no" to any of these questions, think of more descriptive names for the columns
- [ ] check the dimensions of the dataframe. Do they make sense? Have you unexpectedly lost or gained rows?