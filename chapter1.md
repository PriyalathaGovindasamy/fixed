---
title       : Chapter 1
description : This chapter is an introduction to fixed meta-analysis
attachments :
slides_link : https://s3.amazonaws.com/assets.datacamp.com/course/teach/slides_example.pdf

--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:1e5367ace8
## Effect size for correlation coefficient

What information is needed to estimate efects size for correlation?

*** =instructions
- sample size, coefficient
- study id, coefficient
- study year, coefficient

*** =hint
Weighted coefficient

*** =pre_exercise_code
```{r}
# run code for fixed meta analysis
#load the file
data.mta <- read.csv("http://s3.amazonaws.com/assets.datacamp.com/course/introduction_to_r/movies.csv")

library(metafor)
data.mta <- escalc(measure="ZCOR", ni=ni, ri=ri, data=data.mta, append=TRUE)   

fixed.meta <- rma(yi, vi, data=data.mta, method="FE")
summary(fixed.meta)
```
