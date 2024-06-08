Format: 3 hr, 50 marks, 6 questions. The first question is answer-only (5 marks).

Joke question: What is the probability that during a 30-minute lecture that nobody pull out their cellphone???? (answer: 0)

The five long-answer questions are weighted more heavily on Chapters 4-5 (roughly 60% Ch. 4-5 vs. 40% Ch. 1-3, but the professor is not liable for the exact ratio).


>[!e] Quiz 3 Question 1
$$f(x) = \begin{cases}  Cx^2e^{2x} \quad x < 0 \\ 0 \quad \text{otherwise}  \end{cases}$$
We observe that $X$ can't possibly be a gamma distribution because the support doesn't match that of a gamma. $X = -Y$ where $$f_{Y}(y) = \begin{cases}  Cy^2e^{-2y} \quad y > 0 \\ 0 \quad \text{otherwise}  \end{cases}$$
so $Y \sim \Gamma\left( 3, \frac{1}{2} \right)$.
Therefore $C$ is uniquely determined: $$C = \frac{1}{\Gamma(3) \left( \frac{1}{2} \right)^3} = 4$$
So $$\mathbb{E}(X^3) = \mathbb{E}((-Y)^3) = -\mathbb{E}(Y^3)$$
and $$\mathbb{E}(Y^3) = \int_{0}^{\infty} 4y^2e^{-2y}\cdot y^3 \, dy $$
$$=4 \cdot \int_{0}^{\infty} y^5e^{-2y} \, dy $$
$$=4 \cdot \frac{1}{2^6}\Gamma(6)$$
$$=\frac{5!}{2^4}$$

Toward the beginning of the course, we had very concrete problems with experiments that have certain distributions. Then we started to study distributions by starting with a cumulative density distribution with no experiment in mind for now. In Math 324 and higher courses you can prove convergence of random variables, and you'll see things better then.

>[!e] Our go-to jpdf, revisited
$$f(x,y) = \begin{cases}  6x \quad 0 < x < y < 1 \\ 0 \quad \text{otherwise}  \end{cases}$$
![[desmos-graph-7.png]]
We computed that $$f(x | Y = y) = \begin{cases}  \frac{2}{y^2}x \quad 0 < x < y \\ 0 \quad \text{otherwise}  \end{cases}$$
In case you don't see why $X \sim Y  \cdot Beta(2,1)$ we can rewrite it as $$f_{U}(u) = \begin{cases}  \frac{2u}{a^2} \quad 0 < u < a \\ 0\quad \text{otherwise}  \end{cases}$$
Consider $W = \frac{1}{a}U$. Then by change of variable, $$f_{W}(w) = af_{U}(aw)$$
$$= \begin{cases}  \frac{a \cdot 2aw}{a^2} \quad 0 < a w < 1 \\ 0 \quad \text{otherwise}  \end{cases}$$
$$=\begin{cases}  2w \quad 0 < w < 1  \end{cases}$$

---
>[!e] Midterm questions—short answer
>Suppose that there are 6 people sitting in a row, and two certain people cannot sit next to each other. There are $6!$ total possibilities for 6 people to sit, and if two particular people can't sit together then we remove $5\cdot 2 \cdot 4!$.
><br>
>How many times is digit 0 listed betwee 99 and 999?
>There are these configurations:
>- X0X, XX0 There are $9 \cdot 9 \cdot 2$ choices
>- X00 (0X0 and 00X are not valid because we need a 3-digit number). There are $2 \cdot 9$ such choices.
>answer: $\frac{2 \cdot 9(9+1)}{180}$
><br>
>
>$(\sqrt{ x } + 3x^2)^4$
$=(\underbrace{ x^{1/2} }_{ a } + \underbrace{ 3x^2 }_{ b })^4$
The only way to get $x^5$ is the $a^2b^2$ term. The term is $C_{2}^4 (x^{1/2})^2(3x^2)^2$ which has a coefficient of $54$.

