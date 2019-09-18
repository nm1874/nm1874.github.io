---
layout: post
title:      "Geometric and Inverse Binomial"
date:       2019-09-18 15:03:48 +0000
permalink:  geometric_and_inverse_binomial
---



In this blog, I’m going dwell on their so-called ‘counterparts’, which are Geometric and Inverse Binomial.
Both of them concerns the idea of a sequence of Bernoulli trials, hence it is worth it to recall when we are facing a Bernoulli random experiment.
The Bernoulli distribution is the discrete probability distribution of a random variable which takes a binary, boolean output: 1 with probability p, and 0 with probability (1-p). The idea is that, whenever you are running an experiment which might lead either to a success or to a failure, you can associate with your success (labeled with 1) a probability p, while your insuccess (labeled with 0) will have probability (1-p).
The probability function associated with a Bernoulli variable is the following:
The probability of success p is the parameter of the Bernoulli distribution, and if a discrete random variable X follows that distribution, we write:
Now, we know that if we run multiple Bernoulli trials and we are inquiring about the probability of having exactly k successes, we are dealing with a Binomial distribution.
But what about the number of trials we need to obtain one (or more) success?
Geometric Distribution
The idea of Geometric distribution is modeling the probability of having a certain number of Bernoulli trials (each with parameter p) before getting the first success. Of course, the number of trials, which we will indicate with k, ranges from 1 (the first trial is a success) to potentially infinity (if you are very unlucky).
So let’s intuitively derive the probability function with the following example. Imagine you are flipping a coin and you want to obtain Head (H). Hence, H will be your success. Each flipping is a Bernoulli random variable with probability p of having H, and (1-p) of having Tail (T).
Your goal is computing the probability that exactly k trials are necessary to obtain your first H. Hence, our random variable X will be:
X = “number of Bernoulli trials to get the first success”
So the situation can be modeled as follows:

We want to compute the probability of having first k-1 failures, each with probability 1-p, and then, at the kth trial, having a success (with probability p). Since each Bernoulli trial is independent from the others, we will have:
And we write:
To say that our random variable X has a geometric probability function.
Inverse Binomial Distribution
If the Geometric distribution counts the number of trials to have the first success, the Inverse Binomial model the probability of having x trials to get exactly k successes.
Again, let’s model our Inverse Binomial with the same example as before. However, this time let’s say we want to compute the probability of having x trials to get exactly k Heads. The key difference here is that we can have different combinations of this situation: the only constraint we have to respect is that the last outcome of our x trials has to be a success, otherwise to have k successes it would have been sufficient a lower number of trials.
Hence:
Since each failure has probability (1-p) and each success has probability p, we obtain that the probability of having x trials before getting exactly k successes is given by:
Where:
is the binomial coefficient and it’s used to compute all the possible combinations. Furthermore, we write:
To say that our random variable X follows an Inverse Binomial with parameters k,p.
As you can see, in the geometric distribution, as the number of trials increases, the probability decreases. On the other hand, with the Inverse Binomial, having three successes at the first three trials is less likely than having them in more than 3 trials. However, after a certain number of trials (5) the probability decreases again.


