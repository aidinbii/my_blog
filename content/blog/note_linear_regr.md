+++
title = "Note on linear regression"
author = ["Aidin Biibosunov"]
lastmod = 2026-04-05T11:06:12+02:00
tags = ["python", "ML"]
categories = ["blog"]
draft = true
type = "posts"
mathjax = true
+++

**Question**: We train a linear regression model on a data set where all the labels are _positive_. Can this trained model predict a _negative_ value (at least one) on some other data set?

**Answer**: Yes, it can. Since the model is a linear function \\[y=a+bx\\] it will predict negative \\(y\\) values for some \\(x\\) unless \\(a>0\\) and \\(b=0\\).

**Notebook**: And here is a simple demonstration:

{{&lt; notebook "noteLinearRegr" 1300 &gt;}}
