* In this post, we discuss about **Bayes' theorem** for Gaussian variables. With
  $$
  \mathbf{x}=
  \begin{pmatrix}
  \mathbf{x}_a\\\mathbf{x}_b\tag1
  \end{pmatrix},
  $$
  given $p(\mathbf{x}_a)$ and a Gaussian conditional distribution $p(\mathbf{x}_b|\mathbf{x}_a)$, we wish to find $p(\mathbf{x}_a,\mathbf{x}_b)=p(\mathbf{x})$. As show in <a href='https://khoatranrb.github.io/2020/11/30/ml&pr-8' style='color:green'>MLPR8</a>, $p(\mathbf{x}_b|\mathbf{x}_a)$ has mean is a linear function of $\mathbf{x}_a$:
  $$
  \begin{align}
  p(\mathbf{x}_a)&=\mathcal{N}(\mathbf{x}_a\mathbf{|\mu,\Lambda}^{-1})\tag2\\
  p(\mathbf{x}_b\mathbf{|x}_a)&=\mathcal{N}(\mathbf{x}_b\mathbf{|Ax}_a+\mathbf{b,L}^{-1})\tag3.
  \end{align}.
  $$

* We consider the joint distribution:
  $$
  p(\mathbf{x})=p(\mathbf{x}_a)p(\mathbf{x}_b\mathbf{|x}_a)\tag4.
  $$
  Take the log, we obtain:
  $$
  \begin{align}
  \ln p(\mathbf{x})&=\ln p(\mathbf{x}_a)+p(\mathbf{x}_b\mathbf{|x}_a)\\
  &=-\frac{1}{2}(\mathbf{x}_a-\mu)^\top\mathbf{\Lambda}(\mathbf{x}_a-\mu)-\frac{1}{2}(\mathbf{x}_b-\mathbf{Ax}_a-\mathbf{b})^\top\mathbf{L}(\mathbf{x}_b-\mathbf{Ax}_a-\mathbf{b})+\text{const}\tag5.
  \end{align}
  $$

* In order to find covariance matrix of $p(\mathbf{x})$, we rewrite the $(5)$ as a quadratic function:
  $$
  \begin{align}
  &-\frac{1}{2}(\mathbf{x}_a-\mu)^\top\mathbf{\Lambda}(\mathbf{x}_a-\mu)-\frac{1}{2}(\mathbf{x}_b-\mathbf{Ax}_a-\mathbf{b})^\top\mathbf{L}(\mathbf{x}_b-\mathbf{Ax}_a-\mathbf{b})\\
  &=-\frac{1}{2}\mathbf{x}_a^\top\mathbf{\Lambda x}_a-\frac{1}{2}\mathbf{x}_b^\top \mathbf{Lx}_b-\frac{1}{2}\mathbf{x}_a^\top \mathbf{A^\top LAx}_a+\frac{1}{2}\mathbf{x}_b^\top \mathbf{LAx}_a+\frac{1}{2}\mathbf{x}_a^\top\mathbf{A^\top Lx}_b+\text{const}\tag6\\
  &=-\frac{1}{2}\mathbf{x}_a^\top\mathbf{(\Lambda+A^\top LA) x}_a-\frac{1}{2}\mathbf{x}_b^\top \mathbf{Lx}_b+\frac{1}{2}\mathbf{x}_b^\top\mathbf{ LAx}_a+\frac{1}{2}\mathbf{x}_a^\top\mathbf{A^\top Ly}+\text{const}\tag7\\
  &=-\frac{1}{2}\begin{pmatrix}\mathbf{x\\y}\end{pmatrix}^\top\begin{pmatrix}\mathbf{\Lambda}+\mathbf{A^\top LA}&-\mathbf{A^\top L}\\-\mathbf{LA}&\mathbf{L}\end{pmatrix}\begin{pmatrix}\mathbf{x\\y}\end{pmatrix}\tag9.
  \end{align}
  $$
  
* Finally, we get:
  $$
  \begin{align}
  \mathbf{E}[\mathbf{x}]&=\begin{pmatrix}\mu\\ \mathbf{A\mu+b}\end{pmatrix}\tag{10}\\
  \text{cov}[\mathbf{x}]&=\begin{pmatrix}\mathbf{\Lambda}+\mathbf{A^\top LA}&-\mathbf{A^\top L}\\-\mathbf{LA}&\mathbf{L}\end{pmatrix}^{-1}\tag{11}.
  \end{align}
  $$

#### Reference:

* Pattern Recognition and Machine Learning | C.M. Bishop.