A fumbled-up quiz question:
Choose one ball from 3 reds and 6 blues. If you get a red, flip an unfair coin with $P(H|R) = p$, $P(T|R) = 1-p$. If you get a blue, flip another unfair coin with $P(T|B) = q$, $P(H|B) = 1-q$. If $H$ is $+2$ and $T$ is $-1$, find the expected value.
$P(H) = P(R)P(H | R)  + P(B)P(H | B) = \frac{1}{3} \cdot p+\frac{2}{3}(1-q)$
$P(T) = P(R)P(T | R)  + P(B)P(T | B) =\frac{1}{3}(1-p)+\frac{2}{3}q$
$\mathbb{E}(\text{score}) =2\left( \frac{1}{3}p+\frac{2}{3}(1-q) \right) -(\frac{1}{3}(1-p)+\frac{2}{3}q) = p-2q+1$

---
#### Exponential distributions
Recall that $$\int_{0}^{\infty} x^ae^{-bx} \, dx  = \frac{\Gamma(a+1)}{b^{a+1}}$$
for $a > -1, b > 0$.
>[!d] Definition: Exponential distribution
Exponential distributions are gamma distributions with $\alpha = 1$. We write $X \sim \text{Exponential}(\beta)$, and the pdf of $X$ is $$f_{X}(x) = \begin{cases}  \frac{1}{\beta} e^{-x/\beta} \quad x \in (0, \infty) \\ 0 \quad \text{ otherwise}  \end{cases}$$
The cdf of $X$ is $$F_{X}(t) = \int_{-\infty}^{x} f_{X}(t) \, dt = \begin{cases}  1-e^{-x/\beta} \quad x \geq 0 \\ 0 \quad \text{otherwise}  \end{cases}$$

>[!r] Remark
>Just writing $$f(x) = \frac{1}{\beta} e^{-x/\beta}$$ without specifying the domain does *not* make $f(x)$ a pdf.


Exponential distributions are used to model lifetimes.
>[!d] Definition: Survival function
> $$S(x) = P(X > x)= 1-F_{X}(x)$$
> $$=\begin{cases}  1 \quad x \leq 0 \\ e^{-x/\beta}\quad x \geq 0  \end{cases}$$

Because $S(a+b) = S(a) S(b)$ for $a, b > 0$ due to the properties of the exponential distribution, we have $$P(X > a+ b) = P(X > a) P(X >b)$$
$$\frac{P(X> a + b)}{P(X > a)} = P(X > b)$$
Since $P(X > a + b) = P([X > a + b] \cap [X > a])$,
$$\frac{P([X > a + b] \cap [X > a])}{P(X > a)} = P(X > b)$$
The right hand side is $P(X > a + b | X > a)$, so we have $$P(X > a + b | X > a) = P(X > b)$$
which is the famous **memoryless property**.
>[!r] Remark
>Exercise for those that love analysis: It can be prove that any continuous function that satisfies $F(a + b) = F(a) F(b)$ is exponential. So this is the only distribution with this property.

>[!t] Properties of the exponential distribution
>1. $\mathbb{E}(X) = \beta$
>2. $V(X) = \beta^2$
>
>>[!p] Proof
>>Obviously elementary from the fact that $X$ also has a gamma pdf.

>[!e] Example
>Let $X \sim E(\beta)$ with $\mathbb{E}(X) = \beta$. Consider $$Y = \begin{cases}  10 \quad 0 < x < 2 \\
15 \quad 2 < x < 4 \\
50 \quad x > 4  \end{cases}$$
Find $\mathbb{E}(Y)$.
>We see that $\beta = 4$ $p_{Y}(10) = F_{X}(2) = 1-e^{-1/2}$,
>$p_{Y}(15) = F_{X}(4) - F_{X}(2) =e^{-1/2} - e^{-1}$
>$p_{Y}(50) = 1-F_{X}(4) = e^{-1}$.
>So $\mathbb{E}(Y) =$

---
#### Chi-square distribution
Let $Z \sim N(0,1)$. We find the distribution of $X = Z^2$.
We first find the cdf of $X$.
$$F_{X}(x) = P(X = Z^2 \leq x) = 0, \; x < 0$$
If $x > 0$, $$F_{X}(x) = P(Z^2 \leq x)$$
$$=P(-\sqrt{ x } \leq Z \leq \sqrt{ x })$$
$$=\Phi_{Z}(\sqrt{ x }) - \Phi_{Z}(-\sqrt{ x })$$
By symmetry,
$$=2\Phi_{Z}(\sqrt{ x }) - 1$$

