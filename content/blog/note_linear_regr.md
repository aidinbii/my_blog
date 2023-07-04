+++
title = "Note on linear regression"
author = ["Aidin Biibosunov"]
date = 2023-07-04T18:17:00+02:00
lastmod = 2023-07-04T19:00:58+02:00
tags = ["python", "ML"]
categories = ["blog"]
draft = false
type = "posts"
mathjax = true
+++

**Question**: We train a linear regression model on a data set where all the labels are _positive_. Can this trained model predict a _negative_ value (at least one) on some other data set?

**Answer**: Yes, it can. Since the model is a linear function \\[y=a+bx\\] it will predict negative \\(y\\) values for some \\(x\\) unless \\(a>0\\) and \\(b=0\\).

**Notebook**: And here is a simple demonstration:

{{< notebook "noteLinearRegr" 1120 >}}