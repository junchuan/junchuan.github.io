---
title: Generate random numbers from various probability distributions
date: 2015-03-12 19:39:18
categories:
- Data Science

tags:
- algorithm
- data science
- random number

---


## Uniform Distribution

+ congruential method :  

$$  

x_{i+1}=(ax_i+c)\mod\;  m, i=1, 2, ...,n-1
  
$$  

-  we should choose a, c, m carefully. e.g., [$a = 25214903917, c = 11,  m = 2^{48}$](https://docs.oracle.com/javase/6/docs/api/java/util/Random.html#next(int))

+ Uniformly distributed numbers on [0,1] can be obtained by : $u_i= {x_i \over {m-1} }, i=1,2,...,n$

+ Uniformly distributed numbers on [a,b] can be obtained by : $u_i=a+ {x_i \over {m-1} } {(b-a)}, i=1,2,...,n $

## Bernoulli Distribution

- Generate `u` from `uniform(0,1)`, if `u < p` , then return 1, else return 0. 

## Binomial Distribution 
- Generate $y_1,y_2,...,y_n$ from bernoulli distribution, return $y_1+y_2+...+y_n$.

## Cauchy Distribution $C(\alpha,\beta)$
- Generate `u` from `uniform(0,1)`,return $x={ \alpha- {\beta \over tan(\pi u)}}$

## Empirical Distribution
- Generate `u` from `uniform(0,1)`, let `i` be the integer part of $(n-1)u + 1$, return 
$a_i + [(n-1)u-i+1]{(a_{i+1}-a_i)}$

## Exponential Distribution
- Generate `u` from `uniform(0,1)`, return $-\beta ln(u)$

## Erlang Distribution $ER(k,\beta)$
- Generate $y_1,y_2,...,y_k$ from exponential distribution $exp{(\beta \over k)}$, return $y_1 + y_2 +... +y_k$

## Gamma Distribution $G(\alpha,\beta)$
>
$x=0$  
$repeat:$  
$\quad	generate \; v \;  from \;  exp(1)$  
$\quad x=x+v$  
$\quad \alpha=\alpha-1 $  
until $\alpha=1$  
return $\beta x$  


## Beta Distribution
- Generate $y_1$ from gamma distribution $G(\alpha,1)$
- Generate $y_2$ from gamma distribution $G(\beta,1)$
- $x= {y_1 \over {y_1 + y_2}}$
- return x


## Weibull Distribution $W(\alpha,\beta)$
- Generate v from $exp(1)$
- return $x={\beta v^{1 \over \alpha}}$

## Geometric Distribution GE(p)
- Generate `u` from `uniform(0,1)`
- return the integer part of $ln(u) \over ln{(1-p)}$

## Negative Binomial Distribution $NB(k,p)$
- Generate $y_1,y_2,...,y_k$ from geometric distribution `GE(p)`
- return $y_1+y_2+...+y_k$

## Logistic Distribution $L(a,b)$
- Generate `u` from `uniform(0,1)`
- return $ a-{bln({1 \over u}-1)} $

## Normal Distribution $N(u,\sigma)$
- Generate $u_1$ from `uniform(0,1)`
- Generate $u_2$ from `uniform(0,1)`
-  $z=[-2ln(u_1)]^{1 \over 2} sin(2\pi u_2)$
- return $u+\sigma z$

## Chi-Square Distribution
- Generate $z_i, i=1,2,...,k$ from $Normal(0,1)$
- return $z_1^2+z_2^2+...+z_k^2$

## F Distribution  $F(k_1,k_2)$
- Generate $y_1$ from chi-square distribution $Chi(k_1)$
- Generate $y_2$ from chi-square distribution $Chi(k_2)$
- return $y1 / k1 \over y2/k2$

## Student Distribution $S(k)$
- Generate z from $N(0,1)$
- Generate y from $Chi(k)$
- return $z \over {\sqrt {y/k}}$

## Lognormal Distribution  $LogN(u,\sigma^2)$
- Generate z from $N(0,1)$
- $x=u+\sigma z$
- return $exp(x)$

## Multinormal Distribution $N(u,\Sigma)$
- Generate an upper triangular matrix C such that $\Sigma=CC'$
- Generate $u_1,u_2,...,u_n$ from $N(0,1)$
- $x_k=u_k+ \sum_{i=1}^k c_{ki}u_i , (k=1,2,...,n)$
- return $x=(x_1,x_2,...x_n)$

## Triangular Distribution T(a,b,m)
- $c={(m-a)} \over {(b-a)}$
- Generate u from $uniform(0,1)$
- If $u < c$, then $y=\sqrt {cu}$
- else, $y=1-{\sqrt {(1-c)(1-u)}}$
- return $a+(b-a)y$

## Poisson distribution $P(\lambda)$
>
x=0  
b=1  
`mark`  
generate u from $uniform(0,1)$  
b=bu  
if $b > e^\lambda$, then $x=x+1$ and goto `mark`  

return x.

