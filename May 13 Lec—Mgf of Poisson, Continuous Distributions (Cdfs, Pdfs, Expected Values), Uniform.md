Recall that $$m_{X}(t)  = \mathbb{E}(e^{tx})$$
the definition for the moment generating function. If $X$ has a finite support, then the mgf is a finite sum of functions of the form $ke^{rt}$. If $X$ has an infinite and countable support, the sum of $ke^{rt}$ converge to a function with a domain that is restricted depending on the function the series converges to.
We also had $$\frac{d^n}{dt^n}(m_{X}(t))|_{t=0} = \mathbb{E}(x^n) =: \mu_{n}$$
and if $Y = aX + b$ then
$$m_{Y}(t) = e^{bt}m_{X}(at)$$

#### Poisson
Let $X \sim P(\lambda)$.
$$p_{X}(k) = e^{-\lambda} \cdot \frac{\lambda^{k}}{k!} \quad k \in \mathbb{N}$$
$$m_{X}(t) = \mathbb{E}(e^{tx}) = \sum_{ k = 0 } ^{  \infty } e^{tk}e^{-\lambda} \cdot \frac{\lambda^k}{k!}$$
$$=e^{-\lambda} \cdot \sum_{ k = 0 } ^{  \infty } \frac{(e^t\lambda)^k}{k!}$$
$$=e^{-\lambda} \cdot e^{\lambda e^t}$$
The interval of convergence is all $\mathbb{R}$.
So to summarize, $$m_{X}(t)  =e^{\lambda\cdot(e^{t}-1)}$$
>[!e] Examples
>1. $e^{3-2e^t}$ is not a moment generating function because its integral is definitely not 1 (since $e^{3-2e^0} = e > 1$)
>2. $e^{2-2e^t}$ might be a mgf (scribe's note: it is not—just apply the inverse Laplace transform 😅) but it can't be a Poisson
>3. $e^{3e^t-3}$ is the mgf of a Poisson distribution ($\lambda = 3$).


>[!e] Example
>A random variable $X$ is such that $m_{X}(t) = e^{4e^{-2t} + 3t - 4}$ for all $t \in \mathbb{R}$.
>1. Find $\mathbb{E}(X)$ and $V(X)$.
>2. Find $P(X  =-3)$ and $P(X = 0)$.
>
>
>We observe that $m_{X}(t) = e^{3t} \cdot e^{4(e^{-2t} - 1)} = e^{3t}m_{Y}(-2t)$ where $Y \sim P(4)$. We therefore have $X = -2Y + 3$.
>Therefore, $\mathbb{E}(X) = 2\mathbb{E}(Y)+ 3 = -5$, $V(X) = 4V(Y) = 16$.
>$P(X = -3) = P(-2Y + 3 = -3) = P(Y = 3) = e^{-4} \cdot \frac{4^3}{3!}$
>and $P(X = 0) = P(-2Y+3 = 0) = P\left( Y = \frac{3}{2} \right) = 0$ (because the support of $Y$ is over $\mathbb{N}$).
End of this quiz's material and midterm material.

---
#### Cumulative distribution function (cdf)
>[!d] Definition: Cumulative distributive function (cdf)
>Given a random variable $X$, the cdf of $X$ is the function defined as $$F_{X}(x) = P(X \leq x)$$

>[!e] Examples
>Let $X$ be a discrete random variable with
>$p_{X}(-2) = \frac{1}{2}$
>$p_{X}(0) = \frac{1}{3}$
>$p_{X}(1) = \frac{1}{6}$
We therefore have $$F_{X}(x) = \begin{cases}  0 \quad x < -2 \\
-2 \quad -2 \leq x < 0 \\
\frac{5}{6}\quad 0 \leq  x < 1 \\
 1 \quad x \geq 1 \end{cases}$$
This is a step function:![[desmos-graph.png]]
(I'm sorry for not being able to show the discontinuity points)

>[!r] Remark
>If $X$ is a discrete random variable, $F_{X}$ is:
>1. nondecreasing
>2. a step function
>3. right continuous
>4. $\lim_{ x \to \infty }F_{X}(x) = 1$, $\lim_{ x \to -\infty }F_{X}(x) = 0$

Of course, there are cumulative density functions that satisfy all the above except that they are not step functions and they are continuous (these are the cdfs of continuous random variables, which we'll talk about below), and there are cdfs that satisfy the above properties except they are not step functions and are not continuous (this you will need Analysis 2 for).

>[!d] Definition: 
>A function $F: \mathbb{R} \to [0,1]$
>such that
>1. $\lim_{ x \to -\infty }F(x) = 0$ and $\lim_{ x \to \infty }F(x) = 1$
>2. $F$ is nondecreasing
>3. $F$ is continuous

>[!e] Examples
> The function $F(x) = \frac{1}{\pi}\tan ^{-1}(x) + \frac{1}{2}$ is the cdf of the so-called Cauchy distribution. ![[desmos-graph-2.png]]
> Taking its derivative, we have $F'(x) = \frac{1}{\pi} \cdot \frac{1}{1+ x^2}$

>[!t] Fact
>A nondecreasing continuous function is differentiable almost everywhere.
>>[!p] Proof
>>(I shall do my best to prove that, if only for my own practice to get ready for analysis 3)

This means taht if $F_{X}$ is a cdf of a continuous random variable, then $f_{X}(x) := \frac{d}{dx} (F_{X}(x))$ exists.
Properties of $f_{X}$:
1. By Darboux's theorem, $f_{X}(x) \geq 0$
2. $\int_{-\infty}^{\infty} f_{X}(x) \, dx = \lim_{ x \to \infty }F_{X}(x) - \lim_{ x \to -\infty }F_{X}(x) = 1$ (challenge: prove that rigorously from an analysis viewpoint)

>[!d] Definition
>A function $f: \mathbb{R} \to \mathbb{R}$ such that
>1. $f(x) \geq 0, \forall x$
>2. $\int_{-\infty}^{\infty} f(x) \, dx = 1$
>is called a **probability density function (pdf)** of a continuous random variable $X$. Moreover, if $F_{X}$ is the cdf of $X$, we have
> $$F_{X}'(x) = f(x)$$
> and $$F_{X}(x) = \int_{-\infty}^{x} f(t) \, dt $$


>[!e] Example
>Find $c$ such that $$f(x) = \begin{cases}  cxe^{-x} \quad x > 0 \\
0 \quad \text{otherwise}  \end{cases}$$
is a pdf.
<br>
We observe that $(0, \infty)$ is the support of $f$.
(We call $xe^{-x}$ the *normalizing constant* and $c$ the *normalizing constant.*)
To satisfy the definition of a pdf, we need to have $$\int_{-\infty}^{\infty} f(x) \, dx =\int_{0}^{\infty} cxe^{-x} \, dx =1$$
We know that $\int_{0}^{\infty} xe^{-x} \, dx$ converges because $| xe^{-x} | = | xe^{-\frac{x}{2}}e^{-\frac{x}{2}} |$ which is eventually $< | e^{-\frac{x}{2}} |$. This justifies an attempt to calculate the integral.
$$\int_{0}^{\infty} xe^{-x} \, dx = -xe^{-x}|_{0}^\infty  +\int_{0}^{\infty} e^{-x} \, dx $$
$$=(\lim_{ b \to \infty } -xe^{-x}) - 0 + \lim_{ b \to \infty } -e^{-x} + 1$$
$$=1$$
So $$\int_{0}^{\infty} cxe^{-x} \, dx  = c\int_{0}^{\infty} xe^{-x} \, dx=1$$
implies $c = 1$.
We also can find the cdf:
$$F_{X}(x) = \int_{-\infty}^{x} f(t) \, dt $$
$$=\begin{cases}  0 \quad \quad\quad\quad\quad x < 0 \\ \int_{0}^{x} f(t) \, dt \quad x > 0  \end{cases}$$
and we can readily compute to see that $\int_{0}^{x} f(t) \, dt = -xe^{-x} + (1-e^{-x})$

#### Expected value
>[!d] Definition: Expected value of a continuous random variable
Let $f_{X}$ be the pdf of a random variable $X$ and $G: \mathbb{R}\to \mathbb{R}$ be a function.
Along the same gusto as we have $\mathbb{E}(G(x))$ for a probability function of a discrete random variable, we define
$$\mathbb{E}(G(x)) = \int_{-\infty}^{\infty} G(x)f_{X}(x) \, dx $$
provided that the improper integral converges.

>[!t] Properties of the expected value
> 1. If $G(x) = C \in \mathbb{R}$ (a constant) then $\mathbb{E}(G(x)) = C$.
> 2. For any constant $\alpha \in \mathbb{R}$, we have $\mathbb{E}(\alpha G(x)) = \alpha \mathbb{E}(G(x))$.
> 3. $\mathbb{E}(G_{1}(x) + G_{2}(x)) = \mathbb{E}(G_{1}(x)) + \mathbb{E}(G_{2}(x))$


>[!e] Examples
>Consider the pdf of the Cauchy distribution, which is $$f_{X}(x) = \frac{1}{\pi} \frac{1}{1+x^2}$$
> Does $\mathbb{E}(X) = \frac{1}{\pi} \int_{-\infty}^{\infty} \frac{x}{1+x^2} \, dx$ exists?
> You might think that $\frac{x}{1+x}$ is odd (this is right) and the integral of an odd function on a symmetric interval is 0 (also a correct fact). **However,** $(-\infty, \infty)$ is not an interval! We need to check $\int_{c}^{\infty} \frac{x}{1+x^2} \, dx$ (and $\int_{-\infty}^{c} \frac{x}{1+x^2}  \, dx$) for arbitrary $c \in \mathbb{R}$ to see if the integrals converge. They do not (by comparison to $\frac{1}{x}$), so $\mathbb{E}(X)$ is not defined.


>[!e] Another more well-behaved example
>![[desmos-graph-3.png]]
>Let $f_{X}$ be defined as in the above graph and let it be the pdf of a continuous random variable $X$. Does $\mathbb{E}(X)$ exist? If so, what is it?
> $$\mathbb{E}(X) = \int_{-\infty}^{\infty} xf_{X}(x) \, dx $$
> From the graph, we have $$f_{X}(x) = \begin{cases}  x \quad 0 < x < 1 \\ 2-x \quad 1 < x < 2 \\
0 \quad \text{otherwise}  \end{cases}$$
so $$\int_{-\infty}^{\infty} xf_{X}(x) \, dx = \int_{0}^{2} xf_{X}(x) \, dx  $$
which certainly exists because it's a proper integral.
$$\int_{0}^{2} xf_{X}(x) \, dx = \int_{0}^{1} xf_{X}(x) \, dx  + \int_{1}^{2} xf_{X}(x) \, dx$$



---
#### Uniform distributions
>[!d] Definition: Uniform distribution
Let $a < b$. A continuous random variable $X$ is said to have a uniform distribution on $(a,b)$ (written $X \sim \text{Uniform}(a,b)$ if its pdf is $$f_{X}(x) = \begin{cases}  \frac{1}{b-a } \quad x \in (a,b) \\ 0 \quad \text{otherwise}  \end{cases}$$
![[desmos-graph-4.png]]
(an example of such a pdf with $a = 3, b = 5$)
>>[!a] Scribe's aside
>>Again, for brevity's sake I will write $X \sim U(3, 5)$.

We observe that $$F_{X}(x) = \begin{cases}  0 \quad \quad \quad \quad \quad x \leq a \\
\frac{1}{b-a}(x-a) \quad a \leq x \leq b \\
1 \quad \quad \quad \quad \quad x \geq b  \end{cases}$$
![[desmos-graph-5.png]]

>[!e] Example
>Continuing with the example above ($X \sim U(3, 5)$). Compute $P(2 \leq X \leq 4)$.
><br>
>$P(2 \leq X \leq 4) = P(2 \leq X \leq 3) + P(3 < X \leq 4)$
>$= 0 + \int_{3}^{4}  (b-a)\, dx$
>$=\int_{3}^{4} \frac{1}{2} \, dx = \frac{1}{2}$

More generally, for any $c, d \in \mathbb{R}$, and $X \sim U(a,b)$, we have
$$P(c \leq X \leq d) = \frac{1}{b-a} \cdot \text{length}([c,d] \cap [a,b])$$
$$=\max\{0,[\min(b,d) - \max(a,c)]\} \cdot \frac{1}{b-a}$$

Upshot for tomorrow: For two continuous random variables $X, Y$ where $Y = \alpha X +\beta$ for $\alpha, \beta \in \mathbb{R}$, we have $$f_{Y}(t) = \frac{1}{|\alpha|} f_{X}\left( \frac{t-\beta}{\alpha} \right)$$
