---
layout: post
title:      "Hypothesis Testing"
date:       2019-09-18 14:55:56 +0000
permalink:  hypothesis_testing
---


The content Hypothesis tests are necessary to evaluate the likelihood of the estimates obtained from a representative sample being equal to the real parameters on some population which cannot be observed. 
There’s always a situation which is considered as the default, or the conservative scenarios, the one you’d be better to keep if you’re not enough sure of your assumption. This is the null hypothesis, or H0. On the other hand, there’s the alternative scenario, that if accepted, will change the status quo ante. It’s the alternative hypothesis, or H1. 
One pivotal thing we need to know before running hypothesis tests is the distribution of our data. In this post, we’ll use the Stand Normal as the example. 
To standardize a normal distribution of one sample, the procedure is the following:
The value z is called z-score and it expresses the number of standard deviations that lie between the mean of a population and the value of a data point. 
For instance, if we received a score of 30 to our exam, with the average of the class being 25 and the standard deviation being 3. Our z-score will be equal to: 
That means we’re 1.67 standard deviations above the mean. 
Note: When you have multiple samples and want to describe the standard deviation of those sample means, you would use this formula for z-score:

The z-score is necessary for us to compute the probability of our hypothesis and hence decide, with a given level of confidence, whether to reject or not reject the null, H0. 
Imagine the population mean of the exam of the above example being 25. However, after selecting a sample of 30 students, it turns out that their mark average is higher, let’s say 28. The question that might arise is whether this evidence is sufficiently strong to state that the population’s mean is higher than 25. Your hypotheses will be:
-	H0: “the mean is equal to 25”
-	H1: “the mean is greater than 25”
Whenever statisticians are asked to make inference on some population parameters, which cannot be observed, they need to start from a representative sample of that population. However, once obtained the estimate of that parameter (called statistic), how can they state whether it corresponds to the real parameter, since the latter is unknown?
Because of the impossibility of comparing the two results (again, one is not observable), it will be necessary to make some assumptions and run the so-called hypothesis tests.
Those tests are meant to evaluate the likelihood of the estimate of being equal to the real parameter. The idea is that it always exists a situation which can be considered as the default: it is the conservative scenario, the one you’d be better to keep if you are not enough sure of your assumption. This situation will be our Null Hypothesis, or H0. On the other hand, there is the alternative scenario, that, if accepted, will change the status quo ante. It is the Alternative Hypothesis, or H1.
Those hypotheses have a meaningful interpretation, and the penalty for taking the wrong decision is not balanced. Indeed, if you decide to reject the Null because of your findings and it turns out that it was actually true, you are falling in the worst scenario you could face: indeed, you are rejecting the conservative status which is, let’s say, your ‘comfort zone’. On the other hand, not rejecting the Null when the Alternative is true is not as bad. To make it easier, let’s consider the following example.
Imagine you are a doctor and you have to decide whether to hospitalize a patient. You are very prudent and you normally prefer to hospitalize your patients for at least one night in case of doubts, however it is highly costly for your structure to do so. Hence you decide to set these two hypotheses:
•	H0: ‘the patient needs to be hospitalized’
•	H1: ‘the patient does not need to be hospitalized’
Imagine that the patient actually needs to be hospitalized, but you are convinced of the contrary: you will send back home someone in severe conditions, with potential terrible results. On the other hand, if you decide to keep the patient for the night, but it turns that he was perfectly sane, you lose some money for sure, but this scenario is not as bad as letting someone dying because of negligence.
With that being said, how can we concretely run hypothesis tests? Well, to do so, it is pivotal to know the distribution of your data. Here, we will use the Standard Normal, which has the well-known bell shape and exhibits mean=0 and standard deviation=1.
To standardize a normal distribution of one sample, the procedure is the following:
The value z is called z-score and it expresses the number of standard deviations that lie between the mean of a population and the value of a data point.
Namely, imagine you obtained a mark of 30 to your exam, with the average of that exam being 25 and the standard deviation being 3. Your z-score will be equal to:
It means that your mark is 1.67 standard deviations above the mean. Let’s visualize it:
Note that, when you have multiple samples and want to describe the standard deviation of those sample means, you would use this z score formula:
Where n=size of the sample.
Nice, but which is the link with Hypothesis test? Well, the idea is that you need z-score to compute the probability of your hypothesis and hence decide, with a given level of confidence, whether to reject or not reject the Null. Let’s see how with the following example.
Imagine the population mean of the exam of the above example being 25. However, after selecting a sample of 30 students, it turns out that their mark average is higher, let’s say 28. The question that might arise is whether this evidence is sufficiently strong to state that the population’s mean is higher than 25. Your hypotheses will be:
•	H0: “the mean is equal to 25”
•	H1: “the mean is greater than 25”
Then, you have to set the so-called significance level, which is a margin of error with which you are willing to reject the null hypothesis. The significance level, indicated with α, is hence the probability of making the wrong decision when the null hypothesis is true. It generally assumes values like 1%, 5% and 10% and it corresponds to the area of rejection of the null hypothesis when it is true.
Namely, having α=5%, since the distribution is symmetric, we will have two critical values of z-scores, indicated as Zα/2 and -Zα/2, which are the boundary of the acceptance area (the green one), while the red fields represent the rejection areas:
And here comes the importance of knowing the probability distribution. Indeed, thanks to our known Standard Normal, we can use the Tables containing the probability associated with each z-score.
Namely, if we want to approach the problem above with α=5%, we have to find those critical z-scores which determine an acceptance area of 95%. Hence, they will leave in the tail a probability of 2.5% for each side and we can easily read on our table that those values are, respectively, -0.67 and 0.67.
Now, we can compute the z-score of our problem:
Since the z-score falls out of the acceptance area, we can reject our null hypothesis of the population mean being equal to 25: we have enough evidence (with a significance of 5%) to reject that hypothesis.

