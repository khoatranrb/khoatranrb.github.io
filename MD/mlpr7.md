##### **1. Cross entropy**

* **Cross-entropy** is a measure the difference between two probability of distributions $p$ and $q$, denoted as:
  $$
  \mathbf{H}(p,q)=-\int p(x)\log q(x)\text{d}x
  $$

* **Cross-entropy** calculates the number of bits required to represent or transmit an average event from one distribution compared to another distribution. In formula $(1)$, $p(x)$ is the target distribution, $q(x)$ is the approximation of the target distribution.

* By Lagrange multiplier method, we can prove $\mathbf{H}(p,q)$ reaches the minimum value when $p(x)=q(x)$, it means:
  $$
  \begin{align}
  \min \mathbf{H}(p,q)&=\mathbf{H}(p,p)\\
  &=-\int p(x)\log p(x)\text{d}x=\H[p]\tag2
  \end{align}
  $$
  

**Note that:** In this blog, we denote:

  * **entropy** of $p(x)$ as $\H[p]$
  * **entropy** of $p(x ,y)$ as $\H[(x,y)]$
  * **cross entropy** of $p(x)$ and $q(x)$ as $\mathbf{H}(p,q)$.

##### **2. Kullback-Leibler divergence**

* **KL divergence** or **relative entropy** is a method to measure the *dissimilarity* of two probability distribution, denoted by $p$ and $q$. It is defined:
  $$
  \mathbf{KL}(p||q)=\int p(x)\log\frac{p(x)}{q(x)}\text{d}x\tag3.
  $$
In discrete domain, **KL divergence** is written as:
  $$
  \mathbf{KL}(p||q)=\sum_kp_k\log\frac{p_k}{q_k}\tag4
  $$
  
  
  Difference from cross-entropy, **KL divergence** is the average number of *extra* bits needed to encode data when we use distribution $q(x)$ instead of true distribution $p(x)$.
  
* We can rewrite:
  $$
  \mathbf{KL}(p||q)=\int p(x)\log p(x)\text{d}x-\int p(x)\log q(x)\text{d}x=-\H[p]+\mathbf{H}(p,q)\tag5
  $$

**Theorem 1:** $\mathbf{KL}(p||q)\ge0$ with equality iff $p=q$.

*Proof:*

​	To prove this, we use **Jensen's inequality** for a convex function:
$$
f(\sum_{i=1}^n\lambda_ix_i)\le\sum_{i=1}^n\lambda_if(x_i)\tag6
$$
​	where $\lambda_i\ge0$ and $\sum_i\lambda_i=1$.

​	We have:
$$
\begin{align}
-\mathbf{KL}(p||q)&=-\sum_kp(x_k)\log\frac{p(x_k)}{q(x_k)}=\sum_kp(x_k)\log\frac{q(x_k)}{p(x_k)}\tag7\\
&\le\log\sum_kp(x_k)\frac{q(x_k)}{p(x_k)}=\log\sum_kq(x_k)=\log1=0\tag8\\
\end{align}
$$

###### **2.1. Jensen-Shannon divergence**


* We can see that, both of **cross-entropy** and **KL divergence** are asymmetric. So, both of them cannot used as a measure for two distribution. So, **JS divergence** measure is built based on **KL divergence**:
  $$
  \mathbf{JS}(p||q)=\mathbf{KL}(p||\frac{p+q}{2})+\mathbf{KL}(q||\frac{p+q}{2})\tag9.
  $$

* **JS divergence** calculates the *dissimilarity* of two distribution $p$ and $q$  adopted the *dissimilarity* of $p$ vs $\frac{p+q}{2}$ and  $q$ vs $\frac{p+q}{2}$. If $p$ and $q$ are more match, **KL divergence** of both of $p$ and $q$ with $\frac{p+q}{2}$ are smaller and more close as 0.

* From $(1)$ and $(4)$, we can rewrite $(8)$ as:
  $$
  \begin{align}
  \mathbf{JS}(p||q)&=\mathbf{KL}(p||\frac{p+q}{2})+\mathbf{KL}(q||\frac{p+q}{2})\\
  &=-\H[p]+\mathbf{H}(p,\frac{p+q}{2})-\H[q]+\mathbf{H}(q,\frac{p+q}{2})\tag{10}\\
  &=-\H[p]-\int p(x)\log \frac{p(x)+q(x)}{2}\text{d}x-\H[q]-\int q(x)\log \frac{p(x)+q(x)}{2}\text{d}x\tag{11}\\
  &=-2\int\frac{p(x)+q(x)}{2}\log \frac{p(x)+q(x)}{2}\text{d}x-\H[p]-\H[q]\tag{12}\\
  &=2.\H[\frac{p+q}{2}]-\H[p]-\H[q]\tag{13}
  \end{align}
  $$

* Next, we prove **JS divergence** has upper limit. We start with:
  $$
  \begin{align}
  \mathbf{KL}(p||\frac{p+q}{2})=\int p(x)\log\frac{2p(x)}{p(x)+q(x)}\text{d}x\tag{14}
  \end{align}
  $$
  We have
  $$
  \frac{2p(x)}{p(x)+q(x)}\le2\tag{15}
  $$
  so
  $$
  \mathbf{KL}(p||\frac{p+q}{2})\le\log2\int p(x)\text{d}x=\log2\tag{16}.
  $$
  It is equal when $p_k(x)q_k(x)=0$ with all of $k$ values.
  
  Similarity, we have:
  $$
  \mathbf{KL}(q||\frac{p+q}{2})\le\log2\int q(x)\text{d}x=\log2\tag{17}.
  $$
  It is also equal when $p_k(x)q_k(x)=0$ with all of $k$ values.
  
  Then
  $$
  \mathbf{JS}(p||q)\le2\log2\tag{18}.
  $$
  

##### **Reference:**

* 2.8.2 | Machine Learning A Probabilistic Perspective | K.P. Murphy.
* <a href='https://ttic.uchicago.edu/~dmcallester/ttic101-07/lectures/jensen/jensen.pdf' style='color:green'>Jensen's inequality</a>.
* <a href='https://machinelearningmastery.com/cross-entropy-for-machine-learning/' style="color:green">Cross-entropy for machine learning | Machine Learning Mastery</a>.
* <a href='https://phamdinhkhanh.github.io/2020/07/25/GAN_Wasserstein.html#4-jensen-shannon' style='color:green'>Bài 44 - Model Wasserstein GAN (WGAN)</a>.