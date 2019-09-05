---
title: "Analyzing Customer Profitability"
date: 2019-07-24
tags: [Business Analytics]
header:
  image:
excerpt: "Data Mining for Business Analytics"
---
"Understanding profitability at the customer level is particularly important in retail banking because customer transactions generate incremental costs but typically don't generate incremental revenue"

In this post I share a data analytics project that I worked on in my Master's program for a small regional retail bank. In 2012 the bank launched an online banking platform and was debating whether to charge for the service or provide it for free or even whether to provide rebates and incentives to encourage the use of the online platform. We found answers to these questions in the customer data.

Question 1: Are online customers more profitable?

Question 2: Are online customers more profitable?

Question 3: How much variation in profitability is observed across customers and how could we best deal with this variability?

Question 4: Is the difference in average profitability between online and offline customers in the sample indicative of a meaningful difference in profitability across these groups in the entire population of Pilgrim Bank’s customers?

Question 5: What is the role of customer demographics in comparing online and offline profitability?

Question 6: To what extent the profit in 1999 can help us predict profit in 2000?

# Insights into customer profitability

We collected a sample of 30,000 customers, their profits, and whether or not they used online banking.

To look at variation in profits I sorted the customers from most to least profitable and charted percent cumulative profitability versus percent cumulative customers.

-- Insert visual and analysis of cumm graph

10% of the customer generated 70% of the profits.


10% of the customers

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
