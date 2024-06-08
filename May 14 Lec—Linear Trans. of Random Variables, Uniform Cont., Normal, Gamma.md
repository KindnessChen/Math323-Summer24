Quiz 2 is tonight/tomorrow morning, on Chapter 3.

Continuing the discussion of uniform distributions:
>[!t] Proposition (linear transformations of random variables)
>If $Y = \alpha X + \beta$, $\alpha \neq 0$, the pdf of $X$ and $Y$ are linked through the equation $$f_{Y}(y) = \frac{1}{| \alpha | }f_{X}\left( \frac{y-\beta}{\alpha} \right)$$
>>[!p] Proof
>>Case 1: $\alpha < 0$. The case $\alpha > 0$ is left as an exercise.
>>We have $$F_{Y}(y) = P(Y \leq y)$$
>> $$=P(\alpha X + \beta \leq y)$$
>> $$=P\left( X \geq\frac{y - \beta}{\alpha} \right)$$
>> (notice that we switched the sign of the inequality because $\alpha < 0$)
>> $$=1-P\left( X \leq \frac{y-\beta}{\alpha} \right)$$
>> $$=1-F_{X}\left( \frac{y-\beta}{\alpha} \right)$$
>> So the pdf of $Y$ is
>> $$f_{Y}(y) = F_{Y}'(y) = \frac{d}{dy}\left[ 1-F_{X}\left( \frac{y-\beta}{\alpha} \right) \right]$$
>> Applying the Chain Rule (and making the ghastly assumption that $\frac{d}{dx}F_{X} = f_{X}$ exists at $y$), we have $$f_{Y}(y) = -\frac{1}{\alpha} F'_{X}\left( \frac{y-\beta}{\alpha} \right)$$
>> $$=-\frac{1}{\alpha} f_{X}\left( \frac{y-\beta}{\alpha} \right)$$
>> By the definition of absolute value,
>> $$\frac{1}{| \alpha | }f_{X}\left( \frac{y-\beta}{\alpha} \right)$$

Back to the uniform distribution:
>[!r] Remark
>If $X \sim U(a, b)$ then $Y = \frac{1}{b-a} (X-a) \sim U(0,1)$ (i.e. $X = (b-a)Y + a$)
>>[!p] Proof
>>Apply the previous proposition with $$f_{X}(x) = \begin{cases}  \frac{1}{b-a} \quad a< x < b \\ 0 \quad \text{otherwise}  \end{cases}$$
>>and $\alpha = |\frac{1}{b-a}| = \frac{1}{b-a}$ (since we assume $b > a$), $\beta = \frac{-a}{b-a}$.
>>So by the previous proposition, $$f_{Y}(y) = \frac{1}{| \alpha | }f_{X}\left( \frac{y-\beta}{\alpha} \right)$$
>> We have $\frac{1}{| \alpha |}=\frac{1}{\alpha}= b-a$, and $\frac{y-\beta}{\alpha} = \frac{1}{\alpha}\left( y+\frac{a}{b-a} \right) =(b-a)\left( y+\frac{a}{b-a} \right)=(b-a)y+a$
>> So $$f_{Y} (y) = (b-a)f_{X}((b-a)y + a)$$

>[!t] Proposition
>If $X\sim U(a,b)$ then
>1. $\mathbb{E}(X) = \frac{b+a}{2}$
>2. $V(X) = \frac{(b-a)^2}{12}$
>>[!p] Proof
>>We have the relationship $$X = (b-a)Y + a$$ thus $$\mathbb{E}(X) = (b-a)\mathbb{E}(Y) + a$$, where $Y \sim U(0,1)$
>> and $$V(X) = (b-a)^2 V(Y)$$
>> We have $$\mathbb{E}(Y) = \int_{0}^{1} y \cdot 1 \, dy  = \frac{1}{2}$$
>> and $$\mathbb{E}(Y^2 )= \int_{0}^{1} y^2 \cdot 1 \, dy  = \frac{1}{3}$$
>> and $$V(Y) = \mathbb{E}(Y^2) - (\mathbb{E}(Y))^2$$
>> $$=\frac{1}{3} - \frac{1}{4} = \frac{1}{12}$$
>> So $$\mathbb{E}(X) = (b-a) \cdot \frac{1}{2} + a = \frac{b+a}{2}$$
>> and $$V(X) = (b-a)^2 \cdot \frac{1}{12}$$


