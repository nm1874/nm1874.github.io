---
layout: post
title:      "Statistical Distributions"
date:       2019-09-07 19:47:55 -0400
permalink:  statistical_distributions
---


One key field of statistical knowledge we need before tackling the definition of statistical significance and analyzing test results of A/B testing is probability distributions. We would need to know how our data is shaped in order to choose the right statistical test for various distributions. 
Several key types of distributions that are common in A/B testing include:
-	Binomial distribution
-	Normal distribution 
-	T-distribution 
-	Chi-Square distribution 

**Binomial distribution **

-	This type of distribution occurs when there’re only two possible outcomes for each trial, these trials are independent and have been repeated a certain number of times. Some examples include: users churned/returned, coin flips, games won/lost, and etc.
-	These following criteria must be met for the experiments’ outcomes to have a binomial distribution
o	There’re n trails 
o	Each trial is independent, i.e. knowing the result of one trial gives us no information on the results of other trails 
o	Each trial has exactly two outcomes, i.e. success or failure, with probabilities p and q (or 1-p)
-	Knowing the probability of success (p), the number of trials (n) and the number of successes (x), we can plot the binomial distribution using the following formula
o	 
o	This formula tells us the probability to get exactly x number of successes in n trials, given that we know the probability of success (p) and the number of trials (n)
-	Example (1)
o	Let’s say that we have 100 users (n=100), and only 30 of them have returned on the next day after installing the game (x=30). We know that the probability of a user to return (or the so called retention rate) is 70% (p=.7). So, then what is the probability to get only 30 returners from 100?
o	Using the binomial distribution’s formula provided above,
	 
o	The probability is close to zero, which means it’s a highly unlikely situation.
o	We can plot the distributions with different probabilities p to see how likely and unlikely a certain number of successes (x) could occur.
	 
o	Lastly, the binomial distribution is a discrete distribution. Since x, is the number of successes in n trials, it can only take the number 0, 1, 2, 3, 4…n. 
o	Its mean and standard deviation can be found using the following formulas
	 

**Normal distribution **

-	One of the most popular and well known distributions on the world of statistics, also called Gaussian distribution. 
-	The following criteria must be met for the experiments’ outcomes to be considered normal: 
o	The mean, median and mode of the distribution are all equal 
o	The curve is symmetric at the center (i.e. around the mean, μ)
o	All the values are symmetrically distributed around the mean (exactly half of the values are to the left of mean and exactly half the values are to the right)
o	The total area under the curve is equal to 1
-	Additionally, knowing the standard deviation and the mean you can say the probability of getting exact values.
o	 
-	The statistics formula for a normal distribution is the following 
o	 
-	The normal distribution is fully described by two variables: the mean μ (aka median and mode) and the standard deviation σ.
o	 
-	If μ = 0 and σ = 1, the normal distribution can also be called the standard normal distribution (aka Z-distribution).
o	 

**Student’s T-distribution**

-	T-distribution can be seen as the shorter and fatter cousin of the Normal Distribution. It’s used when you have a small sample size (usually in practice less than 30). The larger the size of the sample size, the more the t-distribution looks like the normal one. 
o	 
-	The following formula can be used to describe the T-distribution:
o	 
-	Γ is the symbol for gamma-function and v is the degrees of freedom. 
-	The calculations for the mean and standard deviation are slightly different from the Normal Distribution as we usually assume that the given data is a sample from a certain population. Therefore, we must use sample means and sample standard deviation instead of mean (μ) and standard deviation (σ). Instead of using the number of samples (n) we use the degrees of freedom (v = n-1).
o	 
-	T-distribution also has its own version of Z-score, called T-score, used heavily in statistical tests:
o	 

**Chi-Square distribution **

-	Chi-Square distribution is widely used for statistical testing of categorical data.
-	Chi-square distribution is a special case of gamma-distribution (just like T-distribution), and has only one parameter: degrees of freedom (v). The distribution only has positive values, and it’s right-skewed. Its shape varies depending on v: from very asymmetric with low v, to almost symmetric with very high v (with v approaching infinity, chi-square distribution becomes normal distribution). 
o	 
o	 
o	 
-	The mean = the number of degrees of freedom.
-	The standard deviation = square root of two times the number of degrees of freedom. 
-	Chi-Square’s own metric for statistical testing is the following:
o	 
	Oi is the number of times i-category occurred in a sample, or the so called observed frequency 
	Ei is the assumption of the number of times i-category that should occur, or the so called expected frequency. 
-	The assumption Ei is something we check for with statistical testing. 

