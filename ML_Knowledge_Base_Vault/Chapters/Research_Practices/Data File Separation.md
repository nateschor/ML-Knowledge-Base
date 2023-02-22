When the data is large it is important to think about how the data should be partitioned before saved. Thinking about identifieers in time, space, or a combination of the two is a good starting point. For example, if you are working with a panel dataset that is unique at the consumer + quarter level (see [[Reasoning About your Data#Knowing the level of your data]] to see what level it is unique at), then you might want to save file at the quarter level with all consumers present in that quarter. An example is below:

```R
v_qtrs <- c("2000Q1, 2000Q2, 2000Q3, 2000Q4, 20001Q1") # and so on

for (qtr_ in v_qtrs) {

	print(qtr_)
	df_filtered <- df %>% # df contains the info you want to save, but for all quarters
		filter(qtr %in% qtr_)

	path_out <- here(paste0("data/outcome/default_calculated_", qtr_, ".fst"))
	write_fst(df_filtered, path_out)

}


```

You can then load the data one qtr at a time and process it at a later stage in the pipeline, or load it all into memory if you're using it for modeling

```R

path_data <- here("data/outcome/")
v_data_paths <- dir_ls(path_data)

df <- map_dfr(v_data_paths, function(x) {
	print(x)
	read_fst(x)
})


```
