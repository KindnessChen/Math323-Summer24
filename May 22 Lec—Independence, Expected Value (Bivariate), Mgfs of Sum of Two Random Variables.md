 We did this example before:
>[!e] Example
> $$f(x,y) = \begin{cases}  6x \quad 0 < x < y < 1 \\ 0 \quad \text{otherwise}  \end{cases}$$
> and saw that $X \sim Beta(2,2), Y \sim Beta(3,1)$ (marginal distributions).
> Let us find $f(y | X = x) = \frac{f(x,y)}{f_{X}(x)}$
> $$f(y|X = x) = \begin{cases}  \frac{6x}{f_{X}(x)} \quad x < y < 1 \\ 0 \quad \text{otherwise}  \end{cases}$$
> $$=\begin{cases}  \frac{6x}{6x(1-x)} = \frac{1}{1-x}\quad x < y < 1 \\ 0 \quad \text{otherwise}  \end{cases}$$
> Given $X = x$, we see $Y \sim U(x, 1)$.
> Now calculating $f(x | Y = y) = \frac{f(x,y)}{f_{Y}(y)}$:
> $$f(x | Y = y) = \begin{cases}  \frac{6x}{3y^2} = \frac{2x}{y^2} \quad 0 < x < y \\ 0 \quad \text{otherwise} \end{cases}$$
> Given $Y = y$, we have $X \sim Y \cdot Beta(2,1)$ (you can easily verify this by using the formula $f_{V}(v) = \frac{1}{| \alpha | }f_{U}\left( \frac{v-\beta}{\alpha} \right)$ for $V = \alpha U + \beta$, taught in May 14)

>[!e] Example 2
> $$f(x,y) = \begin{cases}  e^{-x} \quad 0 < y < x \\ 0 \quad \text{otherwise}  \end{cases}$$
> We found yesterday that $X \sim G(\alpha = 2, \beta = 1)$, $Y \sim E(\beta = 1)$.
> Let $x > 0$. Given $X = x$, we have $$f(y |X = x ) = \frac{f(x,y)}{f_{X}(x)} = \begin{cases}  \frac{e^{-x}}{xe^{-x}} \quad 0 < y < x \\ 0 \quad \text{otherwise}  \end{cases}$$
> So given $X = x$, we have $Y \sim U(0,x)$.
> Now for $f(x|Y = y)$:
> $$f(x | Y = y) = \begin{cases}  \frac{e^{-x}}{e^{-y}} = e^{-(x+y)} \quad y < x \\ 0 \quad \text{otherwise}  \end{cases}$$
> So given $Y = y$, we have $X + Y  \sim Exponential(1)$.
> Intuitively, $X$ and $Y$ are dependent. We'll formally define this notation now.


---
#### Independence
>[!d] Definition: 
>1. Let $(X, Y)$ be a pair of discrete random variables, and $p$ be their jpf. We say $X$ and $Y$ are independent if $$p(x,y) = p_{X}(x) p_{Y}(y)$$
>2. If $(X, Y)$ is a pair of continuous random variables and $f$ is their jpdf, then $X$ and $Y$ are independent if $$f(x,y) = f_{X}(x) f_{Y}(y)$$

The motivation of this definition is the fact that, in the discrete case, $$p(x,y) = P(\{ X = x \} \cap \{ Y =y \})$$
and if $X$ and $Y$ are independent, then $\{ X = x \}$ and $\{ Y = y \}$ should be independent events too. So
$$p(x,y)=P(\{ X = x \}) \cdot P(\{Y = y\})$$
$$=p_{X}(x) \cdot p_{Y}(y)$$
So the above definition of independence is equivalent to saying that (in the discrete case, and vice versa for $Y$)
$$p(x | Y = y) = \frac{p(x,y)}{p_{Y}(y)} = p_{X}(x)$$
and (in the continuous case, vice versa for $Y$)
$$f(x|Y = y) = \frac{f(x,y)}{f_{Y}(y)} = f_{X}(x)$$


>[!e] Example
>$y$-value\ $x$-value | $-1$ | $0$ | $1$ | $p_{Y}(y)$
-- | -- | -- | --| --
$0$ | $\frac{1}{4}$ | $\frac{1}{6}$ | $\frac{1}{12}$ | $\frac{1}{2}$
$1$ | $\frac{1}{4}$ | $0$ | $\frac{1}{4}$ | $\frac{1}{2}$
$p_{X}(x)$ | $\frac{1}{2}$ | $\frac{1}{6}$ | $\frac{1}{3}$
>$Y$ and $X$ cannot possibly be independent because $p(0,1) = 0 \neq p_{X}(0)\cdot p_{Y}(1)$.

