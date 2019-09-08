---
title: "Loading Multiple Files into a DataFrame"
author: "Dataasana"
date: 2019-09-05
categories: ["R"]
tags: ["tidbit"]
output:
  html_document:
    code_folding: hide
---




This is a quick tidbit for showing how we can load multiple files with the same structure in a folder into a dataframe.

You can either read all the files separately and bind them together into one single dataframe using bind_rows() or you can do this with one line of code using one of the options below.

<br>

### Option 1

This is one of the slowest option
<br>

> data <- bind_rows(lapply(list.files(pattern = "*.csv"), read.csv))



### Option 2

This is one of the second best option in terms of speed

<br>

> data <- bind_rows(lapply(list.files(pattern = "*.csv"), read_delim, delim = ","))


### Option 3

This is the best option as it takes the least amount of time to read. 4GB of data took less than 30 seconds.

<br>

> data <- bind_rows(lapply(list.files(pattern = "*.csv"), fread))


<br>

Remember the speed of these options mentioned is based on my local system testing.
