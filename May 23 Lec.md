A quick recap of the dot product
>[!t] Dot product properties
>(Let $V$ be a (finite?) dimensional vector space over $\mathbb{R}$. Then the inner product, also called the *dot product*, $\cdot: V \times V \to \mathbb{R}$ is a function such that:)
>1. $\vec{u}\cdot(\vec{v_{1}}+\vec{v_{2}}) = \vec{u}\cdot\vec{v_{1}}+\vec{u}\cdot\vec{v_{2}}$
>2. $\vec{u} \cdot (\alpha \vec{v}) = \alpha \vec{u} \cdot  \vec{v}$
>3. $\vec{u} \cdot \vec{v} = \vec{v} \cdot \vec{u}$
>4. If $V = \mathbb{R}^n$ for some $n \in \mathbb{N}$, then $\vec{u} \cdot \vec{v} = \| \vec{u} \| \| \vec{v} \|  \cos\alpha$ where $\alpha$ is the angle between $\vec{u}$ and $\vec{v}$.

>[!d] Definition: 
>Let $X ,Y$ be two random variables. The covariance between $X$ and $Y$ is defined as $$Cov(X, Y) = \mathbb{E}(XY) - \mathbb{E}(X)\mathbb{E}(Y)$$
>>[!r] Remark
>>If $\mu_{X} = \mathbb{E}(X)$, $\mu_{Y} = \mathbb{E}(Y)$, then $$Cov(X,Y) = \mathbb{E}[(X - \mu_{X})(Y - \mu_{Y})]$$
>


>[!t] Properties of covariance
>1. $Cov(X,X) = V(X)$
>2. $Cov(X, Y) = Cov(Y,X)$
>3. $Cov(X, Y_{1} + Y_{2}) = Cov(X, Y_{1}) + Cov(X, Y_{2})$
>4. $Cov(X, \alpha Y) = \alpha Cov(X, Y)$
>
>These properties establish $Cov$ as a dot product on the vector space of random variables.

$y$-value\ $x$-value | $-1$ | $0$ | $1$ | $p_{Y}(y)$
-- | -- | -- | --| --
$0$ | $\frac{1}{4}$ | $\frac{1}{6}$ | $\frac{1}{12}$ | $\frac{1}{2}$
$1$ | $\frac{1}{4}$ | $0$ | $\frac{1}{4}$ | $\frac{1}{2}$
$p_{X}(x)$ | $\frac{1}{2}$ | $\frac{1}{6}$
>[!e] Examples
>We calculated last time that $\mathbb{E}(XY) = 0$. Furthermore, $\mathbb{E}(X) = -\frac{1}{10}$ and $\mathbb{E}(Y) = \frac{1}{2}$. So $Cov(X , Y) = 0 - \left( -\frac{1}{6} \cdot \frac{1}{2} \right)= \frac{1}{12}$.

>[!e] A continuous example
>Again the function $$f(x,y) = \begin{cases}  6x \quad 0 < x < y < 1 \\ 0 \quad \text{otherwise}  \end{cases}$$
>![[desmos-graph-8.png]]
>We have $$\mathbb{E}(XY) = \iint_{\mathbb{R}^2}xy f(x,y)\;dA$$
> $$=\int_{0}^{1} \int_{0}^{y} xy \cdot 6x \, dx  \, dy $$
> $$\int_{0}^{1} y\int_{0}^{y} 6x^2 \, dx  \, dy $$
> $$\int_{0}^{1} y \cdot 2y^3 \, dy =\frac{2}{5}$$
We computed before that $X \sim Beta(2,2)$ and $Y \sim Beta(3,1)$, so $\mathbb{E}(X) = \frac{1}{2}, \mathbb{E}(Y) = \frac{3}{4}$. Therefore $Cov(X, Y) = \frac{1}{40}$.


Recall the famous Cauchy-Schwartz inequality:
$$| \vec{u} \cdot  \vec{v} |  = \| \vec{u} \|  \| \vec{v} \| $$
with equality if and only if $\vec{u} = \pm \vec{v}$.

>[!t] Proposition
> $$| Cov(X, Y) |  \leq \sqrt{ V(X) } \cdot \sqrt{ V(Y) }$$
> >[!p] Proof
> >Follows from the Cauchy-Schwartz inequality.