Also consider these two supports, the first for a discrete distribution and the second for a continuous one:
![[desmos-graph-11.png]]![[desmos-graph-13.png]]
In the first case, if $X =4$ then $p(Y=4 | X = 4) = 0$, but if $X = 2$ then $p(Y = 4 | X = 2) \neq 0$.
In the second case, a similar thing happens if we choose $y = 0$ and $X = -0.2$.

>[!t] Proposition
>If two continuous random variables $X, Y$ are independent, then their joint support is rectangular type.
>If the joint support is rectangular type, a sufficient condition is $f(x,y) = h(x) g(y)$.
>In total, two continuous random variables $X, Y$ are independent if and only if their joint support is of rectangular type and $f(x,y) = h(x) g(y)$ for some functions $h(x),g(y)$.

>[!e] Examples
> 1. $$f(x,y) = \begin{cases}  6x \quad 0 < x < y < 1 \\ 0 \quad \text{otherwise}  \end{cases}$$
> We drew the support of this before—it's not rectangular, so $X$ and $Y$ aren't independent.
> 2. $$f(x,y) = \begin{cases}  x + y \quad x, y \in (0,1) \\ 0 \quad \text{otherwise}  \end{cases}$$
> Rectangular support, but for the sake of your dear life you can't write the kernel $x + y$ as a product of a function of $x$ and a function of $y$.
> 3. $$f(x,y) = \begin{cases}  2x^2ye^{-(x+2y)} \quad x, y  > 0 \\ 0 \quad \text{otherwise}  \end{cases}$$
> Rectangular type support, but that fact alone is not enough.
> We want to write it as functions of $X$ and $Y$ in the form of $h(x) = C_{1} \cdot x^2 e^{-x}$ and $g(y) =C_{2}\cdot ye^{-2y}$.
> If $X$ and $Y$'s marginal distributions have these kinds of kernel, we see that $X \sim G(\alpha = 3, \beta = 1)$ so $C_{1} = \frac{1}{2}$, and $Y \sim G\left( \alpha = 2, \beta = \frac{1}{2} \right)$ so $C_{2} = 4$. Hence we should split the $2$ in $f(x,y)$ as $4 \cdot \frac{1}{2}$.

---
#### Expected value
You have seen that, for discrete cases,
$$\mathbb{E}(h(x)) = \sum_{ x } h(x)p_{X}(x)$$
and for continuous cases, $$\mathbb{E}(h(x))=\int_{-\infty}^{\infty} h(x)f_{X}(x) \, dx $$
For joint random variables, this is a generalization:
>[!d] Definition: Expected value (joint random variables)
>1. Let $(X, Y)$ be a pair of discrete random variables and $p(x,y)$ be their jpf. If $h: \mathbb{R}^2 \to \mathbb{R}$, then $$\mathbb{E}(h(x,y)) = \sum_{ x,y} h(x,y)p(x,y) $$
>2. Let $(X,Y)$ be a pair of continuous random variable and $f(x,y)$ be their jpdf. Again, if $h: \mathbb{R}^2 \to \mathbb{R}$, then $$\mathbb{E}(h (x,y)) = \iint_{\mathbb{R}^2}h(x,y)f(x,y)\; dA$$

The univariate case is a special case of the bivariate case: Let $h(x,y) = g(x)$. Then $\mathbb{E}(h(x,y)) = \mathbb{E}(g(x))$. So $$\iint_{\mathbb{R}^2}h(x,y)f(x,y)\;dA = \int_{-\infty}^{\infty}\left( \int_{-\infty}^{\infty} g(x)f(x,y) \, dy  \right)  \, dx $$
$$=\int_{-\infty}^{\infty}g(x)\left( \int_{-\infty}^{\infty} f(x,y) \, dy  \right)  \, dx $$
$$=\int_{-\infty}^{\infty}g(x)f_{X}(x)  \, dx = \mathbb{E}(g(x))$$

