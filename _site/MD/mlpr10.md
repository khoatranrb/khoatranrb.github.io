* In this post, we discuss about Linear Regression in statistic view, thereby answer why we should use Mean Square Error as a loss function.
  
* We suppose that target variable $t$ is given by a deterministic function $y(\mathbf{x},\mathbf{w})$ with additive Gaussian noise $\epsilon$:
  $$
  t=y(\mathbf{x},\mathbf{w})+\epsilon\tag1
  $$
  where $\epsilon$ is a zero mean Gaussian random variable with precision $\beta$. We can write:
  $$
  p(t|\mathbf{x},\mathbf{w},\beta)=\mathcal{N}(t|y(\mathbf{x},\mathbf{w}),\beta^{-1})\tag2.
  $$

* Now consider a data set of inputs $\mathbf{X}=\{\mathbf{x}_1,...,\mathbf{x}_N\}$ with corresponding target values $t_1,...t_N$. We have:
  $$
  p(\mathbf{t}|\mathbf{X},\mathbf{w},\beta)=\prod_{n=1}^N\mathcal{N}(t_n|\mathbf{x}_n\mathbf{w},\beta^{-1})\tag3.
  $$

* We wish to maximize $p(\mathbf{t}|\mathbf{X},\mathbf{w},\beta)$, synonymous with maximize $\ln p(t|\mathbf{X},\mathbf{w},\beta)$:
  $$
  \begin{align}
  \ln p(t|\mathbf{X},\mathbf{w},\beta)&=\sum_{n=1}^N\ln\mathcal{N}(t_n|\mathbf{w}^\top\phi(\mathbf{x}_n),\beta^{-1})\tag4\\
  &=\sum_{n=1}^N\ln\frac{1}{\sqrt{2\pi\beta^{-1}}}\exp({-\frac{(t_n-\mathbf{w}^\top\phi(\mathbf{x}_n))^2}{2\beta^{-1}}})\tag5\\
  &=N\ln\frac{1}{\sqrt{2\pi\beta^{-1}}}-\beta E_D(\mathbf{w})\tag6
  \end{align}
  $$
  where
  $$
  E_D(\mathbf{w})=\frac{1}{2}\sum_{n=1}^N(t_n-\mathbf{w}^\top\phi(\mathbf{x}_n))^2,\tag7
  $$

  we must minimize $E_D(\mathbf{w})$ - the MSE loss. 

  And we are done!

#### Reference:

* Pattern Recognition and Machine Learning | C.M. Bishop.