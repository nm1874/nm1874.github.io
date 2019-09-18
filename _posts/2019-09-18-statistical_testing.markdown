---
layout: post
title:      "Statistical Testing"
date:       2019-09-18 15:05:26 +0000
permalink:  statistical_testing
---


A statistical test is a tool to make a quantitative decision about sampled data. Although these tests are strongly related to statistical inference, one should keep in his mind that these tests are designed neither to prove nor to falsify the hypothesis. This is the reason there is no such an expression /conclusion in statistics as:
“There is sufficient evidence at the alpha level of significance to reject the claim given in the alternative hypothesis, so the alternative hypothesis is accepted. ”
Instead, there are two possible conclusions after employing statistical tests as:
•	There is sufficient evidence at the alpha level of significance to reject the claim given in the null hypothesis, so the null hypothesis can be rejected.
•	There is no sufficient evidence at the alpha level of significance to reject the claim given in the null hypothesis, so the null hypothesis cannot be rejected.
Therefore, we should select the null hypothesis as the hypothesis we are trying to falsify, i.e. there is no difference between two conditions, the difference between results / metric / test statistics occurred by chance etc. Alternative hypothesis, on the other hand, support the statement we are trying to come up with.


For example, if you have an hypothesis the earth is round, your null and alternative hypotheses should be:
Null hypothesis: Earth is flat.
Alternative hypothesis: Earth is round.
If you have a sufficient evidence to reject the null hypothesis, you may conclude that “Earth is not flat.” with a confidence interval you choose, however, it doesn’t mean that you can come up with the result of “Earth is round.”. Therefore, you should be careful about forming the null hypothesis in a proper way.
________________________________________
One-tailed vs. two-tailed hypothesis testing
Before employing a statistical test, you should define the significance level or confidence interval of your resulting inference. Two-tailed or two-sided tests are generally used if your hypothesis does not include a directional relationship. Lets make this clear with an example: If you want to compare two test statistics and your null hypothesis is that “these two test statistics are equal to each other”, two-tailed test checks both the first tests statistics is significantly greater and significantly less than the second one. 0.025 fraction of bottom and the top of test statistics’ probability distribution is considered in this case. The alternative hypothesis here is that these two statistics are not equal to each other. In one-tailed or one-sided tests, on the other hand, 0.05 of the fraction of the probability distribution is considered in interested direction. This test only checks the first statistics is significantly greater or significantly less than the second one, and completely disregards the other direction. The alternative hypothesis here is that the first test statistics is greater/less than the second one.
________________________________________
Regardless of the data you have and test you want to employ, the general procedures are always same.
1.	First, you need to formulate null and alternative hypotheses and which test is more appropriate for your sample. This step also requires a decision whether one-tailed or two-tailed test will be applied (the critical region).
2.	Then, you need to calculate the test statistics based on your sample.
3.	You should choose the significance level (the size of the critical region). This size defines how much risk we are taking, because it is actually the probability of rejecting the null hypothesis although it is true. We usually set significance level between 0.01 to 0.1.
4.	Then, you need to calculate a necessary test statistics and draw the calculation.
________________________________________
Before deciding the appropriate statistical test, first you need to have an idea about the population distribution from which sampled data is withdrawn. If you have a valid assumption about the population distribution, you can employ the proper parametric statistical test. Though employing one of the parametric tests is a common approach in the case of small deviation from the normality assumption, you should use a non-parametric statistical test when the assumption is completely violated. Here, before giving more detail about the parametric and nonparametric tests, lets talk about the four most common statistical tests in the statistics.
z-test and t-test
z-test is a univariate statistical test in which the distribution of the test-statistic (z-statistic) under the null hypothesis is assumed to have a normal distribution. It is generally employed to test whether the two population means are different than each other when the variances of those populations are known, and best used for greater than 30 samples. One of the most important assumption of z-test is that all sample observations are independent than each other.
t-test is an another univariate statistical test in which the mean of the distribution of the test-statistic (t-statistic) is known and the population variance is approximated using the observations. It is generally employed to test whether the two population means are different than each other when the variances of those populations are unknown and sample size is not big enough. One of the most important assumption of t-test is that all sample observations are independent than each other.
Use of z-test
•	To understand the significance of the difference between the sample mean and the assumed normally distributed population mean, when the population variance is known.
•	To understand the significance of the difference between two normally distributed populations, when the variances of both populations are known and equal to each other.
•	To understand the significance of the difference between two assumed normally distributed populations, when the variances of both populations are known and not equal to each other.
•	To understand the significance of the difference between an assumed proportion of binomially distributed population and observed proportion, when sample size is high enough.
•	To understand the significance of the difference between two binomially distributed observed proportion, when sample size is high enough for both samples.
•	To understand the significance of the difference between two Porisson distributed counts.
•	To understand the significance of the difference between sample correlation coefficient and a specified value of correlation, when observations are withdrawn from a normal distribution and, there is a linear relationship between variables
Use of t-test
•	To understand the significance of the difference between the sample mean and the assumed normally distributed population mean, when the population variance is unknown.
•	To understand the significance of the difference between two normally distributed populations, when the variances of both populations are unknown but equal to each other.
•	To understand the significance of the difference between two normally distributed populations, when the variances of both populations are unknown and not equal to each other.
•	To understand the significance of the difference between two population means, when the samples are paired and obtained under almost identical conditions.
•	To understand the significance of the linear regression coefficient estimates.
•	To understand the significance of the difference between sample correlation coefficient and zero correlation, when observations are withdrawn from a bivariate normal distribution and, there is a linear relationship between variables.
f-test
Statisticians showed that the ratios of the variances of the two samples which are withdrawn from a normal distribution always follow F-distribution. One main necessity of using f-test is to test whether two populations have the same variance. The difference from t-test here is that t-test is used to compare the means of the populations, rather f-test is used to compare their variances.
Use of f-test
•	To understand the significance of the difference between two population variances, when populations are normally distributed.
•	To understand the significance of the difference between two population variances, when pairs of observation are correlated and populations are normally distributed.
•	To test the hypothesis that K samples (three or more) come from populations with equal means in analyzing variance, when populations are normally distributed and samples are independent.
•	To understand the significance of the difference between two Porisson distributed counts.
•	To understand the significance of the difference between the overall mean of the K subpopulations (three or more) and the assumed normally distributed population mean, when variances are equal and samples are independent. P.S: This test might be extended to understand which linear combination of mean values of the subpopulations show significant difference than those of the others.
•	To test for non-additivity in a two-way classification, when samples are independently and normally distributed with constant variance.
•	To test the main and interaction effects for the case of a two-way classification, when every cells include the same number of observations and error is normally distributed. P.S: This test might be performed even in the case of unequal numbers of observations per cell.
•	To test the nestedness of an hierarchical classification, when samples are normally distributed.
•	To understand the significance of the multiple linear regression coefficients, when the error is independently and normally distributed with zero mean.
chi-square test
This test is generally used for testing related with categorical variables. There are mainly two types of chi-square tests which are goodness of fit test and test for indepedence (consistency). The goodness of fit test is used to test whether observations match with a distribution. The independence test, on the other hand, used to compare two variables in a contingency table to see whether they are related.
Use of chi-square test
•	To understand the significance of the difference between a sample variance and assumed normally distributed population variance.
•	To understand the significance of the differences between a population variance and assumed normally distributed population variance.
•	To understand the significance of the difference between an observed value and the expected value. It is also called as “goodness of fit” test because it determines how well observed distribution fits the known theoretical distributions such as normal, binomial, Poisson etc. To employ this test, observed data is divided into K intervals. The observed and theoretical distributions should have the same number of observations. Each K intervals should have the expected frequency of at least 5 and these frequencies should be obtained by random sampling.
•	For consistency: To understand the significance of the differences between observed frequencies of two dichotomous distributions. Each intervals should have the expected frequency of at least 3 and total frequency should be greater than 20. It should be noted that Yates’ correction might be necessary for discrete values that is obtained from continuous distribution. Additionally, this test might be also used for understanding the differences between K observed frequency distributions with a dichotomous classification, two distributions based on two samples spread over K classes when samples are sufficiently large enough.
•	To understand the appropriate probabilistic model for the observations when intervals have same number of elements.
________________________________________
These are the common 4 tests used in statistical inference. For validating your results, you may need a valid statistical method. You should first decide whether you need a parametric or non-parametric test. According to the number of sample you are testing, you can use the following charts for deciding the statistical test you need.
Colors represent tests for central tendency (pink), association (yellow), randomness (gray), variability (orange), proportion (blue) and distribution (green).

