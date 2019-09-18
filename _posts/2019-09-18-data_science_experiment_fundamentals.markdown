---
layout: post
title:      "Data Science Experiment Fundamentals"
date:       2019-09-18 11:06:16 -0400
permalink:  data_science_experiment_fundamentals
---


Randomized experiments are the gold standard for causal inference: if you want to get an unbiased (the average value of your estimation method is the true value) estimate of an effect of a treatment, a randomized experiment is the best way to do so.
But experiments are expensive. So if we are going to make the investment to do one, we need to know we’ll be able to collect enough data in the experiment to have a high chance of measuring an effect if it exists. A power analysis will tell us how much data we need.
We also want to know that the effect we measure isn’t just the result of chance. We declare our effect statistically significant only if the chance that we would measure an effect as extreme as the one we measure in our experiment if the treatment has no effect (the p-value) is sufficiently low.
Additionally, we would like to be able to give some sense of how precisely the effect is measured by providing a confidence interval — a range of values of the effect, which if calculated the same way for many experiments repeated the same way, would include the true effect a large percent of the time (e.g. 95%).
Finally, we’d like to know if our experimental design is flawed such that we don’t have a way to measure an effect in an unbiased way.
This post will enable you to do a power analysis, calculate p-values, get confidence intervals, and check for bias in your design without making any assumptions (non-parametrically).
Example Experiment
Let’s say I’m a dog football marketer. In previous advertisements, I’ve used the picture on the left below to showcase how fun dog footballs are. I hypothesize that if I add a funny note like “Teddy Approved”, a larger portion of people (p) who see the ad will purchase a football (p is called the “conversion rate”).
To test my hypothesis, every time a person is about to see one of my ads, I’ll randomly show them one of the two images: a control image (with no label) or a treatment image with “Teddy Approved”. Then, I’ll compare the conversion rates within the groups (p_{control} vs. p_{teddy_approved}) to see if the label improves conversion (conversion = # customers ordered football / # customers saw the ad).
Hypotheses
The null hypothesis is the assumption that there is no effect: that adding “Teddy Approved” to the ad will not increase conversion:
H_0: p_{teddy_approved} — p_{control} = 0
We test this against our alternative hypothesis that the label increases conversion.
H_a: p_{teddy_approved} - p_{control} > 0
We do this by calculating the chance that we would see our experimental test statistic (the difference in conversion rates among customers that saw the label and those that didn’t \hat{p}_{teddy_approved} - \hat{p}_{control} ) given the null hypothesis is true (i.e., a p-value). If that chance is low enough (e.g., <5%), we reject H_0 and can say that the label significantly (in the statistical sense) increases conversion. In our power analysis, we’ll determine how large the true difference p_{teddy_approved} — p_{control} will need to be or how much data we will need to collect to have a high chance (e.g. >80%) of observing a test statistic with a significant p-value (i.e., a high power).
The key here is we need to be able to calculate the probability of seeing different values of our test statistic under the null hypothesis: we need to have a sense of what the distribution of the difference in our sample conversion rates \hat{p}_{teddy_approved} - \hat{p}_{control} looks like given the true difference in conversion rate is 0: p_{teddy_approved} - p_{control} = 0.
We could use some parametric assumptions. For example, we could assume normality and perform a t-test. However, in many settings, data is highly skewed and this assumption won’t hold. It would be better if we could simulate the difference in conversion rates non-parametrically (without any assumptions), and trace out this distribution ourselves. To do that, we’ll need some data.
Historical Data
Let’s assume we have historical information where the label was not applied: we have a data set of customers that have seen the control group image and whether or not they purchased a football. If the null hypothesis is true, the data generating process for this historical data’s conversion rates should be similar to the process during the experiment because adding the label has no impact on conversion.* That is, we could consider this historical data set to be similar to a realization of a hypothetical data set collected during the experiment under the null hypothesis.
*note we are assuming time isn’t impacting the variability in the conversion rate. If we aren’t interested in using the simulation to do a power analysis (e.g., we just want to calculate confidence intervals/p-values or confirm our design isn’t biased), we can apply randomization inference on the true experimental data to remove this assumption.
Let’s create a toy historical data set assuming conversion is independent between customers and that the true probability of purchase after seeing the control ad, p_{control} is 0.01.
Simulating Under the Null
With our historical data set, there are 2 key ways to simulate example differences in observed conversion rates between groups \hat{p}{teddy_approved} — \hat{p}{control} under the null hypothesis:
1.	Randomization Inference — explore how much variability comes from random assignment to control and treatment groups
2.	Bootstrapping — explore how much variability comes from the data generating process
We’ll focus on randomization inference, but bootstrapping is also described at the end of this post.
Randomization Inference
Randomization Inference is my preferred method for identifying variability in your data. I first came across it in Field Experiments by Gerber and Green. This book is a rigorous, concise, and well-written introduction to notation for causal inference and experimental methods. I highly recommend it.
The idea behind randomization inference is that uncertainty arises naturally from the random assignment to treatment groups. It’s kind of like answering the question: what would the effect size have been if we just assigned our treatment groups differently?
The procedure to simulate your effect is as follows
1.	Have a data set that has the same number of experimental units as you will have in your experiment. You could use historical data to do a power analysis or the actual data from the outcome for your experiment to get p-values and confidence intervals.
2.	Randomly assign a hypothetical treatment within your data set. The treatment assignment methodology should follow the same assignment methodology you would use / used in your experiment (e.g. if you assigned clusters to treatment, do that here as well).
3.	Calculate the test statistic using the hypothetical treatment assignment
4.	Repeat the above steps many times
5.	The distribution of the calculated test statistics from the various hypothetical random assignments can be considered the distribution of the test statistic under the null distribution.
Power Analysis
Now that we know how to get simulated effect sizes, we are ready to perform a power analysis. The idea behind a power analysis is that we want to know how much data we need to have a high chance of getting a statistically significant result. We want to do this before the experiment begins so we don’t waste time and money running an experiment that can’t measure anything.
Let’s say we’ll declare the change in conversion significant if there is a 5% or less chance of seeing that change in conversion or greater under the null hypothesis. We traced out the effect size distribution under the null in the previous section, so it’s easy to find this critical value point (it’s just the 95th percentile of our simulated effect sizes).
Let’s say we want to have at least an 80% chance of getting a significant result. The trick here is to assume that the true effect size is constant, such that we can just shift the distribution of effect sizes under the null by the true effect size. We shift the distribution until 80% of the area under it is beyond the critical region. The amount we need to shift is called the minimum measurable effect (“MME”) because it is the smallest true difference in conversion that we would be able to get a statistically significant result with at least 80% probability. This minimum measurable effect can be calculated by taking the difference between the critical value and the 20th 
A minimum measurable difference in the conversion rate of 0.019 does not seem plausible given our conversion rate started at 0.01. However, all of this was assuming we would collect 1000 customers during the course of our experiment (just like we had in the historical data). We can 
With a lot more data the minimum measurable effect is reduced to 0.0016, which is still big, but at least a possible effect size to measure.
The increased precision is more noticeable if we plot the two simulated distributions together:
Check for Bias
In our example, we have used a very clean experimental design: we compared apples to apples groups (because customers were randomly assigned to them) in the same period and calculated a difference in means. In this situation, the measured difference in conversion will be an unbiased estimate of the true difference in conversion caused by the added label: though the treatment effect we measure is random, on average, it will be the true treatment effect:
E[\hat{p}{teddy_approved} — \hat{p}{control}] = p_{teddy_approved} — p_{control}
We can do a gut check that this is true by confirming that the average of our simulations under the null of the effect size is near 0: under the null p_{teddy_approved} — p_{control}=0, so \hat{E}[\hat{p}{teddy_approved} — \hat{p}{control}] =\frac{1}{n}\sum_{i=1}^{n}\hat{p}{teddy_approved} — \hat{p}{control}\approx 0 if we have an unbiased design.
We pass this gut check given the mean is so close to 0. Even though this doesn’t confirm the design is unbiased, it gives us more confidence that it is.
However, many experiments do not have such a clean design and the measured effect size can be prone to bias. In such a case, you should do all you can to correct the design so that it is unbiased. However, there may be a situation where you run an experiment and cannot correct the bias post-experiment. In such a case, you may still be able to use the same p-value methodology so long as the bias is applied uniformly: randomization inference still indicates the actual assignments measured effect size is in the top 95% of measured effect sizes under other hypothetical assignments even if all the measured effects are biased. However, you’ll need to adjust your reported effect size and thus confidence interval. One quick and dirty way to do so is to just report the measured effect size minus the average of the simulated effect sizes under the null distribution. Then, make a confidence interval the same way as above, but centered at that adjusted effect size instead.
Summary
In this post we’ve gone over non-parametric ways to
•	simulate the effect size under the null distribution: hypothetically randomly reassign treatment and calculate the effect size with the hypothetical assignment many times.
•	do power analyses: the minimum measurable effect is the 95th percentile minus the 20th percentile of the simulated effect sizes under the null.
•	calculate p-values: find what proportion of simulated effect sizes under the null are more extreme than the measured effect size in the experimental data.
•	get confidence intervals: center the distribution of effect sizes under the null at the measured effect size and get the 2.5th and 97.5th percentiles for confidence bounds.
•	check and adjust for bias: mean of the simulated effect sizes under the null should be 0. If it isn’t, adjust the measured effect size by the mean of the simulated effect sizes under the null (and use the adjusted effect size for centering confidence intervals).

