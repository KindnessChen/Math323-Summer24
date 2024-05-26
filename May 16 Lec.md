#### Beta distributions
Note that the **beta integral ** 
$$\int_{0}^{1} x^{\alpha-1}(1-x)^{\beta-1} \, dx = \frac{\Gamma(\alpha)\Gamma(\beta)}{\Gamma(\alpha + \beta)}$$

for $\alpha > 0$, $\beta > 0$.
>[!e] Example
> $$\int_{0}^{1} x^2(1-x)^3 \, dx $$
is a beta integral with $\alpha = 3, \beta = 4$. The integral is equal to $\frac{\Gamma(3)\Gamma(4)}{\Gamma(7)} = \frac{2!3!}{6!}$

>[!d] Definition: beta distribution
>The function $$f_{X}(x) = \begin{cases}  \frac{\Gamma(\alpha+\beta)}{\Gamma(\alpha)\Gamma(\beta)} x^{\alpha-1}(1-x)^{\beta-1}\quad x \in (0,1) \\ 0 \quad \text{otherwise}  \end{cases}$$
>is the pdf of the **beta distribution** with parameters $\alpha, \beta$. We write $X \sim Beta(\alpha, \beta)$ if $X$ has a beta distribution with parameters $\alpha, \beta$.

>[!r] Remark
>$U(0,1) = Beta(1,1)$

>[!t] Expected value and variance of beta distribution
>If $X \sim Beta (\alpha, \beta)$, then
>1. $\mathbb{E}(X) = \frac{\alpha}{\alpha + \beta}$
>2. $V(X) = \frac{\alpha \beta}{(\alpha+\beta)^2 (\alpha + \beta  + 1)}$
>>[!p] Proof
>>$$\mathbb{E}(X) = \frac{\Gamma(\alpha + \beta)}{\Gamma(\alpha) \Gamma(\beta)} \int_{0}^{1} x \cdot x^{\alpha - 1}(1-x)^{\beta-1} \, dx$$
>> $$\frac{\Gamma(\alpha + \beta)}{\Gamma(\alpha) \Gamma(\beta)} \int_{0}^{\infty} x^{\alpha }(1-x)^{\beta-1} \, dx $$
>> $$\frac{\Gamma(\alpha + \beta)}{\Gamma(\alpha) \Gamma(\beta)} \cdot \frac{\Gamma(\alpha + 1)\Gamma(\beta)}{\Gamma(\alpha+ \beta +1)}$$
>> $$=\frac{\alpha}{\alpha + \beta}$$
>> and $$\mathbb{E}(X^2) = \frac{\Gamma(\alpha + \beta)}{\Gamma(\alpha) \Gamma(\beta)} \int_{0}^{1} x^2 \cdot x^{\alpha - 1}(1-x)^{\beta-1} \, dx$$
>> $$=\frac{\Gamma(\alpha + \beta)}{\Gamma(\alpha) \Gamma(\beta)} \int_{0}^{1} x^{\alpha +1}(1-x)^{\beta-1} \, dx$$
>> $$\frac{\Gamma(\alpha + \beta)}{\Gamma(\alpha) \Gamma(\beta)} \cdot \frac{\Gamma(\alpha + 2)\Gamma(\beta)}{\Gamma(\alpha+ \beta +2)}$$
>> $$=\frac{\alpha(\alpha + 1)}{(\alpha + \beta + 1)(\alpha + \beta)}$$
>> So $$V(X) = \mathbb{E}(X^2) - (\mathbb{E}(X))^2$$
>> $$=\frac{\alpha(\alpha + 1)}{(\alpha + \beta + 1)(\alpha + \beta)} - \left(\frac{\alpha}{\alpha + \beta}\right)^2$$


---
#### Moment generating functions of pdfs
You know full well that this is just the Laplace transform of the pdf!
>[!d] Definition: Moment generating function of a pdf
>For a pdf $f_{X}$,
> $$m_{X}(t) = \mathbb{E}(e^{tx})$$
> $$=\int_{-\infty}^{\infty} e^{tx}f_{X}(x) \, dx $$

