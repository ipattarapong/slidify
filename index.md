---
title       : Varaint Sampling Demonstrate
subtitle    : Presentation
author      : Pattarapong Ingsakulrunraung
job         : Internet
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

## Overview

Nowsaday we processing a huge amount of data to make a quick decision on business.

Sometime sampling needs to be in place to perform quick analysis.

My application demonstarte how the population and sampling size effect the expect outcome.

This application will sample data with 2 variants ('A' and 'B') by number of population then sampling the sample data and show the percentage  of  two variants

Application link : https://ipattarapong.shinyapps.io/assign1

Gist link:  https://gist.github.com/ipattarapong/805081b9e6c57b31d38a

---

## How to use Application

This application is re-active so the result will update if parameter changes which are

1. probability of two variants
2. number of population 
3. percentage of sampling data
4. Refresh sampling data without changing parameters

---

## How it work 

1. Sample number of population base on probability of variants 
2. Sampling data as percentage of total sample
3. Update result interactive 
4. Display number of A and B with percentage

---

## Coding and Techniques
* using reactiveValues() and observe() function to do re-active output

```
values = reactiveValues()
Data <- observe({
      input$refresh
      values$a <- as.numeric(input$probs)
      ...
```  
* Sample data using r sample function


```r
sample(c("a","b"), 10,prob=c(0.7,0.3),replace=TRUE)
```

```
##  [1] "a" "a" "a" "a" "a" "a" "a" "b" "a" "a"
```

* using input$refresh inside reactive to refresh


---

## Summary

If the population size is low and the sampling rate is low the chance to get sampling data not match with raw data  is higher than when you get more population and more sampling rate.

For example, sampling 10 % of 1000 population size may not good enough to decide the out come of 70 % of A and 30% of B.

In some situation processing all of data is consume a lot of resouces, sampling portion of data should be one of solution. Besides, population size and sampling rate need to be reasonable to create confident result.

For instance, sampling 10 % of 10000 data with 50 % change on both variant.

--- .class #id
