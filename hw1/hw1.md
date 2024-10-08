# Task 1

### Part A
Suppose $\theta \ in [0,1]$ is flag of oracle and $x_i \in [0,1]$ is outcome of $i$ trial. Hence probability of task statement for ordinary person can be rewritten as:
$$
    P(x_1=1,\dots,x_10=1 | \theta =0 ) = P(x_1 =1 | \theta=0) \dots  P(x_10 =1 | \theta=0) P(\theta =0) = 10^{-3} 0.9^(10) 
$$
Factorization comes from fact that trials are independent. Likewise, for oracle:
$$
    P(x_1=1,\dots,x_10=1 | \theta =1 ) =  (1 - 10^{-3}) 0.5^(10)
$$
Using bayesian formula, we will achieve:
$$
    P(\theta=1| x_1=1,\dots,x_10=1) = \frac{P(x_1=1,\dots,x_10=1 | \theta =1 )}{P(x_1=1,\dots,x_10=1 | \theta =1 ) + P(x_1=1,\dots,x_10=1 | \theta =0 )}
$$
### Part B

Graph is provided in [Notebook](./task1.ipynb)

# Task 2

Quantile estimation of large population (k >>1) can be assymptoticall estimated with normal distribution with known:
$$
    F^{-1}(p), \frac{p(1-p)}{n[f(F^{-1}(p))]^2}
$$

. For further clarification please follow [Wiki](https://en.wikipedia.org/wiki/Order_statistic#Large%20sample%20sizes)

# Task 3

Without reasonable approximation statistic:

$$
    T(\mathbf{Z}) = \frac{1}{n} \sum_{i=1}^n x_i y_i
$$

is seamed hard to approximate (look for SOTA method [here](https://www1.up.poznan.pl/cb48/prezentacje/Oliveira.pdf)). Therefore, use large scale approximation.

First, we will start with transform to indepent variables using cholesky decomposition (look [through](https://www2.stat.duke.edu/courses/Spring12/sta104.1/Lectures/Lec22.pdf)):
$$
    X= Z_1 \\
    Y = \rho Z_1 + \sqrt{1-\rho^2} Z_2
$$,
with $Z_1, Z_2 \sim \mathcal{N}(0,1)$ 
Therefore expected value is 
$$
    E(XY) = \rho E(Z_1^2) + \sqrt{1-\rho^2} E(Z_1) E(Z_2) = \rho
$$
Yield second order using second order moment:
$$
    E((XY)^2) = E((\rho Z_1^2 + \sqrt{1-\rho^2} Z_1 Z_2)^2) = 
    E(\rho^2 Z_1^4 + 2 \rho \sqrt{1-\rho^2} Z_1^3 Z_2 + (1-\rho) Z_1^2 Z_2^2) = 3 \rho^2 + 1-\rho  
$$

Therefore, dispersion:
$$
    D(XY) = 1 - \rho + 2 \rho^2
$$

Using central limit theorem:
$$
    \sqrt{N} (T(Z) - \rho) = N(0,1 - \rho + 2 \rho^2)
$$

Follow Part A of notebook for [graph](./task3.ipynb#PartA) 


## Task 4

Correlation coefficients even for bivariate normal distribution has complex analytical [form](https://en.wikipedia.org/wiki/Pearson_correlation_coefficient#Using_the_exact_distribution). Therefore, we'll use central limit theorem for sake of simplicity:
$$
    \sqrt{N}(\rho) \sim \ma
$$


