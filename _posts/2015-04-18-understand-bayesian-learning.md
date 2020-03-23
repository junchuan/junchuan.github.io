---
title: Understand Bayesian Learning
date: 2015-04-18 09:16:00
categories:
- Data Science
- Machine Learning

tags:
- data science
- bayesian

---

## What is Bayesian Learning? 

What is Bayesian Learning? Simply speaking, it is an extension of **point estimation method**. We are no longer satisfied with just getting a **best approximation** for the parameters we are trying to estimate. We want more information. The beautiful thing is all those information are just there. We just need to uncover them instead of ditching them during the computing process.  

Once we know the *posterior distribution* over models, then we can have predictive distribution for unknown input data. The overall predictive distribution is obtained by averaging the predictive distributions of individual models, weighted by the posterior probabilities of those models. If we use the model with the highest probabilities, then it’s called *model selection*.

