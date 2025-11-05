---
title: Intuition of the Markov Inequality
subtitle: In short, we have to keep the expectation intact. 
layout: default
date: 2025-10-06
keywords: machine-learning
published: true
---

Markovs inequality is a worst case. It is an upper bound on the probability of {% katex %} X \ge a {% endkatex %}.

It is based on the known expectation of a distribution. 

In other words, what are the greatest area of {% katex %} X \ge a {% endkatex %} we can allow, that *we know* will not increase this mean. Being a very conservative estimate, we can understand how dividing {% katex %} \frac{E[X]}{a} {% endkatex %} is not going to increase the mean. 

Therefore it is also a very loose estimate; it is obviously not wrong, but it is not very informative.

The expectead value must at least account for the value beyond a. Every X that lies beyond a, must contribute with at least {% katex %} a {% endkatex %} to the mean. The total mean must therefore be at least a times the probability of the region {% katex %} X \ge a {% endkatex %}.

If we consider the Law of Total Expectation:
In the worst case, where the probability of the area {% katex %} X < a {% endkatex %} is 0; then the area {% katex %} X \ge a {% endkatex %} must be concentrated at {% katex %} a {% endkatex %}, and the probability would therefore be upper bounded by {% katex %} \le \frac{E[X]}{a} {% endkatex %} in order to not increase {% katex %} E[X] {% endkatex %}.

We consider the worst case where the expectation is entirely driven by the second term; the values exactly at {% katex %} a {% endkatex %}.

This is the worst case, as we have found the minimum expected value; the terms below a are 0 (and dissapears), while the term above or equal to a, all becomes exactly a. 

This gives us 

{% katex %} E[x] \ge 0*Pr(X < a) + a * Pr(x \ge a) {% endkatex %}

{% katex %} E[x]/a \ge Pr(x \ge a) {% endkatex %}
