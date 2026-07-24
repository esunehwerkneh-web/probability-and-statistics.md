# probability-and-statistics.md
# Math  1 — Probability & Statistics

**Task Type:** AI Model Math-Evaluation (Problem + Gold-Standard Solution + Grading Notes)

Problem Statement

A construction company is monitoring the quality of a batch of 500 concrete cube samples from a project site. Historically, 4% of cubes fail to meet the required 28-day compressive strength. A quality control engineer selects a random sample of 40 cubes for testing.

1. **(a)** Using the binomial distribution, calculate the probability that exactly 2 of the 40 sampled cubes fail the strength test.
2. **(b)** Using the Poisson approximation to the binomial (appropriate here since $n$ is large and $p$ is small), estimate the same probability and compare it to the exact binomial answer.
3. **(c)** State one condition under which the Poisson approximation would NOT be considered appropriate.


## Gold-Standard Reference Solution

Let $X = \text{number of cubes (out of 40) that fail the strength test}$.  
$X \sim \text{Binomial}(n = 40, p = 0.04)$

### Part (a): Exact Binomial Calculation

$$P(X = 2) = \binom{40}{2} \times (0.04)^2 \times (0.96)^{38}$$

* $\binom{40}{2} = \frac{40 \times 39}{2} = 780$
* $(0.04)^2 = 0.0016$
* $(0.96)^{38} \approx 0.2120$

$$P(X = 2) = 780 \times 0.0016 \times 0.2120 \approx 0.2646$$

> **Result:** $P(X = 2) \approx 0.265 \quad (26.5\%)$

### Part (b): Poisson Approximation

$$\lambda = n \times p = 40 \times 0.04 = 1.6$$

$$P(X = 2) = \frac{\lambda^2 \times e^{-\lambda}}{2!} = \frac{1.6^2 \times e^{-1.6}}{2}$$

* $1.6^2 = 2.56$
* $e^{-1.6} \approx 0.2019$

$$P(X = 2) = \frac{2.56 \times 0.2019}{2} \approx 0.2584$$

> **Result:** $P(X = 2) \approx 0.258 \quad (25.8\%)$ under the Poisson approximation.

**Comparison:** The exact binomial value ($\approx 26.5\%$) and the Poisson approximation ($\approx 25.8\%$) agree closely (within $0.7$ percentage points). This aligns with the rule of thumb that the Poisson approximation is reliable when $n \ge 20$ and $p \le 0.05$.

### Part (c): Condition Where Poisson Approximation Breaks Down

The Poisson approximation becomes unreliable when $p$ is not small relative to $n$. For example, if the defect rate were $20\%$ instead of $4\%$, $np$ would no longer approximate a rare-event process well, and the binomial variance ($np(1-p)$) would diverge noticeably from the Poisson variance ($\lambda = np$).



## Evaluation & Grading Notes (AI-Response Review Format)

* [ ] Verify that the model identifies this as a binomial setup prior to approximating.
* [ ] **Common Error:** Applying the Poisson formula with $\lambda = n \cdot p$ but forgetting $k!$ in the denominator ($\frac{\lambda^k}{k!}$).
* [ ] **Common Error:** Computing $(0.96)^{38}$ inaccurately by rounding early. Flag deviations from $\approx 0.265$ exceeding $\pm 0.01$ without justification.
* [ ] **Credit Requirement:** Must include a numerical comparison between parts (a) and (b), plus a substantive answer to part (c) referencing the $n/p$ relationship.