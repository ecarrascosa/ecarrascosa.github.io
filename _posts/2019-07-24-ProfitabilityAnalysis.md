---
title: "Analysis of Pilgrim Bank Case Study"
date: 2019-07-24
tags: [Profit Analytics]
header:
  image:
excerpt: "Data Mining for Business Analytics"
---
# Getting insights into profitability

Getting insights into your profitability can help you devise strategies to maximize profits. Let's start by answering some basic questions.

## Insights into variation in profitability across customers

To analyze the variation in profitability across customers we use a sample of 30,000 customers and their profits for last year. After handling the missing data and with the help of R's tidy verse library we can plot the cumulative profit percentile across customers. 

### H3 Heading

Here is some basic body text.

*italics*
**bold**

A [hyperlink](hyperlink)

Big Questions
1. Are online customers more profitable?
2. Does going online lead to higher profits?
3. What does our profitability look like across the customer base?

Python code block:
```python
   import numpy as np

    def test(x,y):
      z = np.sum(x,y)
      return z
```

R code block:

```r
library(tidyverse)
df <- read_csv('data_2009.csv')

sum_profit9 <- sum(select(DATA9, profit9))
count_customer <- nrow(DATA9)
DATA9 <- arrange(DATA9, desc(profit9))
DATA9 <- mutate(DATA9, cum_profit9 = cumsum(profit9))
DATA9 <- mutate(DATA9, per_profit9 = cum_profit9 / sum_profit9 * 100)
DATA9 <- mutate(DATA9, rnk_customer = row_number())
DATA9 <- mutate(DATA9, per_customer = rnk_customer / count_customer * 100)
```

R code block:
```r
head(filter(DATA9, per_customer > 20), n = 1)

ggplot(DATA9) +
geom_line(aes(x=per_customer, y=per_profit9)) +
labs(x = "Customer Percentile", y = "Cumulative\nProfit\nPercentile")
```
