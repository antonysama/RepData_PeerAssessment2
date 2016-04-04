# rprdcbl_rsch_2



## R Markdown
*getting data and procession damage*


```r
df<-read.csv("repdata_data_StormData.csv")
hundred<-c("H","h")
df$dmg<- ifelse(grepl(paste(hundred, collapse = "|"),df$PROPDMGEXP, ignore.case = T), df$PROPDMG*100, 0)
```

## Including Plots

You can also embed plots, for example:

![](rprdcbl_rsch_2_files/figure-html/pressure-1.png)

Note that the `echo = FALSE` parameter was added to the code chunk to prevent printing of the R code that generated the plot.
