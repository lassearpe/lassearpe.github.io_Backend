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

In practise, our P would be represented by a chosen parametric probability distribution. 
This could be the **Bernoulli distribution**. It models a series of experiments with binary outcome. 

{% katex %}
P(X=1)=\prod_{i=1}^{n} P^{x_i}*(1-P)^{1-x_i}
{% endkatex %}

P is the known probabiliity of the outcome. E.g for a coinflip, P=0.5.

But P can also be unknow.

##### So what about likelihhod?

Now, when we know (or assume) the probability distribution of our data, we can use this to calculate the likelihood of observing the data, based on different parameters of the probability function.  

So when we're interested in the *likelihood* of some parameter theta, we can calculate that as the joint probability of our data, given a fixed parameter theta, which is refered to as the *joint likelihood*.

{% katex %}
L(\theta|x_1,...,x_n)=\prod_i^n p(x_i|\theta)
{% endkatex %}

We are can then consider the likelihood distribution as a distribution of the potential parameters, theta. 

Interesting usecases are finding the parameters, that maximizes this likelihood. This is parameters we can wish to model our original probability distribution after. 



### What is probability? 

Probability refers to an *anticipation* of the probability of an event.

Consider that we have a model, consisting of parameters such as the mean and variance. 

This model can provide us with a probability measure of an event, e.g. based on the parameters provided, the probability of the event happening. 

This model can be constructed with our knowledge about the world; e.g equal probability of heads and tails in a fair coin, equal probabillity of each side sides in a fair die. 

One can see this as going from the model towards the data, e.g in a forward direction. 

{% katex %} 
P(D)
{% endkatex %}

or
{% katex %} 
P(D|M)
{% endkatex %}

<canvas id="gaussianChart" width="600" height="300"></canvas>

<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>

<script>
  // Gaussian (normal) distribution function
  function gaussian(x, mean, stdDev) {
    return (1 / (stdDev * Math.sqrt(2 * Math.PI))) * Math.exp(-0.5 * ((x - mean) / stdDev) ** 2);
  }

  // Generate x values from -4 to 4
  const xValues = [];
  const yValues = [];
  const mean = 0;
  const stdDev = 1;

  for(let x = -4; x <= 4; x += 0.1) {
    xValues.push(x.toFixed(2));
    yValues.push(gaussian(x, mean, stdDev));
  }

  const ctx = document.getElementById('gaussianChart').getContext('2d');

  const gaussianChart = new Chart(ctx, {
    type: 'line',
    data: {
      labels: xValues,
      datasets: [{
        label: 'Normal Distribution',
        data: yValues,
        borderColor: 'rgba(75, 192, 192, 1)',
        backgroundColor: 'rgba(75, 192, 192, 0.2)',
        fill: true,
        tension: 0.3,  // smooth curve
      }]
    },
    options: {
      scales: {
        x: {
          title: {
            display: true,
            text: 'x'
          }
        },
        y: {
          title: {
            display: true,
            text: 'Probability Density'
          },
          beginAtZero: true
        }
      }
    }
  });
</script>

# What is likelihood? 

Likelihood provides us with the tools to judge the quality of the model. A model is a set of parameters, an example could be the gaussian distribution {% katex %} N(\mu, \omega^2) {% endkatex %}.

**In essence, the likelihood is how likely the data is to have been generated by a given model (set of parameters)**.  

So, the likelihood of a set of parameters {% katex %} \theta {% endkatex %} is the result of the **joint likelihood** of the observed data, given this set of parameters. 

{% katex %}
L(\theta|x)=P(x_1,x_2,...,x_n|\theta)
{% endkatex %}

So, a likelihood function (or distribution) shows the distribution of likelihoods, given our fixed observed data across different possible parameter values.

The x-axis represent our possible set of parameters (models) ({% katex %} \theta {% endkatex %}), and y-axis our likelihood, {% katex %} L(\theta) {% endkatex %}.

So in essence, we are discovering *based on our gathered data, how likely are different models to have generated this data*.

# Bonus: Log likelihhod

The log likelihood function is the likelihood function transformed by the natural log. 

The likelihood function itself can be diffisicult to work with, as we have to calculate the joint distribution of the data and a given parameter, for all relevant parameters. The joint distribution (for independent data) is the product of each probability 

In log Likelihod, we are converting the likelihood function to the log of the likelihhod function. 

We can utilize the rules:

{% katex %} \log{a^b} = b * \log(a) {% endkatex %}

{% katex %} \log{ab}= \log{a}+\log{b} {% endkatex %}

{% katex %} {% endkatex %}

# Bonus: Maximum Likelihood Estimation

In MLE, given observed data, find the model that maximizes the likelihood of the data observed. 

