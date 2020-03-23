---
title: Naive Bayes, Hidden Markov Model, Structured Prediction
date: 2018-10-19 11:29:00
categories:
- Data Science
- Machine Learning

tags:
- data science
- hidden markov model
- naive bayes
- structured prediction



---

## Naive Bayes Model
An approach to classify a single class variable that depends on several feature values. In this model the input feature values are assumed to be *independent* with each other. It is a *generative* approach, modeling the joint probability `p(y,x)` of the input values `x` and the class variable `y`.   


## Hidden Markov Model
In Naive Bayes model, only a single class variable is considered. If we want to predict a a sequence of class variables 
$(y_1,y_2...y_n)$ for an observation sequence $x=(x_1,x_2...x_n)$, naively, a simple sequence model can be formulated as a product over single Naive Bayes Models.  
$$ p(y,x)=\prod_i^m p(y_i)p(x_i|y_i) $$  
We can immediately notice that the dependencies between single sequence positions are not taken into account. Each observation $x_i$ depends only on the class variable $y_i$ at the respective sequence position. If we want to incorporate the dependencies between observations at consecutive sequence positions, then we have to adapt our model to:  
$$p(y,x)=\prod_i^m p(y_i|y_{i-1})p(x_i|y_i)$$

## Maximum Entropy Model
Principle of Maximum Entropy: if incomplete information about a probability distribution is available, the only unbiased assumption that can be made is a distribution which is as uniform as possible given the available information.  
## Structured Prediction 
Essentially, structured prediction is the combination of graphical modeling with classification. Graphical modeling is good at modeling multivariate data, and classification methods are good at performing prediction using large sets of input features. 
Conditional random field is a popular probabilistic method for structured prediction. 


HMM is an extension to Naive Bayes model for sequentially structured data, also representing the dependencies between `x` and `y` as a joint probability distribution. Modeling joint probability distribution has its disadvantages due to the computation complexity.  The maximum entropy model directly model  `p(y|x)`. While HMM can be understood as an extension to Naive Bayes model, CRF can be considered as an extension of maximum entropy model onto sequential structured data. Both maximum entropy and CRF are discriminative approach. 