So we have $$F_{X}(x) = \begin{cases}  0 \quad x < 0 \\
2 \Phi_{Z}(\sqrt{ x }) -1 \quad x \geq 0 \end{cases}$$
The pdf of $X$ is $$f_{X}(x) = \begin{cases}  0 \quad x < 0 \\ \frac{1}{\sqrt{ x }}\Phi_{Z}'(\sqrt{ x }) \quad x > 0  \end{cases}$$
Recall that $\Phi_{Z}(t) =f_{Z}(t)  = \frac{1}{\sqrt{ 2\pi }} e^{-t^2/2}$
So $$f_{X}(x) = \begin{cases}  0 \quad x < 0 \\ \frac{1}{\sqrt{ 2\pi }}x^{-1/2}e^{-x/2}  \quad x > 0  \end{cases}$$

We therefore observe that $X \sim G\left( \alpha = \frac{1}{2}, \beta = 2 \right)$

(Aside: From here we learn that $\frac{1}{\Gamma\left( \frac{1}{2} \right) \cdot \left( \frac{1}{2} \right)^{1/2}} = \frac{1}{\sqrt{ 2\pi }}$ so $\Gamma\left( \frac{1}{2} \right) = \sqrt{ \pi }$.)

>[!d] Definition: Chi-square distribution
>$X$ is said to have a chi-square distribution with $p$ degrees of freedom ($X \sim \chi^2(p)$, $p$ a positive integer) if $X \sim G\left( \alpha = \frac{p}{2}, \beta = 2 \right)$, i.e. the pdf of $X$ is $$f_{X}(x) = \begin{cases}  \frac{1}{\Gamma\left( \frac{p}{2} \right)2^{p/2}}x^{p/2 - 1}e^{-x/2} \quad x > 0 \\ 0 \quad \text{otherwise}  \end{cases}$$



>[!t] Expected value and variance
>If $X \sim \chi^2(p)$, then
>1. $\mathbb{E}(X) = 2 \cdot \frac{p}{2} = p$
>2. $V(X) = 2^2 \cdot \frac{p}{2} = 2p$

>[!e] Example
>Find $\mathbb{E}(Z^{2n})$.
> We have $\mathbb{E}(Z^{2n}) = \mathbb{E}((Z^2)^n) = \mathbb{E}(X^n)$ where $X = Z^2 \sim G\left( \frac{1}{2}, 2 \right)$
> and $$\mathbb{E}(X^n) = \int_{0}^{\infty} x^n f_{X}(x) \, dx$$
> $$=\int_{0}^{\infty} x^n \cdot \frac{1}{\sqrt{ 2\pi }}x^{-1/2}e^{-x/2} \, dx $$
> $$=\frac{1}{\sqrt{ 2\pi }} \int_{0}^{\infty} x^{n-1/2} e^{-x/2} \, dx $$
> $$=\frac{1}{\sqrt{ 2\pi }} \cdot \frac{\Gamma\left( n + \frac{1}{2} \right)}{\left( \frac{1}{2} \right)^{n+1/2}}$$
> $$=\frac{2^n}{\sqrt{ \pi }}\Gamma\left( n+\frac{1}{2} \right)$$


---
#### Midterm Review
1. Consider the jumbled up REDDDIITT. What is the probability that in any shuffling of the letters the two T's are together?
There are $\frac{9!}{3!2!2!}$ unique placements up to the same letters.
There are 8 possible positions of the two T's. For the other 7 letters, there are $\frac{7!}{3!2!}$ ways of numbering them up to the same letters. So the probability of this event happening is $$\frac{8 \cdot \frac{7!}{3!2!}}{\frac{9!}{3!2!2!}}$$
What if we specify that the two T's are together and only two of the three D's are together? (this would be very complicated)

Side note: The most probable/most likely outcome is the outcome with the highest probability, not the expected value.
<br>

2. Consider $X$ with mgf $\frac{e^{-2t}}{8} (1 + e^{2t})^3$. What is the distribution of $X$?
$$\frac{e^{-2t}}{8} (1 + e^{2t})^3 = e^{-2t}\left( \frac{1}{2} + \frac{1}{2}e^{2t} \right)^3$$
$X = -2 + 2Y$ where $Y \sim B\left( 3, \frac{1}{2} \right)$

3. Let $X \sim B\left( 4, \frac{1}{5} \right)$, $X  =$ number of heads in 4 tosses. If head, triple your current fortune (10). If tail, half your current fortune. Let $Y$ be your fortune after the 4 tosses. Find the expected fortune.
$$Y = 10 \cdot 3^X \cdot \left(\frac{1}{2}\right)^{4-X} = \frac{10}{16}\cdot 6^X$$
$$\mathbb{E}(Y) = \frac{10}{16} \mathbb{E}(6^X) = \frac{10}{16} \mathbb{E}(e^{\ln(6)X}) = \frac{10}{16}m_{X}(\ln(6))$$
$$=\frac{10}{16}\left( \frac{4}{5} + \frac{1}{5}e^{\ln(6)} \right)^4=10$$

4. Consider the probability function $p_{Y}(n) = (\frac{1}{2})^{n+1}$. It isn't a geometric distribution. But consider $X = Y + 1$. We see that $X \in \{ 1,2,3,\dots \}$ and $P(X = k) = P(Y = k-1)$.