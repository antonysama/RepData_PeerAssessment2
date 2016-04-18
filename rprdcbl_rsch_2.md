# Reproducible Research Assignment 2

##The purpose of the assignment is to learn to write & present reproducible research using US disaster data

##Snopisis:Predownloaded data was absorbed into R, processesed and massaged to get what we need related to the health & economic impacts. In the following steps I show how I prioriised and subset data with the greatest impacts and most significant exponents

##Steps:



#1.Process previously downloaded "StormData.csv.bz2"


#2.Aggregate and PRIORITISED TOP 15 EVENTS leasing to fatalities & injuries


##RESULTS: HEALTH EFFECTS

#3.Plot fatalities

```r
library("ggplot2")
qplot(EVTYPE, INJURIES, data=inj)+ geom_bar(stat="identity")+ ylab("No. of Injuries") + xlab("Enviromental Disaster Type") + ggtitle("Estimates of Injuries") + theme(axis.text.x = element_text(angle=80, hjust=1))
```

![](rprdcbl_rsch_2_files/figure-html/unnamed-chunk-3-1.png)

#4.Plot injuries

```r
qplot(EVTYPE, FATALITIES, data=fat)+ geom_bar(stat="identity")+ ylab("No. of Fatalities") + xlab("Enviromental Disaster Type") + ggtitle("Estimates of Fatalities") + theme(axis.text.x = element_text(angle=80, hjust=1))
```

![](rprdcbl_rsch_2_files/figure-html/unnamed-chunk-4-1.png)

#5(a).Table all the diffeent types of exponents including NAs ("") with some helpful info<<https://rstudio-pubs-static.s3.amazonaws.com/58957_37b6723ee52b455990e149edde45e5b6.html>>

```r
table(df$PROPDMGEXP)
```

```
## 
##             -      ?      +      0      1      2      3      4      5 
## 465934      1      8      5    216     25     13      4      4     28 
##      6      7      8      B      h      H      K      m      M 
##      4      5      1     40      1      6 424665      7  11330
```

```r
table(df$CROPDMGEXP)
```

```
## 
##             ?      0      2      B      k      K      m      M 
## 618413      7     19      1      9     21 281832      1   1994
```

#5(b).Sum up the exponets I prioritised to use

```r
x <- setdiff(df$PROPDMGEXP, c("", "?", "-1", "0"))
sum(df$PROPDMGEXP %in% x)
```

```
## [1] 436139
```

```r
y <- setdiff(df$CROPDMGEXP, c("", "?", "-1", "0"))
sum(df$CROPDMGEXP %in% y)
```

```
## [1] 283858
```

#6.Subset dataframe to have at least one exponent each for property or crop 


#7.Multiply by exponent 


#8 Re-arrange, aggregate & sort


##RESULTS: ECONOMIC EFFECTS

#9 Plot property damage 

```r
library("ggplot2")
qplot(EVTYPE, SUMPROPDMG, data=property)+ geom_bar(stat="identity")+ ylab("Property Damage Amount $") + xlab("Enviromental Disaster Type") + ggtitle("Estimates of Property Damange") + theme(axis.text.x = element_text(angle=80, hjust=1))
```

![](rprdcbl_rsch_2_files/figure-html/unnamed-chunk-10-1.png)

#10. Plot crop damage

```r
qplot(EVTYPE, SUMCROPDMG, data=crop)+ geom_bar(stat="identity")+ ylab("Property Damage Amount $") + xlab("Enviromental Disaster Type") + ggtitle("Estimates of Crop Damange") + theme(axis.text.x = element_text(angle=80, hjust=1))
```

![](rprdcbl_rsch_2_files/figure-html/unnamed-chunk-11-1.png)
