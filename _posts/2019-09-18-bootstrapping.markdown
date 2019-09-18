---
layout: post
title:      "Bootstrapping"
date:       2019-09-18 15:06:46 +0000
permalink:  bootstrapping
---


Bootstrapping is an additional way to simulate the distribution of the effect size.
Instead of using natural variation arising from the treatment assignment in your data, bootstrapping explores uncertainty over the specific sample of the population you draw. The idea is that the most natural distribution to assume your data follows is the one that was actually observed in your sample. So just sample from your data with replacement to create a simulation.
The procedure works as follows:
1.	You use historical data for a power analysis or to calculate a p-value for your experimentally measured effect. You use the actual data from the outcome of your experiment to build a confidence interval.
2.	Randomly draw with replacement from your data set (at the highest cluster level if your assignment is clustered) until you create a data set the same size as in your experiment (a bootstrap). Drawing a lower level will artificially raise your precision.
3.	Calculate the test statistic using the simulated data set
4.	Repeat the above steps many times
5.	The distribution of the calculated test statistics from the various hypothetical random samples with replacement can be considered the distribution of the test statistic under the null distribution when using historical data or under the true effect size when using the experimental data.
6.	When using historical data, the minimum measurable effect for a power analysis is still the 95th minus the 20th percentile. The p-value is still 1 minus the percentile of the actual measured effect in the distribution of simulated effect sizes. The bounds of a confidence interval can be found using the 2.5th and 97.5th percentiles of the bootstrapped effect sizes when drawing with replacement from the true experimental results.
Example
With bootstrapping, we need to have an initialized hypothetical treatment so when we sample with replacement, the treatment comes with it.
Randomization Inference vs Bootstrapping
Titans of causal inference Susan Athey and Guido Ambens “stress randomization-based inference as opposed to sampling-based inference.” That link is a great one to read for more information. I prefer randomization inference to bootstrapping for a couple of reasons.
•	It is easier to identify bias in your design using randomization inference. As shown in the article, we have a simple gut check on the experimental data to determine whether or not our design methodology is biased: check if the simulated effect sizes under the null using the experimental data has mean 0. It is much harder to do this check with bootstrapping because if you resample the experimental data, it should be centered at the measured effect size, not 0. You could use historical data and see if the bootstraps aren’t mean 0, but often some non-linear time difference in the experimental period causes the bias (which cannot be seen with historical data).
•	Randomization inference automatically accounts for correlation in clusters in your sample. A very common error in statistical analysis is to not account for clustered standard errors. If we assign treatment at the cluster level (like geography above) and then perform an analysis at the unit level (e.g., customer), the default standard errors that regressions or a t-test would spit out don’t account for correlation in the assignment of treatment and you can overestimate how much precision you actually have. But with randomization inference, as long as you assign treatment the same way as in your experiment in the simulations, it will automatically account for these clustered standard errors. This is a big reason why I recommend bootstrapping at the cluster level as well: resampling at the unit level for a cluster assigned treatment can produce an inconsistent estimate of the variance.
•	Randomization inference is usually faster. Bootstrapping requires a very computationally expensive random sampling with replacement for each simulation, whereas randomization inference just requires a reassignment of treatment. However, randomization inference can be slower if reassigning the treatment is expensive (e.g., if you expose half of products classes to treatment and then calculate each customer’s percent of products seen as their applied treatment, you’d have to calculate for each customer the percent of products seen with treatment for each new treatment assignment, which would be very expensive).