From here we have $$-1 \leq \frac{Cov(X, Y)}{\sqrt{ V(X) } \sqrt{ V(Y) }}\leq 1$$
>[!d] Definition: Correlation coefficient
> $\rho(x,y)$ is the correlation coefficient between $X$ and $Y$.
> It has the meaning of being a measure of the linear association between $X$ and $Y$.

>[!p] Properties of the correlation coefficient
>1. $$-1 \leq \rho(X, Y)\leq 1$$
>2. if $\rho(X,Y) = 1$, then $Y = \alpha X + b$ where $\alpha > 0$
>3. if $\rho(X, Y) = -1$, then $Y = \alpha X + b$ where $\alpha < 0$.

>[!e] Example
>Suppose $V(X) = 2$, $V(Y) = 3$, $Cov(X, Y) = -\sqrt{ 6 }$, $\mathbb{E}(X) = 1$, $\mathbb{E}(Y)= 3$. What is the relationship between $X$ and $Y$?
>We observe that $\rho (X, Y) =\frac{-\sqrt{ 6 }}{\sqrt{ 6 }} = -1$, so $Y  = \alpha X + b$ where $\alpha < 0$. Since $V(Y) = \alpha^2V(X)$, we deduce $\alpha^2 = \frac{3}{2} \implies \alpha = -\sqrt{ \frac{3}{2} }$, and since $\mathbb{E}(Y) = \alpha\mathbb{E}(X) + b$ we deduce $b = 3 + \sqrt{ \frac{3}{2} }$.

Note that if $Cov(X, Y)$ had been $\sqrt{ 8 }$ in the above example, then that would have been impossible because $\sqrt{ 8 } > \sqrt{ 2 } \cdot \sqrt{ 3 }$ which violates Cauchy-Schwartz.
Also, if $\rho(X, Y)\neq \pm 1$, we have insufficient information.

>[!d] Definition
>$X$ and $Y$ are said to be uncorrelated if $\rho(X, Y) = 0$.

>[!r] Remark
>If $X$ and $Y$ are independent, then $X$ and $Y$ are uncorrelated. But the converse is not true, see the examples below.

>[!e] Example
>
$y$-value\ $x$-value | $-1$ | $0$ | $1$ | $p_{Y}(y)$
-- | -- | -- | --| --
$-1$ | $q$ | $p$ | $q$ | $2q + p$
$0$ | $p$| $0$| $p$ | $2p$
$1$ |$q$| $p$ | $q$ | $2q+p$
$p_{X}(x)$ |  $2q + p$ | $2p$ |  $2q + p$
If $p + q = \frac{1}{4}$ we get a joint probability distribution. $\mathbb{E}(XY) = 0$, and you can verify that $\mathbb{E}(X) =  \mathbb{E}(Y) = 0$. But since the support is not of rectangular type, $X$ and $Y$ are not independent.

>[!t] Proposition
> $V(X+Y) = Cov((X+Y),(X + Y)) =V(X) + V(Y) + 2 Cov(X, Y)$
> more generally, $$V\left( \sum_{ i = 1 } ^{ n } \alpha_{i}X_{i} \right) = \sum_{ i = 1 } ^{ n } \alpha_{i}^2 V(X_{i}) + 2 \sum_{ i < j } \alpha_{i}\alpha_{j}Cov(X_{i}, X_{j}) $$

>[!e] Example
>Suppose $X, Y, W$ are independent, $X \sim N(0,2)$, $Y\sim \chi^2(p=3)$, $W \sim Exponential(3)$.
>Let us calculate $V(2X + 3Y - W)$:
> $$=4V(X) + 9V(Y) + V(W) +\cancel{  12Cov(X, Y) } \cancel{ - 4Cov(X, CW) } \cancel{ -6 Cov(Y, W) }$$



>[!t] Big long formula for taking covariance
> $$Cov\left( \sum_{ i = 1 } ^{ n } \alpha_{i}X_{i}, \sum_{ j = 1 } ^{ m } \beta_{i}Y_{i} \right) = $$

something


---
#### Multinomial distribution
In a binomial distribution, the number of repetitions ($N$) is fixed, each trial is independent, and there are two outcomes (failure and success) with constant probability.
Let $X$ be the number of successes and $Y$ the number of failures. $X \sim B(N, p)$ and $Y \sim B(N, 1-p)$. Furthermore, $Y = N-p$, so $\rho(X, Y) = -1$. Hence $Cov(X, Y) = -\sqrt{ V(X) } \cdot \sqrt{ V(Y) } = -Np(1-p)$
But what if we have more than 2 outcomes?

