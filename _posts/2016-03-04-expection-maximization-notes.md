---
title: Expectation Maximization Algorithm Intuition
date: 2016-03-04 09:16:00
categories:
- Notes

tags:
- data science

---

## Understanding Expectation-Maximization Algorithm 

Two coins, each coin can generate a series of tosses. If during the experiment, you know which coin you have picked, then you can easily using the number of heads and tails to estimate the biases of these two coins. The problem in reality is that oftentimes we don’t have any information about which coin we have picked to generate the sequence of tosses. This messes everything up. Don’t worry though. We have EM algorithm. 


### Now try to entertain this idea: 
I guess coin A and coin B have biases , and their biases are $\theta_a$ and $\theta_b$ respectively. What can I do with this? Well, I can use this guess to match the observed tosses. Based on my preliminary guesses, I can assign each of the sequence to one of the coin. After the assignment, I can now do MLE on the observed tosses since I have complete dataset I need to perform MLE.  
EM is derived from the basic idea of **guessing first and then iteratively optimize**. Using the current guesses of parameters, we can calculate the probabilities of all the possible completions of the missing data.  

### What do you need to perform MLE?
The idea of MLE is that your probabilistic model and the parameters in the model should generate the observed dataset more likely than any other models. Therefore, all you need to perform MLE is 
- observed dataset 
- a probability density function that specifies parameters structure.  

Previously, we don’t have the complete dataset. Why? Because if there is only one coin, then we are good to go. But the problem is we have two different coins, in order to estimate the biases of both of these coins we have to have some observations on them before we can make estimations on them.  

Actually, EM algorithm is just a generalized way to solve MLE problem. If a problem can directly be solved by MLE, then we wouldn’t need EM anymore.  
But in reality, things aren’t ideal. When there are unobserved data, or unobservable data. EM simplifies a difficult MLE problem into a sequence of simpler optimization subproblems. Magically, these solvable subproblem will guarantee to converge to a local optima of the original MLE problem. 

 


