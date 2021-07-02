##### **1. Binomial distribution**

* ***Problem:*** *Toss a coin $n$ times, let $X=1$ represents "obtain a head" and $X=0$ represents "obtain a tail" where $\mathbf{Pr}(X=1)=p$. The probability of obtaining $x$ times $X=1$ is:*
$$
\begin{align}
f(x\ |\ p,n)=\begin{cases}\begin{pmatrix}n\\x\end{pmatrix}p^x(1-p)^{n-x} \ \ \ \ &\text{for } x=0,1,2,...,n,\\ 0 \ \ \ \ &\text{otherwise.}\end{cases}
\end{align}\tag1
$$

##### **2. Poisson distribution**

* ***Problem:*** *A store serves $5.1$ customers per hour on average. We want to find the distribution of the number of customers in the specific period of time.*
    
    * We can use binomial distribution, but first at all, we have to scale the number of customers per hour to the range $[0,1]$. For example, we can use:
        * per minute ($n=60$): $p=\displaystyle\frac{5.1}{60}=0.085$
        * per second ($n=3600$): $p=\displaystyle\frac{5.1}{3600}=0.001417$.
    And now we can use formula $(1)$ to estimate the number of customers per hour/minute/second.
    * But in Poisson distribution, we have a new approach. Consider:
    $$
    \begin{align}
    \displaystyle\frac{f(x+1)}{f(x)}&=\displaystyle\frac{\begin{pmatrix}n\\x+1\end{pmatrix}p^{x+1}(1-p)^{n-x-1}}{\begin{pmatrix}n\\x\end{pmatrix}p^x(1-p)^{n-x}}\\
    &=\displaystyle\frac{(n-x)p}{(x+1)(1-p)}.
    \end{align}\tag2
    $$
    * If we scale $p$ into small periods ($ms$, $\mu s$, ...), then $p\to0^+$ and $n>>x$. So we have some approximations $n-x\approx n$, $1-p\approx1$ and:
    
    $$
    \begin{align}
    \displaystyle\frac{f(x+1)}{f(x)}&\approx\displaystyle\frac{np}{x+1}\\
    \Rightarrow f(x+1)&\approx f(x)\displaystyle\frac{\lambda}{x+1}\ \ \ \ \text{where }\lambda=np\\
    &=f(0)\displaystyle\frac{\lambda^{x+1}}{(x+1)!}\\
    \Rightarrow f(x)&=f(0)\displaystyle\frac{\lambda^{x}}{x!}.\tag3
    \end{align}
    $$
    * Because $f(x)$ is a distribution, we have:
    $$
    \begin{align}
    \sum_{x=0}^{+\infty}f(x)&=1\\
    \Leftrightarrow f(0)\sum_{x=0}^{+\infty}\frac{\lambda^{x}}{x!}&=1\\
    f(0)&=\displaystyle\frac{1}{\sum_{x=0}^{+\infty}\displaystyle\frac{\lambda^{x}}{x!}}.\tag4
    \end{align}
$$
    * By <a href='https://en.wikipedia.org/wiki/Taylor_series' style='color:green'>Taylor approximation</a>, we can obtain $f(0)=\displaystyle\frac{1}{e^\lambda}=e^{\lambda}$.
    
* ***Definition:*** *The Poisson distribution of random variable $x$ with the mean $\lambda>0$ takes the form:*
$$
\begin{align}
\begin{cases}
f(x\ |\ \lambda)=\displaystyle\frac{e^{-\lambda}\lambda^x}{x!} \ \ \ \ &\text{for } x=0,1,2,...,n,\\ 0 \ \ \ \ &\text{otherwise.}\end{cases}
\end{align}\tag5
$$

* From our approach, we have a approximation between **Binomial** and **Poisson**:

$$
\displaystyle\lim_{n\to+\infty}\begin{pmatrix}n\\x\end{pmatrix}p^x(1-p)^{n-x}=\displaystyle\frac{e^{-np}(np)^x}{x!}\tag6
$$

​	for all $x=0,1,...$

##### **Reference:**

* Chapter 5.4 | Probability and Statistics (Fourth Edition) | Morris H. DeGroot & Mark J. Schervish.