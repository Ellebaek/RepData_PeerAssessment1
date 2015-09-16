---
title: "Reproducible Research Assignment 1"
author: "Thomas Ellebæk"
date: "Wednesday, September 16, 2015"
output: html_document
---

This is the first (of two) assignment for the Coursera course Reproducible Research by Roger D. Peng, PhD, Jeff Leek, PhD, Brian Caffo, PhD, from the Johns Hopkins Bloomberg School of Public Health.

## Loading and preprocessing the data
Reading data into data table.


```r
library(data.table)
```

```
## Warning: package 'data.table' was built under R version 3.1.3
```

```
## data.table 1.9.4  For help type: ?data.table
## *** NB: by=.EACHI is now explicit. See README to restore previous behaviour.
```

```r
data <- fread("C:/Users/THEL/Desktop/Privat/RR/repdata_data_activity/activity.csv", na.strings="NA")
```

```
## Warning: running command 'C:\WINDOWS\system32\cmd.exe /c
## (C:/Users/THEL/Desktop/Privat/RR/repdata_data_activity/activity.csv) >
## C:\Users\Thomas\AppData\Local\Temp\Rtmp82mnhs\file1708219f3' had status 1
```

```
## Warning in shell(paste("(", input, ") > ", tt, sep = "")):
## '(C:/Users/THEL/Desktop/Privat/RR/repdata_data_activity/activity.csv) >
## C:\Users\Thomas\AppData\Local\Temp\Rtmp82mnhs\file1708219f3' execution
## failed with error code 1
```

```
## Error in fread("C:/Users/THEL/Desktop/Privat/RR/repdata_data_activity/activity.csv", : File is empty: C:\Users\Thomas\AppData\Local\Temp\Rtmp82mnhs\file1708219f3
```

## What is mean total number of steps taken per day?
Calculating the total number of steps taken per day.


```r
nonNA <- subset(data, !is.na(steps))
```

```
## Error in subset.default(data, !is.na(steps)): object 'steps' not found
```

```r
stepsPerDay <- nonNA[,.(count = sum(steps)),by=list(date)]
```

```
## Error in eval(expr, envir, enclos): object 'nonNA' not found
```

Creating histogram of the total number of steps taken each day.


```r
ave <- round(mean(stepsPerDay$count),2)
```

```
## Error in mean(stepsPerDay$count): object 'stepsPerDay' not found
```

```r
med <- median(stepsPerDay$count)
```

```
## Error in median(stepsPerDay$count): object 'stepsPerDay' not found
```

```r
hist(stepsPerDay$count, xlab="Steps per day", main="Histogram witout NA's")
```

```
## Error in hist(stepsPerDay$count, xlab = "Steps per day", main = "Histogram witout NA's"): object 'stepsPerDay' not found
```

```r
legend("topright", c(paste("Mean =", ave),paste("Median =", med)))
```

```
## Error in paste("Mean =", ave): cannot coerce type 'closure' to vector of type 'character'
```













