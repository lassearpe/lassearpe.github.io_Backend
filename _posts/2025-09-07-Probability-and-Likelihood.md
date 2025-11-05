---
title: Probability and Likelihood
subtitle: Probability vs likelihood is an important distinction within statistics and probability theory. I found it confusing myself, so i set out to explain it.  
layout: default
date: 2025-09-20
keywords: Probability, Likelihood
published: true
---

# Probability and Likelihhod 

In classicial probability, we consider the **data as variable** and the parameter as fixed.

In likelihood, we consider the data as fixed and the **parameter as variable**.

When we have to model the probability or likelihood of data (plural), we are interested in the conditional probability of each datapoint.

Conditional probability is defined as {% katex %} P(A|B)=\frac{P(A \cap B)}{P(B)}=\frac{P(B|A)P(A)}{P(B)} {% endkatex %}

The numerator defines uses the joint probability of the two events. 

The key idea is, that the probability of multiple events happeing rests on their total conditional probability.

Working with multiple joint probabilities therefore reveal the sequence:

{% katex %}
P(A_3 \cap A_2 \cap A_1)=P(A_3|A_2 \cap A_1) * P(A_2|A_1) * P(A_1) 
{% endkatex %}

When calculating the probability distribution of observed data, we simplify our calculation by assuming all data has been generated independently. 

Assuming independence between two events allows us to calculate their joint probability as {% katex %} P(A \cap B) = (B)*P(A){% endkatex %}

This allows us to simplify the calculation of their conditional probability:

{% katex %} P(A|B)=\frac{P(A \cap B)}{P(B)}=\frac{P(B)P(A)}{P(B)}=P(A)*P(B) {% endkatex %}

which in turn become, because of independence:

P(A_3 \cap A_2 \cap A_1)=P(A_3) * P(A_2) * P(A_1) 

{% katex %}
P(A_1,...,A_n)=\prod_i^n p(x_i)
{% endkatex %}

Here, both the data is treated as unknown, while the underlying unknown parameters are considered fixed. 

In practise, our probability of a certain outcome would be modelled by a chosen parametric probability distribution. 
This could be the **Bernoulli distribution**. It models a series of experiments with binary outcome. It is simple, as it only have one parameter, p. here, our p refers to the expected value, and refer to the probability of success. 

{% katex %}
P(X=1)=\prod_{i=1}^{n} p^{x_i}*(1-p)^{1-x_i}
{% endkatex %}

p is the known probabiliity of the outcome. E.g for a coinflip, P=0.5.

If this is the case, we can stop now and be satisfied.

However, p, and parameterts in general, can also be unknown.

Example of parameters for different distributions.

Bernoulli: p -> probability of succes (= expected value, mean)

Multinoulli: p_i -> probability of success for individual category i (expected value for i, mean for i)

Gaussian: mu and sigma -> the mean and the variance 

##### So what about likelihhod?

But consider the case we recieve some data, but have no idea about the parameters behind the data. This is mostly the case, working with real data. We then want to calculate the parameters **most likely to have generated the data**. 

Now, when we know (or assume) the probability distribution of our data, we can use this to calculate the likelihood of observing the data, based on different parameters of the probability function.  

So when we're interested in the *likelihood* of some parameter theta, we can calculate that as the joint probability of our data, given a fixed parameter theta, which is refered to as the *joint likelihood*.

{% katex %}
L(\theta|x_1,...,x_n)=\prod_i^n p(x_i|\theta)
{% endkatex %}

We can then consider the likelihood distribution as a distribution of the potential parameters, theta. 

Based on this distribution, we can find the parameter values most likely to have generated the data. 

So in essence, we are discovering *based on our gathered data, how likely are different models to have generated this data*

# Bonus: Maximum Likelihood Estimation

In MLE, given observed data, find the model that maximizes the likelihood of the data observed. 

The process is:

Decide on distribution

Calculate likelihhod

Find derivative of the likelihood wrt the paramter(s)

Put equal to 0 and solve for p.

# Bonus: Log likelihhod

The log likelihood function is the likelihood function transformed by the natural log. 

The likelihood function itself can be diffisicult to work with, as we have to calculate the joint distribution of the data and a given parameter, for all relevant parameters. The joint distribution (for independent data) is the product of each probability 

In log Likelihod, we are converting the likelihood function to the log of the likelihhod function. 

We can utilize the rules:

{% katex %} \log{a^b} = b * \log(a) {% endkatex %}

{% katex %} \log{ab}= \log{a}+\log{b} {% endkatex %}

{% katex %} {% endkatex %}



