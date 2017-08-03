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
*** =sct
```{r}
# SCT written with testwhat: https://github.com/datacamp/testwhat/wiki

msg_bad <- "That is not correct!"
msg_success <- "Exactly! There seems to be a very bad action movie in the dataset."
test_mc(correct = 2, feedback_msgs = c(msg_bad, msg_success, msg_bad, msg_bad))

test_function("str", args = "object",
              not_called_msg = "You didn't call `str()`!",
              incorrect_msg = "You didn't call `str(object = ...)` with the correct argument, `object`.")

test_object("good_movies")

test_function("plot", args = "x")
test_function("plot", args = "y")
test_function("plot", args = "col")

test_error()
success_msg("Good work!")
```