>[!e] Example
>Assume $X \sim U(0,5)$.
>1. Find $P(-2 \leq x \leq 3)$.
>2. Find $\mathbb{E}(X ^4)$.
>
>
> $P(-2 \leq X \leq 3) = P(0 \leq X \leq 3) = \frac{1}{5} \cdot (3-0) = 0.6$
> The professor ended up showing $\mathbb{E}(X^5) = \int_{0}^{5} x^5 \cdot \frac{1}{5} \, dx$. You can also compute this in another way: since $X = 5Y$, we have $\mathbb{E}(X^5) = 5^5\mathbb{E}(Y^5) = 5^5 \mathbb{E}(Y^5) = 5^5 \cdot \int_{0}^{1} y^5 \, dy = \frac{5^5}{5}$.


---
#### Normal distribution
>[!d] Definition: Normal distribution
>We say that a continuous random variable $X$ has a **normal distribution** with mean $\mu$ and variance $\sigma^2$ ($X \sim N(\mu , \sigma^2)$) if the pdf of $X$ is $$f_{X}(x) = \frac{1}{\sigma \sqrt{ 2\pi }} e^{\frac{1}{2} \left( \frac{x-\mu}{\sigma} \right)^2} $$ 
> for all $x \in \mathbb{R}$.

The reason for this weird formula is $$\int_{-\infty}^{\infty} e^{-t^2/2} \, dt  = \sqrt{ 2\pi }$$ (this can be shown with Calc 3 knowledge). So $$\Phi_{Z}(t) := \int_{-\infty}^{\infty} \frac{1}{\sqrt{ 2\pi }}e^{-\frac{t^2}{2} }\, dx = 1$$ which is the cdf of the *standard normal distribution* ($Z \sim N(0, 1)$). Accordingly, its pdf is $f(t) = \frac{1}{\sqrt{ 2\pi }}e^{- \frac{t^2}{2}}$.

Because there is no closed form to the integral $\int_{-\infty}^{x} e^{-t^2/2} \, dt$, the values of $\Phi_{Z}(t)$ can only be computed numberically (usually with a table of pre-computed values). But we do know trivially that $\Phi_{Z} (0) = \frac{1}{2}$ and $\Phi_{Z}(x) + \Phi_{Z}(-x) = 1$, by symmetry.

>[!t] Proposition
>If $X \sim N(\mu, \sigma^2)$ then $Z := \frac{X - \mu}{\sigma} \sim N(0,1)$
>>[!p] Proof
>>We have $$f_{X}(x) = \frac{1}{\sigma \sqrt{ 2\pi }} e^{\frac{1}{2} \left( \frac{x-\mu}{\sigma} \right)^2}, \quad x \in \mathbb{R}$$
>>and $Z = \underbrace{\frac{1}{\sigma}}_\alpha x \;\;  \underbrace{-\frac{\mu}{\sigma}}_{\beta}$.
>>By the proposition we had earlier, we have $$f_{Z}(z) = \frac{1}{| \alpha | }f_{X}\left( \frac{z-\beta}{\alpha} \right)$$
>> $$=\sigma \cdot f_{X}\left( \left( z + \frac{\mu}{\sigma}  \right) \cdot \sigma\right)$$
>> $$=\sigma \cdot f_{X}(\sigma z + \mu)$$
>> $$\sigma  \cdot \frac{1}{\sigma \sqrt{ 2\pi }} e^{\frac{1}{2} \left( \frac{\sigma z+\mu-\mu}{\sigma} \right)^2}$$
>> $$=\frac{1}{\sqrt{ 2\pi }} \cdot e^{\frac{1}{2} z^2}$$
>> which is the pdf of a standard normal distribution. So $Z \sim N(0,1)$.

>[!t] Proposition
>If $X \sim N(\mu, \sigma^2)$ then
>1. $\mathbb{E}(X) = \mu$
>2. $V(X) = \sigma^2$
>>[!p] Proof
>>Since $X = \sigma Z + \mu$ where $Z \sim N(0,1)$, proving the above is equivalent to proving tht $\mathbb{E}(Z) = 0$ and $V(Z) = 1$.
>>We observe that $$\mathbb{E}(Z) = \int_{-\infty}^{\infty} \frac{t}{\sqrt{ 2\pi }} e^{- \frac{1}{2}t^2} \, dx $$
>>This integral converges, and since the integrand is an odd function we have that the integral is $0$.
>>On the other hand, $$\mathbb{E}(Z)^2 = \frac{1}{\sqrt{ 2\pi }} \int_{-\infty}^{\infty} t^2e^{- \frac{1}{2}}t^2  \, dx $$
>>The integral converges, and the integrand is an even function. So
>> $$\mathbb{E}(Z^2) = 2 \cdot \frac{1}{\sqrt{ 2\pi }} \int_{0}^{\infty} t^2e^{- \frac{1}{2}t^2} \, dt $$
>> Using integration by parts,
>> $$=\frac{2}{\sqrt{  2\pi}} \left[ \int_{0}^{\infty} t \cdot te^{-t^2/2} \, dt  \right] $$
>> $$=\frac{2}{\sqrt{ 2\pi }} \cdot \left[ \cancel{ -te^{-t^2/2}|_{0}^\infty }  +  \int_{0}^{\infty} e^{-t^2/2} \, dt   \right]$$
>> Because $e^{-t^2/2}$ is an even function and $\int_{-\infty}^{\infty} e^{-t^2/2} \, dt = \sqrt{ 2\pi }$, we have
>> $$\mathbb{E}(Z^2)=\frac{2}{\sqrt{ 2\pi }} \cdot \frac{1}{2} \cdot \sqrt{ 2\pi } = 1$$
>> So $V(Z) = \mathbb{E}(Z^2) - (\mathbb{E}(Z))^2 = 1$.

