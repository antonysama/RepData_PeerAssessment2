# rprdcbl_rsch_2



## R Markdown
*getting data and processing the damage*


```r
df<-read.csv("repdata_data_StormData.csv")
lazydf<-df[!df$PROPDMGEXP==""|!df$CROPDMGEXP=="",]
hundred<-c("H","h")
df$dmg<- ifelse(grepl(paste(hundred, collapse = "|"),df$PROPDMGEXP, ignore.case = T), df$pROPDMG*100, 0)
```

*how many damages (PROPDMGEXP) are not in letters

```r
x <- setdiff(df$PROPDMGEXP, c("K", "M", "B", NA))
sum(df$PROPDMGEXP %in% x)
```

```
## [1] 466262
```

```r
table(lazydf$PROPDMGEXP)
```

```
## 
##             -      ?      +      0      1      2      3      4      5 
##   4318      1      8      5    216     25     13      4      4     28 
##      6      7      8      B      h      H      K      m      M 
##      4      5      1     40      1      6 424665      7  11330
```
*how many lazydf$PROPDMGEXP==" " are in lazydf$CROPDMGEXP==" "

```r
x <- setdiff(c(lazydf$PROPDMGEXP==""), !c(lazydf$CROPDMGEXP==""))
sum(lazydf$PROPDMGEXP=="" %in% x)
```

```
## [1] 0
```