>[!t] Properties of the mgf
>1. $m_{X}(0) = 1$
>2. Domain of $m_{X}$ is an interval
>3. If the domain of $m_{X}$ contains an interval centered at $t=0$, then $$\frac{d^n}{dt^n}(m_{X}(t)) | _{t=0} = \mathbb{E}(X^n)$$

Also recall this property:
>[!t] Mgf of a linear transformation of a (continuous random) variable
>If $X = aY + b$ then $$m_{X}(t) = e^{bt}m_{Y}(at)$$


Let's calculate some mgfs!
##### Uniform
$X = (b-a) Y + a$, where $Y \sim U(0,1)$.
The mgf of $Y$ is
$$m_{Y}(s) = \mathbb{E}(e^{sy})$$
$$=\int_{0}^{1} e^{sy} \, dy $$
$$=\begin{cases}  1 \quad s = 0 \\
\frac{1}{s}(e^s - 1) \quad s \neq 0  \end{cases}$$
So the mgf of $X$ is $$m_{X}(t) = e^{at}m_{Y}((b-a)(t))$$
$$=\begin{cases}  1 \quad t = 0 \\  \frac{e^{at}  \cdot e^{(b-a)t} - 1}{(b-a)t}  \quad t \neq 0 \end{cases}$$

##### Normal
Let $X \sim N(\mu , \sigma^2)$
so $X = \sigma Z + \mu$ where $Z \sim N(0, 1)$. So $m_{X}(t) = e^{\mu t}m_{Z}(\sigma t)$
$$m_{Z}(s) = \int_{-\infty}^{\infty} e^{sz}f_{Z}(z) \, dz $$
$$=\int_{-\infty}^{\infty} e^{sz} \cdot \frac{1}{\sqrt{ 2\pi }} e^{-z^2/2} \, dx $$
$$=\frac{1}{\sqrt{ 2\pi }} \int_{-\infty}^{\infty} e^{-\frac{1}{2} \cdot [z^2 - 2sz]}  \, dx $$
Completing the square:
$$=\frac{1}{\sqrt{ 2\pi }} \int_{-\infty}^{\infty} e^{-\frac{1}{2} \cdot [(z-s)^2 - s^2]}\, dx$$
$$= \frac{e^{1/2 \cdot s^2}}{\sqrt{ 2\pi }} \int_{-\infty}^{\infty} e^{-1/2 (z-s)^2} \, dz  $$
Make change of variable $z-s = u$:
$$=\frac{e^{1/2 \cdot s^2}}{\sqrt{ 2\pi }}\underbrace{  \int_{-\infty}^{\infty} e^{-1/2 u^2} \, du }_{ =1 }$$
$$=e^{\frac{1}{2}s^2}$$

#### Gamma
$X \sim \Gamma(\alpha, \beta)$
$$m_{X}(t) = \int_{0}^{\infty} e^{tx}f_{X}(x) \, dx $$
$$=\frac{1}{\Gamma(\alpha)\beta^\alpha} \int_{0}^{\infty} e^{tx}x^{\alpha-1}e^{\frac{t}{\beta}} \, dx $$
$$=\frac{1}{\Gamma(\alpha)\beta^\alpha}  \int_{0}^{\infty} x^ {\alpha-1} e^{-x\left( \frac{1}{\beta}-t \right)} \, dx $$
Let $a = \alpha - 1$, $b = \frac{1}{\beta} - t =\frac{1-\beta t}{\beta}$.
We need $1-\beta t > 0$ (i.e. $t < \frac{1}{\beta}$) for the integral to converge.
$$=\frac{1}{\Gamma(\alpha)\beta^\alpha} \frac{\Gamma(\alpha)}{\left( \frac{1-\beta t}{\beta} \right)^\alpha} $$
$$=\frac{1}{(1-\beta t)^\alpha}, \quad t < \frac{1}{\beta}$$
