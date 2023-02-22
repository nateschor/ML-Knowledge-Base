1. Chat with Vitaly, and take notes on what should be accomplished. This might include: 
	- immediate steps (that will be addressed in the upcoming issue) such as "Create the outcome variable for default. We will define someone as being in the state of default if they are 90 or more days past due on any trade line within 8 quarters. Please look at the data dictionary and suggest to me which variables we should use to capture their trade lines and send them to me. For capturing 90+ DPD, look at [[data.table]] for computing a rolling sum. Let me know what % of consumers default"
	- longer term steps (things that are not yet actionable or that we don't want to forget) such as "We want to be able to look at the interpretability of our model. Read this paper about Shapley values, look into some R packages for computing Shapley values, and test them all on 10,000 observations and report back what you find. You're free to create this as a separate issue or part of our current issue"   
	- revisions to make to previous work (that you can either create a new issue for, or reopen the original issue) such as "we need to change the way we compute or thresholds. Please incorporate this code I have written into our coding pipeline"
2. Create an [Issue](https://docs.github.com/en/issues/tracking-your-work-with-issues/about-issues) for addressing the task
	- Give a title for the issue. For example,  "Create outcome variable for defaulting"

Example issue
### Generate Shapley value plots

#### Data Prep
- [ ]   Create a new folder in `code/workflow/pipeline` called `shapley` to hold the scripts
- [ ]   Run Vitaly's code below for 1 qtr to make sure I am following it
- [ ]   Remove calls to `sample_n()` or any other experimental efficiency lines
- [ ]   In the pipeline script, add a `%dopar%` loop to parallelize over models
- [ ]   save the `df_long` data as `shapley_qtr_rand_no_cid` in a new folder in the pipeline. Saving 1 qtr_rand_no_cid takes 4 minutes
- [ ]   Calculate the average of the absolute values of the shapley values
- [ ]   For each model use the top 10 vars with descriptions
3. In the body of the issue, create tasks to complete using `- [ ]` (see above). These are for you to break down the task into actionable chunks, for you to track your progress, and for Vitaly to be able to see your progress if he would like
4. Send a screenshot of the issue to Vitaly, who will give edits/commits if needed. This is important because by putting Vitaly's instructions in your own words, you will hopefully flush out anything that you are not on the same page about. Using the example above, Vitaly might make a comment like "we don't want to use [[Parallel Processing]] in this case because the computation is short enough that the overhead of setting up parallel processing will take too long, please change `%dopar%` to `%do`. Furthermore, please add a task to send me summary statistics for each of the top 10 variables that are chosen