>[!e] Exercises
>For $Z \sim N(0,1)$, what is $\mathbb{E}(Z^{2n+1})$? (0)
>
>Find $\mathbb{E}(Z^{2n})$ by iteration, i.e. find a recursive formula dependent on $n$. (will be solved in class tomorrow)


>[!e] Example
>Refer to 4.71.
>For $X \sim N(\mu = 0.13, \sigma^2 = (0.005)^2)$, compute $P(0.12 < X < 0.14)$.
> $$P(0.12 < X < 0.14) = P(0.12 < 0.005Z + 0.13 < 0.14)$$
> $$=P\left( -\frac{0.01}{0.005} < Z < \frac{0.01}{0.005} \right)$$
> $$=P(-2 < Z < 2)$$
> $$=1-2\Phi_{Z}(-2)$$
> which (after consulting the table) we found to be $0.944$.
> <br>
> Let the above be the probability that a wire manufactured by a certain factory passes the specifications. Suppose you buy 4 of those wires. What is the probability that all 4 pass specifications?
> Let $X$ be the number of wires that pass specifications among the 4. We see that $X \sim B(4, 0.944)$. So $p_{X}(4) = C_{4}^4 (0.944)^4 (1-0.944)^0 = 0.944^4$.

---
#### A quick review of the gamma function
>[!d] Definition: Gamma function
> $$\Gamma(\alpha) = \int_{0}^{\infty} t^{\alpha - 1}e^{-t} \, dt $$

We have $$\Gamma(\alpha) =\underbrace{ \int_{0}^{1} t^{\alpha - 1}e^{-t} \, dt}_{\text{comparable to }\int_{0}^{1} t^{\alpha-1} \, dt \text{ which converges for } \alpha \cancel{ -1 + 1 } > 0} + \underbrace{\int_{1}^{\infty} t^{\alpha-1}e^{-t} \, dt}_{\text{always converges}}  $$
So $\Gamma(\alpha)$ is defined for $\alpha > 0$.

>[!t] Properties of the gamma function
>For all $\alpha > 0$, we have $\Gamma(\alpha +1) = \alpha \Gamma(\alpha)$.
>>[!p] Proof
>> $$\Gamma(\alpha + 1) = \int_{0}^{\infty} t^{\alpha} e^{-t} \, dt $$
>> Applying integration by parts,
>> $$=[-t^\alpha e^{-t}]_{0}^\infty + \int_{0}^{\infty} \alpha t^{\alpha - 1}e^{-t} \, dt $$
>> $$=\alpha \Gamma(\alpha)$$

We compute that $\Gamma(1) = \int_{0}^{\infty} e^{-t} \, dt = -e^{-t}|0^\infty = 1$. By induction (here the scribe skips a thousand steps which are left as exercise to the reader), for $n \in \mathbb{N}$, we have $\Gamma(n) = (n-1)!$.

Given that $\Gamma\left( \frac{1}{2} \right) = \sqrt{ \pi }$, we have $\Gamma\left( \frac{3}{2} \right) = \frac{1}{2} \cdot \Gamma\left( \frac{1}{2} \right) = \frac{1}{2} \sqrt{ \pi }$, $\Gamma\left( \frac{5}{2} \right) = \frac{3}{2} \cdot \frac{1}{2} \sqrt{ \pi },$ ... We observe that
$$\Gamma\left( \frac{2n+1}{2} \right) = \underbrace{\frac{2n-1}{2} \cdot \frac{2n-3}{2} \cdot \dots \cdot \frac{1}{2}}_{n\text{ terms}} \cdot \sqrt{ \pi }$$
$$=\frac{1}{2^n} (2n-1)(2n-3) \dots(3)(1)\sqrt{ \pi }$$
$$=\frac{\sqrt{ \pi }}{2^n}\left[ \frac{(2n)!}{\underbrace{ (2n)(2n-2)\dots(4)(2) }_{ n\text{ terms} }} \right]$$
$$=\frac{\sqrt{ \pi }}{2^n}\left[ \frac{(2n)!}{2^n(n)(n-1)\dots(2)(1) } \right]$$
$$=\frac{\sqrt{ \pi }}{2^n} \left[ \frac{(2n)!}{2^n \cdot n!} \right]$$
$$=\frac{(2n)!}{2^{2n}\cdot n!}\sqrt{ \pi }$$