>[!e] Example
>A fair die is such that 3 faces are labeled a, 2 are labeled b, and 1 is labeled c. Roll the die 10 times. Let $X_{1}$ be the number of A, $X_{2}$ the number of B, $X_{3}$ the number of $C$.
>Taken by themselves, $X_{1} \sim B\left( 10, \frac{1}{2} \right), X_{2} \sim B\left( 10, \frac{1}{3} \right), X_{3} \sim B\left( 10, \frac{1}{6} \right)$.
>We also have $X_{1} + X_{2} + X_{3} = 10$.
>We know that events like $X_{1} = 1, X_{2} = 3, X_{3} = 7$ is impossible because the sum is not $10$.
>Calculating $P(X_{1} = 1, X_{2} = 3, X_{3} = 6)$:
> $$={10 \brack {1,3,6 } } \left( \frac{1}{2} \right)^{1}\left( \frac{1}{3} \right)^{3}\left( \frac{1}{6} \right)^6$$

>[!d] Definition Multinomial distribution
>Assume that a random experiment has outcomes $w_{1}, w_{2}, \dots, w_k$ with constant probability $p_{1}, p_{2}, \dots, p_k$. Repeat the experiment $N$ times, and let $X_{i}$ be the number of times $w_{i}$ occurred. Let the trials be independent. Then $X_{1}, X_{2}, \dots, X_k$ are said to have a (joint) multinomial distribution with parameters $N, p_{1}, p_{2}, \dots, p_k$.

>[!t] Properties of the multinomial distribution
> 1. $X_{i} \sim B(N, p_{i})$ for $i = 1,\dots,k$
> 2. $$P(X_{1} = x_{1}, \dots, X_{k} = x_{k}) = \frac{N!}{x_{1}!x_{2}!\dots x_{k}!}p_{1}^{x_{1}}\dots p_{k}^{x_{k}}$$

>[!e] Example
>Continue the die example above ($N = 10, p_{1} = \frac{1}{2}, p_{2} = \frac{1}{3} , p_{3} = \frac{1}{6}$). Given $X_{3} = 5$, what is the (conditional) distribution of $X_{1}$?
> $$P(X_{1} = x_{1} | X_{3} = 5) = \frac{P(X_{1} = x_{1}, X_{3} = 5)}{P(X_{3} = 5)}$$
> $$= \frac{P(X_{1} = x_{2}, X_{2} = 5-x_{1}, X_{3} = 5)}{P(X_{3} =5)}$$
> $$\frac{\frac{\cancel{ 10! }}{x_{1}!(5-x_{1})!\cancel{ 5! }}\left( \frac{1}{2} \right)^{x_{1}}\left( \frac{1}{3} \right)^{5-x_{1}}\left( \frac{1}{6} \right)^{5}}{\frac{\cancel{ 10!} }{5!\cancel{ 5! }}\left( \frac{5}{6} \right)^5\cancel{ \left( \frac{1}{6} \right)^5} }$$
> $$=\frac{5!}{x_{1}!(5-x_{1})!}\left( \frac{3}{5} \right)^{x_{1}}\left( \frac{2}{5} \right)^{5-x_{1}}$$
> so $X_{1} \sim B\left( 5, \frac{3}{5} \right)$.
> More generally, if $X_{1},X_{2},X_{3}$ have a multinomial distribution with parameters $N, p_{1},p_{2}, p_{3}$, then given $X_{3} = n$ (where $n < N$) we have $X_{1} \sim B\left( N-n, \frac{p_{1}}{1-p_{3}} \right)$ and $X_{2} \sim B\left( N-n, \frac{p_{2}}{1-p_{3}} \right)$, or equivalently $X_{1} \sim B\left( N-n, \frac{p_{1}}{p_{1} + p_{2}} \right)$ and $X_{2} \sim B\left( N-n, \frac{p_{2}}{p_{1}+p_{2}} \right)$
> >[!a] Exercise
> >Prove the above.

>[!t] Proposition
>If $X_{1}, X_{2}, \dots, X_k$ have a (joint) multinomial distribution with parameter $N, p_{1}, p_{2}, \dots, p_k$, then:
>1. $V(x_{i}) = Np_{i}(1-p_{i})$
>2. $Cov(X_{i}, X{j}) = -Np_{i}p_{j}$ if $i \neq j$
>
>>[!p] Proof
>>Left till next time.