>[!t] Proposition
>1. If $h(x,y) = C$ a constant, then $\mathbb{E}(h(x,y)) = C$.
>2. $\mathbb{E}(h_{1}(x,y) + h_{2}(x,y)) = \mathbb{E}(h_{1}(x,y)) + \mathbb{E}(h_{2}(x,y))$. In particular, $$\mathbb{E}(X+Y) = \mathbb{E}(X) + \mathbb{E}(Y)$$
>3. If $\alpha \in \mathbb{R}$ is a constant, then $\mathbb{E}(\alpha\cdot h(x,y)) = \alpha \cdot \mathbb{E}(h(x,y))$.



>[!e] Example
>$y$-value\ $x$-value | $-1$ | $0$ | $1$ | $p_{Y}(y)$
-- | -- | -- | --| --
$0$ | $\frac{1}{4}$ | $\frac{1}{6}$ | $\frac{1}{12}$ | $\frac{1}{2}$
$1$ | $\frac{1}{4}$ | $0$ | $\frac{1}{4}$ | $\frac{1}{2}$
$p_{X}(x)$ | $\frac{1}{2}$ | $\frac{1}{6}$ | $\frac{1}{3}$
>We calculate $\mathbb{E}(XY)$:
> $$\mathbb{E}(XY) = \sum_{ x,y }xyp(x,y) $$
> A term is $0$ if any one of its factors is $0$. So the sum consists of only two nonzero terms:
> $$\mathbb{E}(XY) = (-1)(1)\left( \frac{1}{4} \right) + (1)(1)\left( \frac{1}{4} \right) = 0$$


>[!e] A continuous example
> $$f(x,y)  \begin{cases}  6x \quad 0 < x < y < 1 \\ 0 \quad \text{otherwise}  \end{cases}$$
> The support we have drawn very many times, it is the upper left triangle of a unit square:
> ![[desmos-graph-7.png]]
> We compute $\mathbb{E}(X^2Y + Y^2)$:
> $$\mathbb{E}(X^2Y + Y^2) = \mathbb{E}(X^2Y) + \mathbb{E}(Y^2)$$
> Calculating each of the right-hand-side terms:
> $$\mathbb{E}(X^2Y) = \iint_{\mathbb{R}^2}x^2yf(x,y)\;dA$$
> $$=\int_{0}^{1} \int_{0}^{y} x^2y \cdot 6x \, dx  \, dy $$
> $$=\int_{0}^{1} \frac{3}{2}y^5 \, dy = \frac{1}{4}$$
> and $$\mathbb{E}(Y^2) = \iint_{\mathbb{R}^2}y^2f(x,y)\; dA$$
> $$=\int_{0}^{1} \int_{0}^{y} y^26x \, dx  \, dy $$
> $$=\int_{0}^{1} 3y^4 \, dy =\frac{3}{5}$$ 
> so $$\mathbb{E}(X^2Y + Y^2)=\frac{1}{4} + \frac{3}{5} = \frac{17}{20}$$


The next thing is SUPER IMPORTANT!!!
>[!t] Proposition
>Let $X$ and $Y$ be two independent random variables. Let $h, g$ be two functions $\mathbb{R} \to \mathbb{R}$. Then $$\mathbb{E}(h(x)g(y)) = \mathbb{E}(h(x))\mathbb{E}(g(y))$$
>>[!a] Scribe's aside
>>We shall see in a few lectures what this formula would look like if $X$ and $Y$ are not independent.
>
>>[!p] Proof
>> $$\mathbb{E}(h(x)g(y)) = \iint_{\mathbb{R}^2}h(x)g(y)f(x,y) \; dA$$
>> $$=\iint_{\mathbb{R}^2}h(x)g(y)f_{X}(x)f_{Y}(y) \; dA$$
>> $$=\int_{-\infty}^{\infty}g(y)f_{Y}(y) \left( \int_{-\infty}^{\infty} h(x)f_{X}(x) \, dx \right)  \, dy $$
>> $$=\int_{-\infty}^{\infty} g(y)f_{Y}(y)\mathbb{E}(h(x)) \, dy$$
>> $$=\mathbb{E}(h(x)) \int_{-\infty}^{\infty} g(y)f_{Y}(y) \, dy $$
>> $$=\mathbb{E}(h(x))\mathbb{E}(g(y))$$


