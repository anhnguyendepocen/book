## Frequentist vs. Bayesian Inference

### Frequentist vs. Bayesian Inference

In this section, we will solve a simple inference problem using both frequentist and Bayesian approaches. Then we will compare our results based on decisions based on the two methods, to see whether we get the same answer or not. If we do not, we will discuss why that happens.

\BeginKnitrBlock{example}<div class="example"><span class="example" id="exm:MM"><strong>(\#exm:MM) </strong></span>We have a population of M&M's, and in this population the percentage of yellow M&M's is either 10% or 20%. You've been hired as a statistical consultant to decide whether the true percentage of yellow M&M's is 10% or 20%. 

Payoffs/losses: You are being asked to make a decision, and there are associated payoff/losses that you should consider. If you make the correct decision, your boss gives you a bonus. On the other hand, if you make the wrong decision, you lose your job.

Data: You can "buy" a random sample from the population -- You pay $200 for each M&M, and you must buy in $1,000 increments (5 M&Ms at a time). You have a total of $4,000 to spend, i.e., you may buy 5, 10, 15, or 20 M&Ms.

Remark: Remember that the cost of making a wrong decision is high, so you want to be fairly confident of your decision. At the same time, though, data collection is also costly, so you don't want to pay for a sample larger than you need. If you believe that you could actually make a correct decision using a smaller sample size, you might choose to do so and save money and resources.</div>\EndKnitrBlock{example}

Let's start with the frequentist inference.

* Hypothesis: $H_0$ is 10% yellow M&Ms, and $H_A$ is >10% yellow M&Ms.

* Significance level: $\alpha = 0.05$.

* Sample: red, green, **yellow**, blue, orange

* Observed data: $k=1, n=5$

* P-value: $P(k \geq 1 | n=5, p=0.10) = 1 - P(k=0 | n=5, p=0.10) = 1 - 0.90^5 \approx 0.41$

Note that the p-value is the probability of observed or more extreme outcome given that the null hypothesis is true.

Therefore, we fail to reject $H_0$ and conclude that the data do not provide convincing evidence that the proportion of yellow M&M's is greater than 10%. This means that if we had to pick between 10% and 20% for the proportion of M&M's, even though this hypothesis testing procedure does not actually confirm the null hypothesis, we would likely stick with 10% since we couldn't find evidence that the proportion of yellow M&M's is greater than 10%.

The Bayesian inference works differently as below.

* Hypotheses: $H_1$ is 10% yellow M&Ms, and $H_2$ is 20% yellow M&Ms.

* Prior: $P(H_1) = P(H_2) = 0.5$

* Sample: red, green, **yellow**, blue, orange

* Observed data: $k=1, n=5$

* Likelihood:

$$\begin{aligned}
P(k=1 | H_1) &= \left( \begin{array}{c} 5 \\ 1 \end{array} \right) \times 0.10 \times 0.90^4 \approx 0.33 \\
P(k=1 | H_2) &= \left( \begin{array}{c} 5 \\ 1 \end{array} \right) \times 0.20 \times 0.80^4 \approx 0.41
\end{aligned}$$

* Posterior

$$\begin{aligned}
P(H_1 | k=1) &= \frac{P(H_1)P(k=1 | H_1)}{P(k=1)} = \frac{0.5 \times 0.33}{0.5 \times 0.33 + 0.5 \times 0.41} \approx 0.45 \\
P(H_2 | k=1) &= 1 - 0.45 = 0.55
\end{aligned}$$

The posterior probabilities of whether $H_1$ or $H_2$ is correct are close to each other. As a result, with equal priors and a low sample size, it is difficult to make a decision with a strong confidence, given the observed data. However, $H_2$ has a higher posterior probability than $H_1$, so if we had to make a decision at this point, we should pick $H_2$, i.e., the proportion of yellow M&Ms is 20%. Note that this decision contradicts with the decision based on the frequentist approach. 

Table \@ref(tab:freq-vs-bayes) summarizes what the results would look like if we had chosen larger sample sizes. Under each of these scenarios, the frequentist method yields a higher p-value than our significance level, so we would fail to reject the null hypothesis with any of these samples. On the other hand, the Bayesian method always yields a higher posterior for the second model where $p$ is equal to 0.20. So the decisions that we would make are contradictory to each other.


Table: (\#tab:freq-vs-bayes)Frequentist and Bayesian probabilities for larger sample sizes

                Frequentist                 Bayesian H_1           Bayesian H_2         
--------------  --------------------------  ---------------------  ---------------------
Observed Data   P(k or more | 10% yellow)   P(10% yellow | n, k)   P(20% yellow | n, k) 
n = 5, k = 1    0.41                        0.45                   0.55                 
n = 10, k = 2   0.26                        0.39                   0.61                 
n = 15, k = 3   0.18                        0.34                   0.66                 
n = 20, k = 4   0.13                        0.29                   0.71                 

However, if we had set up our framework differently in the frequentist method and set our null hypothesis to be $p = 0.20$ and our alternative to be $p < 0.20$, we would obtain different results. This shows that **the frequentist method is highly sensitive to the null hypothesis**, while in the Bayesian method, our results would be the same regardless of which order we evaluate our models. 
