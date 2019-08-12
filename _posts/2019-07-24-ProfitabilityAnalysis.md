---
title: "Analysis of Pilgrim Bank Case Study"
date: 2019-07-24
tags: [machine learning, data science]
header:
  image:
excerpt: "Data Mining for Business Analytics"
---
# H1 Heading
Analysis of Pilgrim Bank Case Study

## H2 Heading

### H3 Heading

Here is some basic body text.

*italics*
**bold**

A [hyperlink](hyperlink)

Big Questions
1. Are online customers more profitable?
2. Does going online lead to higher profits?
3. What does our profitability look like across the customer base?


R code block:
''' r
library(tidyverse)
df <- read_csv('data_2009.csv')

sum_profit9 <- sum(select(DATA9, profit9))
count_customer <- nrow(DATA9)
DATA9 <- arrange(DATA9, desc(profit9))
DATA9 <- mutate(DATA9, cum_profit9 = cumsum(profit9))
DATA9 <- mutate(DATA9, per_profit9 = cum_profit9 / sum_profit9 * 100)
DATA9 <- mutate(DATA9, rnk_customer = row_number())
DATA9 <- mutate(DATA9, per_customer = rnk_customer / count_customer * 100)
'''

R code block:
'''
head(filter(DATA9, per_customer > 20), n = 1)

ggplot(DATA9) +
geom_line(aes(x=per_customer, y=per_profit9)) +
labs(x = "Customer Percentile", y = "Cumulative\nProfit\nPercentile")

'''
