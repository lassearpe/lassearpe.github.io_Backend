---
title: Inductive Bias and the Weight Competition
subtitle: In essence, regularization can be viewed as a competition between weights.  
layout: default
date: 2025-10-06
keywords: machine-learning
published: true
---

# Inductive Bias and Weight Competition

In machine learning, we are interested in a low generalization error. The training error can be arbitrarily optimized emperically, hence the problem of empirical risk minimization. 

The interesting thing is how we will inference on unseen data. This is noted as the generalization error. 

To achieve a low generalization error, we are deliberately introducing bias. 

An example of this is the weight penalization through a regularization term. 

When we introduce a regularization term, we are asking our model to *choose* between weights.  Remember, we want our loss to be as close to zero as possible. If we *add* the very same weight back into the model, it forces the algorithm to choose weigts differently. To choose weights within a given budget. 

Each loss point is the result of the sum of our weighted features. This can be for instance be the absolute value (in ridge, L1), or the squared (in LASSO, L2). 