>[!e] Midterm review—long-answer
>1. Three balls are randomly thrown into 3 box. (For now, assume that the balls are not identical. This gives $3^3 = 27$ choices.) What is the probability that one box is empty?
We have $C_{1}^3 = 3$ ways to choose the empty box. The other two boxes either have 1 ball or 2 balls respectively (that makes $2$), and there are $3$ ways of distributing the three balls in two boxes. So we hvae $3 \cdot 6$ ways out of $3^3$ ways, and the probability is $\frac{3\cdot 6}{3^3} = \frac{2}{3}$.
>2. How many permutations of the letters in STATIC start with a vowel?
In the word STATIC, there are $2 \times \frac{5!}{2!}=120$ ways to permute the letters such that $A$ or $I$ is the first letter.
>3. A plane has equal probability of being in $R_{1},R_{2},R_{3}$
Let $p_{i}$ be the probability to find the plain in $R_{i}$ given that the plane is actually in $R_{i}$ (since the probability of finding the plane in $R_{i}$ if it isn't in $R_{i}$ is $0$).
Let $B$ be "search in $R_{2}$ unsuccessful."
$$P(B) = P(B \cap R_{1}) + P(B  \cap R_{2}) + P(B \cap R_{3})$$
$$=P(B | R_{1}) \cdot \frac{1}{3}  + P(B |R_{2})\cdot \frac{1}{3} + P(B | R_{3}) \cdot \frac{1}{3}$$
$P(B|R_{1})=P(B|R_{3}) = 1$ because you can't find the plane in $R_{2}$ if it's in $R_{1}$ or $R_{3}$.
$P(B | R_{2}) = 1-p_{2}$
Hence
$$P(B)=\frac{1}{3}(3-p_{2})$$
Then we have $$P(R_{3} | B) = P(B | R_{3}) \cdot \frac{P(R_{3})}{P(B)} = \frac{1}{3-p_{2}}$$
>4. Urn 1 has 4 Reds and 6 Blues. Choose a ball and place it in Urn 2 which originally has $X$ Reds and 3 Blues. Then, choose a 2nd ball from Urn 2. The probability of 2nd ball being Red is 
Let $C$ be "2nd ball Red", $R$ be "1st ball Red", $B$ be "1st ball Blue." Then $$P(C) = P(C \cap B) + P(C \cap R)$$
$$=P(C | B) P(B) + P(C | R) P(R)$$
$$=\frac{x}{x+4}\cdot \frac{6}{10} + \frac{x+1}{x+4}\cdot \frac{4}{10} = \frac{2}{5}$$
>5. $m_{X}(t) = e^{3e^{2t}+t-3}$
$=e^{3(e^{2t}-1)\cdot e^t}$
So $X \sim 2Y+1$ where $Y \sim P(\lambda = 3)$.
Therefore $\mathbb{E}(X) = 2\mathbb{E}(Y) + 1 = 7$, and $V(X) = 2^2 V(Y) = 12$.
$P(X = 0) = P\left( Y = -\frac{1}{2} \right) = 0$.
$P(X = 3) = P(Y =1) = e^{-3} \cdot \frac{3^1}{1!}= 3e^{-3}$





---
The professor will not discuss curving up with anybody, but he will never curve down.

---
##### Miscellaneous questions
>[!e] 5.42 from the textbook
Let $Y \sim P(\lambda)$ where $\lambda$ is also a variable with $\lambda \sim Exponential(1)$.
The distribution of $Y$ is given as a conditional distribution, and that of $\lambda$ is a marginal distribution.
Your joint distribution looks like vertical sticks at $0, 1, 2,\dots$ (sorry this is hard to draw so I won't do that)
Approach: multiply conditional of $Y$ by marginal of $\lambda$ to get the joint, then find the marginal of $Y$ by integration.
$$f(y, \lambda) = f(y | \lambda) \cdot f(\lambda)$$
$$=P(Y = y|\lambda) \cdot f(\lambda)$$
$$=\frac{e^{-\lambda}\lambda^y}{y!}\cdot e^{-\lambda}$$
$$=\frac{e^{-2\lambda}\lambda^y}{y!}\quad \lambda > 0, y \in \mathbb{N}$$
So for $y \in \mathbb{N}$,
$$P(Y = y) = \int_{0}^{\infty} f(y, \lambda) \, d\lambda $$
$$=\frac{1}{y!}\int_{0}^{\infty} e^{-2\lambda} \cdot \lambda^y \, d\lambda$$
$$\cancel{ \frac{1}{y!} }\cdot\left( \frac{1}{2}\right)^{y+1} \cdot \cancel{ \Gamma(y+1) }$$
so $Y = X - 1$ where $X \sim G\left( \frac{1}{2} \right)$
Now we know
$$\mathbb{E}(Y) = \mathbb{E}(X) - 1 = 1$$
$$V(Y) = V(X) = 2(2-1) = 2$$
 

>[!e] Quiz 4 question
$$f(x,y) = \begin{cases}  \frac{1}{8x}e^{- \frac{x}{2}} \quad 0 < y < 2x^2, x  >0 \\ 0 \quad \text{otherwise}  \end{cases}$$
Support:
![[desmos-graph-15.png]]
Then $$\mathbb{E}(Y) = \int_{0}^{\infty} \int_{0}^{2x^2} y \cdot \frac{1}{8x}e^{-x/2} \, dy  \, dx $$
$$=\int_{0}^{\infty} \frac{1}{8x}e^{-x/2}\underbrace{ \left( \int_{0}^{2x^2} y \, dy  \right) }_{ 2x^4 } \, dx $$
$$=\int_{0}^{\infty} \frac{x^3}{4}e^{-x/2} \, dx $$
$$=\frac{1}{4}\Gamma(4)\cdot 2^4$$
$$=24$$
Exercise: Find $\mathbb{E}(Y)$ with $\mathbb{E}(\mathbb{E}(Y|X))$.
$$f_{X}(x) = \int_{\mathbb{R}^2} f(x,y) \, dy $$
$$=\begin{cases}  \int_{0}^{2x^2} \frac{1}{8x}e^{-x/2} \, dy \quad x >0 \\0 \quad \text{otherwise}   \end{cases}$$
$$=\begin{cases}  \frac{x}{4}e^{-x/2} \quad x > 0 \\ 0 \quad \text{otherwise}  \end{cases}$$

>[!e] One of the past quiz questions:
$$f(x) = \begin{cases}  \frac{cx^{3/2}}{\sqrt{ 1-x }}  \quad 0 < x < 1 \\0 \quad \text{otherwise}\end{cases}$$
$X\sim Beta\left( \alpha = \frac{5}{2} , \beta = \frac{1}{2} \right)$


>[!e] 5.13 from textbook
$$f(x,y) = \begin{cases}  30xy^2 \quad x-1 \leq y \leq 1-x, \; 0 < x \leq 1 \\ 0 \quad \text{otherwise}  \end{cases}$$
Support:
![[desmos-graph-16.png]]
Looking at the shape of this thing, if we're integrating over the entire domain, it's best to parametrize $y$ in terms of $x$; otherwise we need to split the domain to integrate.
Finding $F\left( \frac{1}{2}, \frac{1}{2} \right)$:
$$F\left( \frac{1}{2}, \frac{1}{2} \right) = P\left( X \leq \frac{1}{2}, Y \leq \frac{1}{2} \right)$$
We are integrating over this region (the region where all three colors overlap):
![[desmos-graph-17.png]]
$$D = \begin{cases}  0 \leq x \leq  \frac{1}{2}\\ x-1 \leq y \leq \frac{1}{2}  \end{cases}$$
so $$F\left( \frac{1}{2}, \frac{1}{2} \right) = P\left( X \leq \frac{1}{2}, Y \leq \frac{1}{2} \right) = \int_{0}^{1/2} \int_{x-1}^{1/2} 30xy^2 \, dy  \, dx $$
<br>
Continuing the same thing, what is $P\left( X \leq \frac{1}{2} | Y = \frac{1}{2} \right)$?
Too bad the professor can't reprint the exam, this question is on the exam 🤣
This probability must must be $1$ because $0 \leq X \leq \frac{1}{2}$ is the entire support of $X$ given $Y$.
If you're not convinced:
$$f\left( x|Y = \frac{1}{2} \right) = \frac{f\left( x, \frac{1}{2} \right)}{f_{Y}\left( \frac{1}{2} \right)}$$

>[!e] Discussion about adding geometrically distributed random variables
Let $X_{1} \sim G(p_{1})$, $X_{2} \sim G(p_{2})$. Suppose $X_{1}, X_{2}$  are independent.
Then for $X = X_{1} + X_{2}$, $$m_{X}(t) = m_{X_{1}}(t) m_{X_{2}}(t)$$
$$\underbrace{ \frac{p_{1}e^t}{1-(1-p_{1})e^t} }_{ t < -\ln(1-p_{1}) }\cdot\underbrace{ \frac{p_{2}e^t}{1-(1-p_{2})e^t} }_{ t < -\ln(1-p_{2}) }$$
For sure that doesn't look like a geometric lol. But more convincingly, the domain of $X$ is $\{ 2,3,\dots \}$ and therefore cannot be a geometric distribution.




>[!e] Textbook question 5.157
$Y \sim P(\lambda)$ given $\lambda$, $\lambda \sim \Gamma(\alpha, \beta)$.
Again, the support are infinite vertical sticks sticking up from $0, 1,2,\dots$
$$f(y, \lambda) = P(Y  = y | \lambda) \cdot f(\lambda)$$
$$=\begin{cases}  \frac{e^{-\lambda}\lambda^y}{y!} \cdot \frac{1}{\Gamma(\alpha)\beta^\alpha}\lambda^{\alpha-1}e^{-\lambda/\beta} \quad y \in \mathbb{N}, \lambda >0 \\ 0 \quad \text{otherwise} \end{cases}$$
$$P(Y = y) = \int_{0}^{\infty} f(y, \lambda) \, d\lambda $$
$$=\frac{1}{\Gamma(\alpha)\beta^\alpha \cdot y!} \int_{0}^{\infty} e^{-\lambda\left( 1+\frac{1}{\beta}  \right)} \lambda^{y + \alpha - 1} \, d\lambda$$
Recalling that $\int_{0}^{\infty} t^a e^{-bt} \, dt = \frac{1}{b^{a+1}}\Gamma(a + 1)$:
$$p(Y = y) = \frac{1}{\Gamma(\alpha)\beta^\alpha \cdot y!} \cdot \frac{1}{\left( \lambda\left( 1+\frac{1}{\beta} \right) \right)^{y+\alpha}}\Gamma(y+\alpha) $$
$$=\frac{1}{\Gamma(\alpha) \cdot y!} \cdot \beta^y\left( \frac{1}{\lambda \cdot (\beta+1)} \right)^{y+\alpha}\Gamma(y+\alpha) $$


*Good luck to all!*