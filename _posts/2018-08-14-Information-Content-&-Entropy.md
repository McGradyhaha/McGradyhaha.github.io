```
layout: post
author: WhyK
comments: true
date: 2018-08-14 9:05:32+10:00
tags: [machine learning]
title: Information Content & Entropy
```
<script type="text/javascript" src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML"></script>

<hr style="filter: alpha(opacity=100,finishopacity=0,style=3);" />
### Information Content & Entropy

How can we measure information content?:

* Information content of an outcome must depend on its probability
* Information content of a random variable must depend on its probability distribution
  
Entropy of an outcome x:

\\[ h(x) = {log_{2}\frac{1}{p(x)}} \\]
* Choice of logarithm basis is arbitrary
* If we use log2 we measure information in bits

### Entropy of a Random Variable
Let X be a discrete r.v. with values drawn from alphabet X from a total number of states |X |.

If we want to transmit the value of X, the average amount of information is given by:
\\[ h(x) = \sum_{x}^{}p(x){log_{2}\frac{1}{p(x)}} \\]
Note that we can also write:

\\[ h(x) = -\sum_{x}^{}p(x){log_{2}{p(x)}} \\]
The expectation of the entropy of each outcome wrt p(x)
We call this the entropy of the r.v. X <span style="color:red">(Note dependency on distribution)</span>

Example 1: Bernoulli Distribution

Let X ∈ {0, 1} with X ∼ Bern(X|θ) and θ = p(X = 1) :