This problem can also be solved with a different approach. Imagine that, instead of your z-score, you want to compute the probability of occurrence of the actual sample mean (or a more extreme value of it). In other words, how likely was, ex ante, obtaining a sample mean equal to or greater than 28?
Since z-scores greater than 3.89 (or less than -3.89) produces a probability of 0, our result will be zero (approximately). It means that the likelihood of obtaining that sample mean was so low (barely impossible) that the fact that occurred suggests that the real distribution of the population has not mean equal to 25. The value of that probability is called p-value.
In general, if the p-value is less than the significance level, we can reject the null hypothesis.
Hypothesis tests are powerful tools that can be run in a variety of situations. In this article, we see the example of a parametric hypothesis test, however they can also be referred to a probability distribution, absence of correlations among data, interval estimates and so on.
In my previous article, I’ve been talking about statistical Hypothesis tests. Those are pivotal in Statistics and Data Science since we are always asked to ‘summarize’ the huge amount of data we want to analyze in samples.
Once provided with samples, which can be arranged with different techniques, like Bootstrap sampling, the general purpose is making inferences on real parameters, belonging to the original populations, by computing so-called statistics or estimators from our sample.
However, we need some kind of ‘insurance’ that our estimates are close to the reality of facts. That’s why we use Hypothesis tests.
In this article, I’m going to provide a practical example with Python, with randomly generated data, so that you can easily visualize all the potential outcomes of the test.
So let’s start by generating our data:
As you can see, I manually generated normally distributed data, with mean=3 and standard deviation=2. Now, the idea is extracting a sample from this population and checking whether it was actually extracted from a population with mean=3. For this purpose, since I want the visualization to be clear, I will create another manual distribution, still normal, but with a different mean ( just imagine it was taken from the population).
Since I manually created a sub-sample of this population with mean deliberately less than 3 (actually 1.5), our hypotheses will be:
First, let’s have a look at both the distribution:

So in red we have our sample distribution, while in blue our real population distribution. In this case, we already know the answer to our problem: our sample does not arise from a population with the blue distribution, and it is obvious since I did not extract that sample from our population. However, what if you are not provided with the real population distribution? We need to inquire about the likelihood of the mean of our sample to be equal to that of our population.
Hence, let’s compute the confidence interval of our sample. Just to recall, a confidence interval of x% expresses that, given a population and a collection of samples from that, in 95% of those samples the sample mean (or whatever parameter you are inquiring about) will be included in that interval.
We can easily compute the interval, with confidence=95%, with a scipy tool:
Now let’s inquire at the possible outcomes of our test:
As you can see, the sample mean (1.5) is included in the Type 2 Error area (meaning that we do not reject the null when it is false). To double-check, let’s compute the p-value, keeping in mind that our confidence level is 5% (hence, we do not reject the null if the p-value is greater than 5%).
As you can see, our test confirmed what it is displayed in the picture above: we can say with 95% confidence that our sample has been extracted from a population with mean=1.5. Of course, we know that it is not true, since the real population has mean=3. So, how could we handle this inconsistency? The answer is that we can’t. I mean, we could shorten our confidence interval, but be aware that this could lead to a Type 1 Error (rejecting the null when it is true).
So, the idea is balancing the size of your confidence interval depending on the kind of task you are facing. Namely, if rejecting the null when it is true would mean a tremendous loss of revenues, you’d rather keep your confidence interval large enough, so that only truly extreme values would lead to a rejection of your Null.
of your blog post goes here.