>[!t] Key formula
> $$\int_{0}^{\infty} t^ae^{-bt} \, dt  = \frac{1}{b^{a+1}}\Gamma(a+1)$$
for $b > 0$, $a+ 1 > 0$.
>>[!p] Proof
>>Make the change of variables $s = bt$. We have $$\int_{0}^{\infty} t^ae^{-bt} \, dt  = \frac{1}{b}\int_{0}^{\infty} \left( \frac{s}{b} \right)^a e^{-s} \, ds$$
>> $$= \frac{1}{b^{a+1}}\int_{0}^{\infty} s^ae^{-s} \, ds  $$
>> $$=\frac{1}{b^{a+1}} \Gamma(a + 1)$$


>[!r] Remark
>For $\alpha  > 0, \beta > 0$, we have
> $$\int_{0}^{\infty} x^{\alpha-1}e^{-x/\beta} \, dx  = \frac{\Gamma(\alpha)}{\left( \frac{1}{\beta} \right)^\alpha}= \beta^a\Gamma(\alpha)$$
> hence $\frac{1}{\beta^\alpha \Gamma(\alpha)}\int_{0}^{\infty} x^{\alpha-1}e^{-x/\beta} \, dx = 1$.

>[!d] Definition: Gamma distribution
>The function $$f_{X}(x) = \begin{cases}  \frac{1}{\beta^\alpha \Gamma(\alpha)}x^{\alpha - 1} e^{-x/\beta} \quad x \in (0, \infty) \\ 0 \quad \text{ otherwise}  \end{cases}$$
>is a pdf. $X$ is said to have a Gamma distribution with parameter $\alpha, \beta$, written as $X \sim \text{Gamma}(\alpha, \beta)$.

>[!e] Exercise
>If $X \sim G(\alpha, \beta)$, then $Y := \frac{X}{\beta} \sim G(\alpha,1)$.

>[!t] Proposition
>If $X \sim G(\alpha, \beta)$, then
>1. $\mathbb{E}(X) = \beta\alpha$
>2. $V(X) = \beta^2 \alpha$
>>[!p] Proof
>> $$\mathbb{E}(X) = \int_{0}^{\infty} xf_{X}(x) \, dx $$
>> $$\int_{0}^{\infty} \frac{1}{\Gamma(\alpha)\beta^\alpha} x^\alpha e^{-x/\beta} \, dx $$
>> $$=\frac{1}{\Gamma(\alpha)\beta^\alpha} \int_{0 }^{\infty} x^\alpha e^{-x/\beta} \, dx $$
>> $$=\frac{1}{\Gamma(\alpha)\beta^\alpha} \cdot (\beta)^{\alpha + 1} \cdot \Gamma(\alpha + 1)$$
>> $$\frac{1}{\Gamma(\alpha)\beta^\alpha} \cdot \beta^{\alpha + 1} \cdot \alpha \Gamma(\alpha)$$
>> $$=\beta\alpha$$
>> and $$\mathbb{E}(X^2) = \frac{1}{\beta^\alpha\Gamma(\alpha)} \int_{ 0}^{\infty} x^{\alpha + 1} e^{-x/\beta} \, dx $$
>> $$=\frac{1}{\beta^\alpha\Gamma(\alpha)} \cdot \beta^{\alpha + 2} \Gamma(\alpha + 2)$$
>> $$=\frac{1}{\beta^\alpha \Gamma(\alpha)} \cdot \beta^{\alpha +2} (\alpha + 1) (\alpha)\Gamma(\alpha)$$
>> $$=\beta^2(\alpha +1)(\alpha)$$
>> So $V(X) = \mathbb{E}(X^2) - (\mathbb{E}(X))^2 =\beta^2\alpha$

>[!e] Exercise
>For $X \sim G(\alpha, \beta)$ we have
> $$\mathbb{E}(X^n) = \beta^n (\alpha)(\alpha+1)(\alpha+2)\dots(\alpha+n-1)$$


For tomorrow:
Many distributions come from the gamma distribution, such as the exponential distribution ($\alpha = 1$) and chi-square distribution ($\beta = 2, \alpha = \frac{p}{2}$).