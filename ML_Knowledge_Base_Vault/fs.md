- create and delete folders and list files using [fs](https://www.tidyverse.org/blog/2018/01/fs-1.0.0/)
- Works well with with `map_dfr` from [purrr](https://purrr.tidyverse.org/),  [[here]], and [[fst]] (works with other file extensions besides `.fst` for reading in all files from a given folder and combining

```R

path_raw_data <- here("path_to_raw_data_folder")

v_files <- dir_ls(path_raw_data)

df_raw <- map_dfr(v_files, function (x) {
	print(x) 
	read_fst(x)
}


```