---
layout: maths
name: Non parametric tests
category: Inferential statistics
---

Tests are *non-parametric* if we do not need to know any parameter of the sample law (e.g. $\mu$, $\sigma$) to perform the test.

Example 1 (**Kolmogorov-Smirnov** test)}: 

- Test whether a sample follow a known law

$F$ is the cumulative ditribution function and $\widehat{F_n}$ its empirical estimation.

The statistic test is $\widehat{F_n}(x) - F(x)$.

We have,

$$\sqrt{n} \underset{1 \leq i \leq k}{\operatorname{max}}|\widehat{F_n}(x_i) - F(x_i)| \underset{n \rightarrow + \infty}{\rightarrow} \underset{0 \leq i \leq k}{\operatorname{max}}|W_i|$$

where $W_i$ is a *Brownian motion* or *Wiener process*.

We also have,

$$\sqrt{n} \underset{0 \leq x \leq 1}{\operatorname{max}}|\widehat{F_n}(x) -x)| \underset{n \rightarrow + \infty}{\rightarrow} \underset{0 \leq x \leq 1}{\operatorname{max}}|B(x)|$$

where $B$ is a *Brownian bridge*.

<a class="cleanLinkSource" href="http://www.math.utah.edu/~davar/ps-pdf-files/Kolmogorov-Smirnov.pdf">Proofs (Empirical-Process Theory)</a>

A Brownian bridge has the following property:

$$\mathbb{P}(\underset{t \in [0,1]}{\operatorname{sup}}|B_t| \geq b) = 2 \Sigma_{n \geq 1}(-1)^{n-1}e^{-2n^2b^2}$$

This allowed statisticians to draw a quantile table, we can thus easily know the critical region.

- Test whether two samples follow the same law

In that case, the statistic is the distance

$$D_{n,m} = \underset{x}{sup}|\widehat{F}_{1,n}(x)-\widehat{F}_{2,m}(x)|$$

Associated test hypothesis are:

$$\begin{cases}
        \mathcal{H}_0: \widehat{F}_{1,n}(x) = \widehat{F}_{2,m}(x) \\
        \mathcal{H}_1: \widehat{F}_{1,n}(x) \neq \widehat{F}_{2,m}(x)
\end{cases}$$

We reject the null hypothesis for level $\alpha$ if $D_{n,m} > \frac{1}{\sqrt{n}} \sqrt{-ln(\frac{\alpha}{2}) \frac{1 + \frac{n}{m}}{2}}$.