---
layout: post
title:      "Poisson Process"
date:       2019-09-18 15:00:53 +0000
permalink:  poisson_process
---

In my previous article I covered several topics on the Poisson process. A topic I did not cover was the intuition for why the Probability Mass Function of the Poisson distribution looks like this:
Probability Mass Function for the Poisson Distribution
In other words, if λ events occur per unit time, why does the above formula yield the probability of k events occurring in time t?
Various texts on the Poisson process explain how the Poisson distribution is the limiting case of the Binomial distribution i.e. as n → ∞, the Binomial distribution’s PMF morphs into the Poisson distribution’s PMF. At least that is how the math works.
But the PMF is more than just math. It can be used to model real events happening in our lives. If I am a restaurant owner, I can use the Poisson PMF to determine how many booths to install and how many chefs and waiters to hire. I can use the Poisson PMF to do capacity planning for my business.
So in the context of real phenomenon, if the probability of k events occurring in t is what we want to know, why is the Poisson PMF, the way it is structured, able to answer this question so well?
That’s the question we’ll answer in this article.
A very simple experiment
Let’s begin with a simple scenario. Say you are an apple inspector. Your job is to pick up an apple, visually inspect it, smell it and decide whether to mark it as good or bad. You are good at your job and you are able to test 60 apples an hour, i.e. an apple a minute. Say each one of your inspection sessions lasts for one hour. I don’t know about you, but my nose will need a break after an hour of sniffing.
From working through many such sessions, you have found that for any given apple, the odds of it being a bad apple are 5%, and of it being a good apple are correspondingly 95%. The inspection of an apple is a simple Bernoulli trial.
In general, a Bernoulli trial in which the probability of running into a bad apple is p will yield the following Probability Mass Function for the corresponding Bernoulli distribution:
PMF for the Bernoulli distribution
________________________________________
From the Bernoulli to the Binomial
One day, when you show up at work, your supervisor asks you to submit data on the odds of finding 1, 2, 3,…,k bad apples during any of your one hour apple testing sessions.
Such a request might flummox an apple inspector, but not you, for you are an apple inspector only by day. By night you are a math ninja. So without batting an eyelid, you deliver the results to your supervisor using the following Binomial Distribution:
PMF of a Binomial distribution
In our case, p=0.05 and n=60.
________________________________________
Re-interpreting the Binomial distribution in the time domain
As you progress through your apple testing career, you deduce another fact. On average, you seem to be running into λ number of bad apples during your hour long apple testing sessions.
Since these λ bad apples are assumed to be uniformly distributed across the 60 minutes of testing, the probability of encountering a bad apple in any particular minute of that hour is λ/60. This is a simple but key insight for understanding the Poisson distribution’s formula, so let’s make a mental note of it before moving ahead.
We are now in a position to interpret the Binomial distribution PMF in the context of time, instead of in terms of the number of Bernoulli trials n.
By substituting ( λ/60) for the probability p in the Bernoulli distribution’s PMF, we can say that the probability of running into k bad apples in 60 minutes of testing is as follows:
Probability of running into k bad apples in 1 hour of testing
As time passes, you become efficient at inspecting apples so that you are able to test 360 apples per hour, i.e. 1 apple every 10 seconds. Since λ is the average number of bad apples encountered in 3600 seconds, and there are 360 ten-second long intervals in this 3600 seconds, the probability of encountering a bad apple in any one of the 10 second intervals is (λ/360).
As expected, this is a much smaller probability given the much smaller time slot.
By setting the number of inspections n to 360, and p = (λ/360), we can rewrite the Binomial distribution as follows:


Let’s take it up a notch. What if (heaven forbid) you are replaced by a robotic inspector that can inspect 1 apple a second i.e. 3600 apples an hour? The probability of finding a bad apple in any one of the 3600 seconds that make up the hour becomes an even rarer event. So with number of inspections n = 3600, and p = (λ/3600) the Binomial distribution’s PMF can be written as:

Going all the way
Let us bring this line of thinking to a conclusion. The robotic inspector version 2.0 has been released. Version 2.0 can inspect apples continuously, i.e. no matter what speed they come down the conveyor belt, the inspector won’t miss any apple. Thus for Version 2.0, the number of inspections n in one hour tends to infinity, and the Binomial distribution finally tends to the Poisson distribution:
Solving the limit to show how the Binomial distribution converges to the Poisson’s PMF formula involves a set of simple math steps that I won’t bore you with.
What is important for us to recollect is how we got to this point in our train of thought about the Binomial distribution.
The following set of plots show how the Binomial distribution’s PMF ‘slides’ toward the Poisson distribution’s PMF as n (number of inspections per hour) increases from 60 to ∞. We keep λ fixed at 3 per hour.
The following table contains the probability values for the first 15 values of k in the plots shown above. The last column was generated by simply using the formula for the Poisson distribution’s PMF with λ set to 3, i.e. Poisson(3).
P(k bad apples in 1 hour) as we vary number of inspections per hour n from 60 to infinity. (λ=3)
Notice how similar are the values in the last two columns (red boxed). Also notice how for any given value of k (green box), the probability of getting that value of k gradually tends toward the Poisson(3)’s PMF value in the last column.
So far we have based all our reasoning on an inspection session that lasts for 1 hour. But all of our reasoning works just the same for 1 millisecond, 1 minute, 1 day, indeed for any unit time interval.
Scaling everything to time t…
As a last step, we will relax this unit time constraint by assuming that our robotic inspector will inspect apples during sessions that last for t hours. This generalization will not break our line of reasoning. We will simply multiply λ, which is the average number of bad apples observed per hour, with t, so that (λt) is the average number of bad apples observed in t hours.
Effectively, we are scaling our observation window, and we are scaling all the relevant formulae by t.
So if an average of λt bad apples are expected to be seen during time t, and the apple inspector can inspect n apples in time t, the probability of seeing a bad apple in any one of those n inspections is (λt/n). i.e. probability p = (λt/n). Therefore the probability of observing k bad apples in time t is given by the Binomial distribution:
Probability of running into k bad apples in t hours of testing
Enter once again, the hyper-efficient robotic inspector who can sample apples continuously. As the number of inspections n, during time t, tends to infinity, the Binomial distribution morphs into the Poisson distribution:
And this is of course the formula that we wanted to get an insight into!

