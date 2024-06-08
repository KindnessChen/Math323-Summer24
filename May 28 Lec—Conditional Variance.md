Recall we proved that $$Cov(Y-\mathbb{E}(Y|X), H(X)) = 0$$
so $Y -\mathbb{E}(Y|X) \perp \mathbb{E}(Y|X)$.
If we transform the Pythagorean theorem of vector spaces to here ($\| u \|^2 = \| w \|^2 +\| u-w \|^2$ for $u \perp w$), and keeping in mind that $\| X\|^2 = Cov(X) = V(X)$, we have $$V(Y)= V(\mathbb{E}(Y|X)) + V(Y -\mathbb{E}(Y|X))$$


>[!t] Proposition
> $$V(Y)= V(\mathbb{E}(Y|X)) + V(Y -\mathbb{E}(Y|X))$$
> >[!p] Proof
> > $$V(Y) = Cov(Y,Y)$$
> > Adding and subtracting $\mathbb{E}(Y|X)$:
> > $$=Cov[(Y-\mathbb{E}(Y|X)) + \mathbb{E}(Y|X), (Y-\mathbb{E}(Y|X))+\mathbb{E}(Y|X)]$$
> > $$=V(Y-\mathbb{E}(Y|X)) + V(\mathbb{E}(Y|X)) + \underbrace{ 2Cov(\mathbb{E}(Y|X), Y-\mathbb{E}(Y|X)) }_{ =0 }$$

>[!r] Remark
> Since by the Tower Property we have $\mathbb{E}(Y - \mathbb{E}(Y|X)) = 0$, we have $V(Y-\mathbb{E}(Y|X)) = \mathbb{E}((Y-\mathbb{E}(Y|X))^2)$.
> Again by the Tower Property,
> $$V(Y-\mathbb{E}(X)) = \mathbb{E}(\mathbb{E}([Y-\mathbb{E}(Y|X)]^2 | X))$$

>[!d] Definition
>The random variable $$\mathbb{E}[(Y-\mathbb{E}(Y|X))^2 | X]$$
>is called the **conditional variance** of $Y$ given $X$ and is denoted $V(Y|X)$.

Applying the Proposition, the Remark, and the Definition, we conclude
$$V(Y) = V(\mathbb{E}(Y|X)) + \mathbb{E}(V(Y|X))$$

>[!e] Example
>Continuing the restaurant example we had yesterday. Find $\mathbb{E}(X_{1})$ and $V(X_{1})$.
>
>Given $X$ fixed, we knew that $X_{1} \sim B(X, p)$.
>So $\mathbb{E}(X_{1} | X) = Xp$ and $V(X_{1} | X) = Xp(1-p)$.
>$\mathbb{E}(X_{1}) = \mathbb{E}(\mathbb{E}(X_{1} | X)) = \mathbb{E}(Xp) = p\mathbb{E}(X) = \lambda p$ (we would have gotten the same answer if we used the fact that $X \sim P(\lambda p)$)
>and $$V(X_{1}) = \mathbb{E}(V(X_{1}|X)) + V(\mathbb{E}(X_{1} | X))$$
> $$\mathbb{E}(p(1-p)X) + V(pX)$$
> $$p(1-p)\mathbb{E}(X) + p^2V(X)$$
> $$=\lambda p(1-p) + p^2\lambda=\lambda p$$
> as we expected from the fact that $X \sim P(\lambda p)$.

