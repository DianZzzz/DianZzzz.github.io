---
layout: blog
topic: Best Practic
title: Data Bias
tags:  datascience daa
comments: true
date: 2022-10-20
---

# Data Bias

## Categorical Variables - Chi-Sqaure

### Hypotheses

H_0: tested variables are independent (No Bias)

H_a Bias: tested variables are not independent (Bias)

```python
# create a crosstab of variables to be tested
crosstab = pd.crosstab(df['sex'], df['class'])

from scipy import stats
from scipy.stats import chi2_contingency
stats.chi2_contingency(crosstab)
```

The first value is the Chi-square value, followed by the p-value, then comes the degrees of freedom, and lastly it outputs the expected frequencies as an array. 

For the Chi-square test assumes that expected frequencies will be greater or equal to 5. If a cell has an expected frequency less that 5, then the Fisher’s Exact test should be use to overcome this problem. 

Reject the null hypothesis if the p-value is less than 0.05 and concludes that the results indicate that there is a relationship between the two variables. 