>[!t] Proposition
>If $X, Y$ are independent, then $V(X + Y) = V(X) + V(Y)$
>>[!p] Proof
>> $$V(X + Y) = \mathbb{E}((X + Y)^2) - (\mathbb{E}(X)+ \mathbb{E}(Y))^2$$
>> $$=\mathbb{E}(X^2 + 2XY + Y^2) - ([\mathbb{E}(X)]^2 + 2\mathbb{E}(X)\mathbb{E}(Y) + [\mathbb{E}(Y)]^2)$$
>> $$= (\mathbb{E}(X^2) - (\mathbb{E}(X))^2) + (\mathbb{E}(Y^2) - (\mathbb{E}(Y))^2) + 2 (\mathbb{E}(XY) - \mathbb{E}(X)\mathbb{E}(Y))$$
>> $$= V(X)  + V(Y)$$


>[!t] Proposition
> If $X, Y$ are independent, and $W = X + Y$, the mgf of $W$ is $$m_W(t) = m_{X}(t)\cdot m_{Y}(t)$$
> >[!p] Proof
> >(Laplace transform and convolutions!)
> > $$\mathbb{E}(e^{tw}) = \mathbb{E}(e^{t(x+ y)})$$
> > $$=\mathbb{E}(e^{tx} e^{ty})$$
> > $$=\mathbb{E}(e^{tx}) \mathbb{E}(e^{ty})$$


>[!e] Examples
>1. Sum of two binomials. Let $X_{1} \sim B(N_{1}, p_{1})$, $X_{2} \sim B(N_{2}, p_{2})$. Suppose $X_{1}, X_{2}$ are independent, and let $X = X_{1} + X_{2}$. Then $$m_{X}(t) = m_{X_{1}}(t)m_{X_{2}}(t)$$
> $$=[p_{1}e^t+(1-p_{1})]^{N_{1}} \cdot [p_{2}e^t + (1-p_{2})]^{N_{2}}$$
> If $p_{1} = p_{2} =: p$, then
> $$m_{X}(t) = [pe^t + (1-p)]^{N_{1}+ N_{2}}$$
> so $X\sim B(N_{1} + N_{2}, p)$. Otherwise, you really can't get much information out of this.
> <br>
> 2. Let $X_{1} \sim P(\lambda_{1})$ be independent from $X_{2} \sim P(\lambda_{2})$. Let $X = X_{1} + X_{2}$. Then $$m_{X}(t) = m_{X_{1}}(t) \cdot m_{X_{2}}(t)$$
> $$=e^{\lambda_{1}(e^t-1)}e^{\lambda_{2}(e^t-1)}$$
> $$=e^{(\lambda_{1}+ \lambda_{2})(e^t-1)}$$
> So $X \sim P(\lambda_{1} + \lambda_{2})$.
> 3. Let $X_{1} \sim N(\mu_{1}, \sigma_{1}^2)$ be independent from $X_{2} \sim N(\mu_{2}, \sigma_{2}^2)$. Let $X = X_{1} + X_{2}$. Then $$m_{X}(t) = m_{X_{1}}(t)\cdot m_{X_{2}}(t)$$
> $$=e^{\left\{  \mu_{1}t + \frac{1}{2}\sigma_{1}^2t^2  \right\}}e^{\left\{  \mu_{2}t + \frac{1}{2}\sigma_{2}^2t^2  \right\}}$$
> $$=e^{(\mu_{1}+\mu_{2})t+\frac{1}{2}(\sigma_{1}^2+\sigma_{2}^2)t^2}$$
> So $X \sim N(\mu_{1}+\mu_{2},\sqrt{ \sigma_{1}^2 + \sigma_{2}^2 })$.
> 4. Let $X_{1} \sim \Gamma(\alpha_{1}, \beta)$ be independent from $X_{2}\sim G(\alpha_{2}, \beta)$ (note that here we require that $X_{1}, X_{2}$ have the same $\beta$). Let $X = X_{1} + X_{2}$. Then $$m_{X}(t) = m_{X_{1}}(t) \cdot m_{X_{2}}(t)$$
> $$=\frac{1}{(1-\beta t)^{\alpha_{1}}} \cdot \frac{1}{(1-\beta t)^{\alpha_{2}}}$$
> $$=\frac{1}{(1-\beta t)^{\alpha_{1}+\alpha_{2}}}$$
> so $X \sim \Gamma(\alpha_{1} + \alpha_{2}, \beta)$.