>[!e] Another example
>Suppose $X \sim \Gamma(\alpha=2, \beta=2)$
>Given $X =x$, suppose $Y \sim U(0, \sqrt{ x })$.
>Find $\mathbb{E}(Y)$ and $V(Y)$.
>
>First, try to brute-force it.
>We know $f_{X}(x) = \frac{1}{\beta^a \Gamma(\alpha)}x^{\alpha-1}e^{-x/\beta} =\frac{1}{4}xe^{-\frac{x}{2}}$ with domain $(0, \infty)$
>and $f(y | X = x) =\frac{1}{\sqrt{ x }}$, domain $(0, \sqrt{ x })$
>So $$f(x,y) = f_{X}(x) \cdot f(y | X = x) = \begin{cases}  \frac{1}{4} xe^{-\frac{x}{2}} \cdot \frac{1}{\sqrt{ x }}\quad 0 < y < \sqrt{ x } \\ 0 \quad \text{otherwise}\end{cases}$$
> $$\begin{cases}  \frac{1}{4} \sqrt{ x }e^{-\frac{x}{2}} \quad 0 < y < \sqrt{ x } \\ 0 \quad \text{otherwise}\end{cases}$$
>![[desmos-graph-14.png]]
> So $$f_{Y}(y) = \int_{-\infty}^{\infty} f(x,y) \, dx $$
> $$=\begin{cases}  \int_{y^2}^{\infty} \frac{1}{4}\sqrt{ x }e^{-x/2} \, dx \quad y > 0 \\ 0 \quad \text{otherwise}   \end{cases}$$
> (Good luck trying to find a closed form for that)
> and
> $$\mathbb{E}(Y) = \int_{0}^{\infty} yf_{Y}(y) \, dy $$
> $$\int_{0}^{\infty} y\left( \int_{y^2}^{\infty} \frac{1}{4}\sqrt{ x }e^{-x/2} \, dx  \right) \, dx $$
> Swap the order of integration (which is what we did in the Tower Property anyway):
> $$=\int_{0}^{\infty} \int_{0}^{\sqrt{ x }} y \cdot \frac{1}{4}\sqrt{ x }e^{-x/2} \, dy  \, dx $$
> $$\int_{0}^{\infty} \frac{1}{4}\sqrt{ x }e^{-x/2}\cdot \frac{x}{2} \, dx $$
> $$=\mathbb{E}\left( \frac{\sqrt{ x }}{2} \right)$$
> (you can compute it, which we'll do below)
> 
> On the other hand, we could have just used the Tower Property and the formulas derived from it:
> $\mathbb{E}(Y |X) = \mathbb{E}(Y | X = x) = \frac{\sqrt{ x }}{2}$
> and $V(Y | X) = V(Y | X = x) = \frac{(\sqrt{ x })^2}{12} = \frac{x}{12}$ by the properties of the uniform distribution.
> So, $$\mathbb{E}(Y) = \mathbb{E}(\mathbb{E}(Y | X)) = \frac{1}{2} \mathbb{E}(\sqrt{ x })$$
> which is a lot lot easier to do:
> $$\frac{1}{2}\mathbb{E}(\sqrt{ x }) = \frac{1}{2} \int_{0}^{\infty} \frac{1}{4}xe^{-\frac{x}{2}} \sqrt{ x }\, dx $$
> $$=\frac{1}{8}\int_{0}^{\infty} x^{3/2}e^{-x/2} \, dx $$
> $$\frac{1}{8} \cdot 2^{5/2} \cdot \Gamma\left( \frac{5}{2} \right)$$
> $$= \frac{3\sqrt{ 2 \pi}}{8}$$
> and $$V(Y) = \mathbb{E}(V (Y |X)) + V(\mathbb{E}(Y|X))$$
> $$=\mathbb{E}\left( \frac{x}{3} \right) + V\left( \frac{\sqrt{ x }}{2} \right)$$
> $$\frac{1}{3} \cdot \mathbb{E}(X) + \mathbb{E}\left( \left( \frac{\sqrt{ x }}{2} \right)^2 \right) - \left( \mathbb{E}\left( \frac{\sqrt{ x }}{2} \right) \right)^2$$
> $$\frac{1}{3}\mathbb{E}(X) + \mathbb{E}\left( \frac{X}{4} \right) - \left( \frac{1}{2}\mathbb{E}(\sqrt{ x }) \right)$$
> $$=\frac{7}{12}\mathbb{E}(X) - \frac{1}{2}\mathbb{E}(\sqrt{ x })$$
> $$=\frac{7}{12}\cdot 4 +\frac{3\sqrt{ 2 \pi}}{8} = \frac{56 + 9\sqrt{ 2\pi }}{24}$$