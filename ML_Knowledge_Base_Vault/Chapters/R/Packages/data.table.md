- vignette [here](https://cran.r-project.org/web/packages/data.table/vignettes/datatable-intro.html)
- Create rolling sums like below

```R
 DT_keys_no_missing_qtr <- DT[,.(qtr=seq(min(qtr),max(qtr),"3 months")),id]
  
  setkey(DT, id, qtr)
  setkey(DT_keys_no_missing_qtr, id, qtr)
  
  
  
  DT <- DT[DT_keys_no_missing_qtr, roll=0]
  DT <- DT[order(id, qtr)]
  
  DT[, ("p_total") := frollsum(.SD, n = 8, na.rm = FALSE, align = "left"), .SDcols="p_total", by = id]
  DT[, ("p_total") := shift(.SD, 1, type = "lead"), .SDcols="p_total", by = id]
  
```