---
title: Summary of probability distributions
date: 2013-10-01 09:16:00
categories:
- Notes

tags:
- data science
---

### Bernoulli process
An experiment whose dichotomous outcomes are random (coin toss, rolling a die, polls).
### Beta Distribution
models events that are constrained to take place within an interval defined by a minimum and maximum value.The Beta probability density function is given by  
$$ \frac {x^{\alpha-1}(1-x)^{\beta-1}} {B(\alpha,\beta)} $$  
where
- α is a positive shape parameter
- β is a positive shape parameter  

The Beta distribution is used in a range of disciplines including rule of succession, Bayesian statistics, and task duration modeling. Examples of events that may be modeled by Beta distribution include:
- The time it takes to complete a task
- The proportion of defective items in a shipment 

### Geometric distribution
The probability distribution of the number of Bernoulli trials needed to get one success. 
### Hyper Geometric
Discrete probability distribution that describes the number of successes in a sequence of n draws from a finite population without replacement. 

### Poisson distribution
A discrete probability distribution that expresses the probability of a given number of events occurring in a fixed interval of time and/or space if these events occur with a known average rate and independently of the time since the last event, that is, it predicts the degree of spread around a known average rate of occurrence.  
$$\frac {\lambda^k e^{-\lambda}} {k!}$$  
where
- e is the base of the natural logarithm (e = 2.71828...)
- k! is the factorial of k
- λ is a positive real number, equal to the expected number of occurrences during the given interval.
As a function of k, this is the probability mass function. The parameter λ is not only the mean number of occurrences , but also its variance.

### Gamma distribution
Gamma distribution is a distribution that arises naturally in processes for which the waiting times between events are relevant. It can be thought of as a waiting time between Poisson distributed events.  
The waiting time until the `hth` Poisson event with a rate of change `λ` is
$$P(x)=\lambda(\lambda x)^{h-1}$$  
The gamma distribution can be used a range of disciplines including queuing models, climatology, and financial services. Examples of events that may be modeled by gamma distribution include:
- The amount of rainfall accumulated in a reservoir
- The size of loan defaults or aggregate insurance claims
- The flow of items through manufacturing and distribution processes
- The load on web servers
- The many and varied forms of telecom exchange  

The gamma distribution is also used to model errors in a multi-level Poisson regression model because the combination of a Poisson distribution and a gamma distribution is a negative binomial distribution.  

### Exponential Distribution
A special case of the gamma distribution. The gamma distribution is the waiting time for more than one event, the exponential distribution describes the time between a single Poisson event. The exponential probability density function is given by  
$$e^{-\lambda x}$$  
where:
- e is the natural number (e = 2.71828…)
- λ is the mean time between events
- x is a random variable   

The exponential distribution occurs naturally when describing the waiting time in a homogeneous Poisson process. It can be used in a range of disciplines including queuing theory, physics, reliability theory, and hydrology. Examples of events that may be modeled by exponential distribution include:
- The time until a radioactive particle decays
- The time between clicks of a Geiger counter
- The time until default on payment to company debt holders
- The distance between roadkills on a given road
- The distance between mutations on a DNA strand
- The time it takes for a bank teller to serve a customer
- The height of various molecules in a gas at a fixed temperature and pressure in a uniform gravitational field
- The monthly and annual maximum values of daily rainfall and river discharge volumes

### Pareto Distribution
A skewed, heavy-tailed distribution that is sometimes used to model that distribution of incomes. The basis of the distribution is that a high proportion of a population has low income while only a few people have very high incomes.
The Pareto probability density function is given by  
$$\frac {ax^a_m}  {x^{a+1}}$$  
where  
- $x_m$ is the minimum possible value of X
- α is a positive parameter which determines the concentration of data towards the mode
- x is a random variable (x > $x_m$)   

The Pareto distribution is sometimes expressed more simply as the “80-20 rule”, which describes a range of situations. In customer support, it means that 80% of problems come from 20% of customers. In economics, it means 80% of the wealth is controlled by 20% of the population. Examples of events that may be modeled by Pareto distribution include:
- The sizes of human settlements (few cities, many villages)
- The file size distribution of Internet traffic which uses the TCP protocol (few larger files, many smaller files)
- Hard disk drive error rates
- The values of oil reserves in oil fields (few large fields, many small fields)
- The length distribution in jobs assigned supercomputers (few large ones, many small ones)
- The standardized price returns on individual stocks
- The sizes of sand particles
- The sizes of meteorites
- The number of species per genus
- The areas burned in forest fires
- The severity of large casualty losses for certain businesses, such as general liability, commercial auto, and workers compensation



 


