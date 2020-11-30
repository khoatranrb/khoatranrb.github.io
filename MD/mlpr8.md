* Consider two sets of variables are jointly Gaussian, then, the conditional distribution of one set conditioned on the other is again Gaussian.

* Suppose $\mathbf{x}$ is a $D$-dimensional vector with Gaussian distribution $\mathcal{N(\mathbf{x|\mu,\Sigma})}$. We split $\mathbf{x}$ into two parts: $\mathbf{x}_a$ and $\mathbf{x}_b$ where $\mathbf{x}_a$ takes first $M$ components of $\mathbf{x}$ and $\mathbf{x}_b$ takes $D-M$ remaining components.
  $$
  \mathbf{x}=
  \begin{pmatrix}
  \mathbf{x}_a\\\mathbf{x}_b\tag1
  \end{pmatrix}.
  $$

* We now define the mean of $\mathbf{x}$:
  $$
  \mathbf{\mu}=
  \begin{pmatrix}
  \mathbf{\mu}_a\\\mathbf{\mu}_b\tag2
  \end{pmatrix}
  $$
  and the covariance matrix of $\mathbf{x}$:
  $$
  \mathbf{\Sigma}=
  \begin{pmatrix}
  \mathbf{\Sigma}_{aa}&\mathbf{\Sigma}_{ab}\\\mathbf{\Sigma}_{ba}&\mathbf{\Sigma}_{bb}\tag3.
  \end{pmatrix}.
  $$
  In there, $\mathbf{\Sigma}$, $\mathbf{\Sigma}_{aa}$ and $\mathbf{\Sigma}_{bb}$ are symmetric and $\mathbf{\Sigma}_{ab}=\mathbf{\Sigma}_{ba}^\top$.

* We now define *precision matrix* takes a form:
  $$
  \mathbf{\Lambda} = \mathbf{\Sigma}^{-1}\tag4.
  $$
  
  Because $\mathbf{\Sigma}$ is symmetric, $\mathbf{\Lambda}$ also is symmetric $(\text{Appendix1})$. So we can rewrite this matrix as follows:
  $$
  \mathbf{\Lambda}=
  \begin{pmatrix}
  \mathbf{\Lambda}_{aa}&\mathbf{\Lambda}_{ab}\\
  \mathbf{\Lambda}_{ba}&\mathbf{\Lambda}_{bb}.
  \end{pmatrix}\tag5
  $$
  where $\mathbf{\Lambda}$, $\mathbf{\Lambda}_{aa}$ and $\mathbf{\Lambda}_{bb}$ are symmetric and $\mathbf{\Lambda}_{ab}=\mathbf{\Lambda}_{ba}^\top$.
  
  **Note that:** $\mathbf{\Lambda}_{aa}$ is not the invert of $\mathbf{\Sigma}_{aa}$, similar to $\mathbf{\Lambda}_{bb}$. We will discuss about it later.

* Now we discuss about the conditional distribution $p(\mathbf{x}_a|\mathbf{x}_b)$, consider $\mathbf{x}_b$ is the observed value. We start form the joint distribution $p(\mathbf{x})=p(\mathbf{x}_a,\mathbf{x}_b)$. To explore it, we consider the quadratic form of Gaussian distribution (as mentioned in) combine with the partitioning $(3)$ and $(5)$:
  $$
  \begin{align}
  -\frac{1}{2}(\mathbf{x-\mu})^\top\mathbf{\Sigma}^{-1}(\mathbf{x}-\mu)&=-\frac{1}{2}(\mathbf{x}_a-\mu_a)^\top\mathbf{\Lambda}_{aa}(\mathbf{x}_a-\mu_a)\\
  &\ \ \ \ -\frac{1}{2}(\mathbf{x}_a-\mu_a)^\top\mathbf{\Lambda}_{ab}(\mathbf{x}_b-\mu_b)\\
  &\ \ \ \ -\frac{1}{2}(\mathbf{x}_b-\mu_b)^\top\mathbf{\Lambda}_{ba}(\mathbf{x}_a-\mu_a)\\
  &\ \ \ \ -\frac{1}{2}(\mathbf{x}_b-\mu_b)^\top\mathbf{\Lambda}_{bb}(\mathbf{x}_b-\mu_b).\tag6\\
  \end{align}
  $$
  The $(6)$ is the function of $\mathbf{x}_a$, we can use this property
  $$
  \begin{align}
  -\frac{1}{2}(\mathbf{a}-\mu)^\top\mathbf{\Sigma}^{-1}(\mathbf{a}-\mu)&=-\frac{1}{2}\mathbf{a}^\top\mathbf{\Sigma}^{-1}\mathbf{a}\\
  &\ \ \ \ +\frac{1}{2}\mathbf{a^\top\Sigma}^{-1}\mu+\frac{1}{2}\mathbf{\mu^\top\Sigma}^{-1}\mathbf{a}\\
  &\ \ \ \ \ -\frac{1}{2}\mu^\top\mathbf{\Sigma}^{-1}\mu\tag7\\
  &=\frac{1}{2}\mathbf{a}^\top\mathbf{\Sigma}^{-1}\mathbf{a} +\mathbf{a^\top\Sigma}^{-1}\mu-\frac{1}{2}\mu^\top\mathbf{\Sigma}^{-1}\mu\tag8\\
  \end{align}
  $$
  (because of $\mathbf{\Sigma}^{-1}$ is symmetric then $\mathbf{a^\top\Sigma}^{-1}\mu=\mathbf{\mu^\top\Sigma}^{-1}\mathbf{a}$)

   to rewrite it by:
  $$
  \begin{align}
  -\frac{1}{2}(\mathbf{x-\mu})^\top\mathbf{\Sigma}^{-1}(\mathbf{x}-\mu)&=-\frac{1}{2}\mathbf{x}_a^\top\mathbf{\Lambda}_{aa} \mathbf{x}_a+\mathbf{x}_a^\top\mathbf{\Lambda}_{aa}\mu_a-\frac{1}{2}\mu_a^\top\mathbf{\Lambda}_{aa}\mu_a\\
  &\ \ \ \ \ -\frac{1}{2}\mathbf{x}_a^\top\mathbf{\Lambda}_{ab} \mathbf{x}_b+\frac{1}{2}\mathbf{x}_a^\top\mathbf{\Lambda}_{ab}\mu_b+\frac{1}{2}\mathbf{\mu}_a^\top\mathbf{\Lambda}_{ab}\mathbf{x}_b-\frac{1}{2}\mu_a^\top\mathbf{\Lambda}_{ab}\mu_b\\
  &\ \ \ \ \ -\frac{1}{2}\mathbf{x}_b^\top\mathbf{\Lambda}_{ba} \mathbf{x}_a+\frac{1}{2}\mathbf{x}_b^\top\mathbf{\Lambda}_{ba}\mu_a+\frac{1}{2}\mathbf{\mu}_b^\top\mathbf{\Lambda}_{ba}\mathbf{x}_a-\frac{1}{2}\mu_b^\top\mathbf{\Lambda}_{ba}\mu_a\\
  &\ \ \ \ \ -\frac{1}{2}(\mathbf{x}_b-\mu_b)^\top\mathbf{\Lambda}_{bb}(\mathbf{x}_b-\mu_b)\tag9\\
  &=-\frac{1}{2}\mathbf{x}_a^\top\mathbf{\Lambda}_{aa} \mathbf{x}_a+\mathbf{x}_a^\top\{\mathbf{\Lambda}_{aa}\mu_a-\mathbf{\Lambda}_{ab}(\mathbf{x}_b-\mu_b)\}+C\tag{10}
  \end{align}
  $$
  where
  $$
  C=-\frac{1}{2}\mu_a^\top\mathbf{\Lambda}_{aa}\mu_a+\mu_a^\top\mathbf{\Lambda}_{ab}(\mathbf{x}_b-\mu_b)-\frac{1}{2}(\mathbf{x}_b-\mu_b)^\top\mathbf{\Lambda}_{bb}(\mathbf{x}_b-\mu_b).\tag{11}
  $$
  We obtain $(10)$ from $(9)$ by  property $\mathbf{\Lambda}_{ab}=\mathbf{\Lambda}_{ba}^\top$. We see this is again a quadratic form with $C$ is independent of $\mathbf{x}_a$. So the condition distribution $p(\mathbf{x}_a|\mathbf{x}_b)$ will be Gaussian.

* We use the quadratic form to determine mean and covariance of conditional distribution, denoted as $\mu_{a|b}$ and $\mathbf{\Sigma}_{a|b}$, respectively. Consider the second order of $\mathbf{x}_a$:
  $$
  -\frac{1}{2}\mathbf{x}_a^\top\mathbf{\Lambda}_{aa}\mathbf{x}_a\tag{12}
  $$
  we can inference the covariance of $p(\mathbf{x}_a|\mathbf{x}_b)$ is:
  $$
  \mathbf{\Sigma}_{a|b}=\mathbf{\Lambda}_{aa}^{-1}\tag{13}.
  $$
  Next, we consider the first order of $\mathbf{x}_a$:
  $$
  \mathbf{x}_a\{\mathbf{\Lambda}_{aa}\mu_a-\mathbf{\Lambda}_{ab}(\mathbf{x}_b-\mu_b)\}\tag{14}
  $$
  we can obtain:
  $$
  \begin{align}
  \mu_{a|b}&=\mathbf{\Sigma}_{a|b}\{\mathbf{\Lambda}_{aa}\mu_a-\mathbf{\Lambda}_{ab}(\mathbf{x}_b-\mu_b)\}\\
  &=\mu_a-\mathbf{\Lambda}_{aa}^{-1}\mathbf{\Lambda}_{ab}(\mathbf{x}_b-\mu_b).\tag{15}
  \end{align}
  $$
  
* Next, we determine each path of $\mathbf{\Lambda}$ based on the following lemma:
  $$
  \begin{pmatrix}
  \mathbf{A}&\mathbf{B}\\\mathbf{C}&\mathbf{D}
  \end{pmatrix}^{-1}=\begin{pmatrix}
  \mathbf{M}&-\mathbf{MBD}^{-1}\\-\mathbf{D}^{-1}\mathbf{CM}&\mathbf{D}^{-1}+\mathbf{D}^{-1}\mathbf{CMBD}^{-1}
  \end{pmatrix}\tag{16}
  $$
  where $\mathbf{M}$ is the *Schur complement* $(\text{Appendix2})$ of $\mathbf{D}$ and $\mathbf{M}^{-1}$ is the *Schur complement* of $\mathbf{A}$, defined as:
  $$
  \mathbf{M}=(\mathbf{A}-\mathbf{BD}^{-1}\mathbf{C})^{-1}\tag{17}.
  $$

* Back to $(4)$ we have:
  $$
  \begin{pmatrix}
  \mathbf{\Sigma}_{aa}&\mathbf{\Sigma}_{ab}\\\mathbf{\Sigma}_{ba}&\mathbf{\Sigma}_{bb}
  \end{pmatrix}^{-1}=\begin{pmatrix}
  \mathbf{\Lambda}_{aa}&\mathbf{\Lambda}_{ab}\\
  \mathbf{\Lambda}_{ba}&\mathbf{\Lambda}_{bb}
  \end{pmatrix}.\tag{18}
  $$
  So:
  $$
  \begin{align}
  \mathbf{\Lambda}_{aa}&=(\mathbf{\Sigma}_{aa}-\mathbf{\Sigma}_{ab}\mathbf{\Sigma}_{bb}^{-1}\mathbf{\Sigma}_{ba})^{-1}\tag{19}\\
  \mathbf{\Lambda}_{ab}&=-(\mathbf{\Sigma}_{aa}-\mathbf{\Sigma}_{ab}\mathbf{\Sigma}_{bb}^{-1}\mathbf{\Sigma}_{ba})^{-1}\mathbf{\Sigma}_{ab}\mathbf{\Sigma}_{bb}^{-1}\tag{20}
  \end{align}.
  $$
  

#### **Appendix:**

1. The inverse of a symmetric matrix also symmetric. 

   **Proof:**

   * Given the inversible and symmetry matrix $A$:
     $$
     \mathbf{A}=\mathbf{A}^\top\tag{21}
     $$
     , we will prove:
     $$
     \mathbf{A}^{-1}=(\mathbf{A}^{-1})^\top\tag{22}.
     $$

   * First, we have:
     $$
     \mathbf{AA}^{-1}=\mathbf{I}\tag{23}.
     $$
     From $(21)$, we obtain:
     $$
     \mathbf{A}^\top\mathbf{A}^{-1}=\mathbf{I}\tag{24}.
     $$
     Then, use two properties $\mathbf{I}=\mathbf{I}^\top$ and $(\mathbf{A}\mathbf{B})^\top=\mathbf{B}^\top\mathbf{A}^\top$:
     $$
     (\mathbf{A}^{-1})^\top \mathbf{A}=\mathbf{I}\tag{25}.
     $$
     Finally, we put $\mathbf{A}^{-1}$ into right side of both:
     $$
     \begin{align}
     (\mathbf{A}^{-1})^\top \mathbf{A}\mathbf{A}^{-1}&=\mathbf{I}\mathbf{A}^{-1}\tag{26}\\
     (\mathbf{A}^{-1})^\top=\mathbf{A}^{-1}\tag{27}
     \end{align}
     $$
     and we are done.

2. In order to prove formula $(16)$, we consider the follow equation:
   $$
   \begin{pmatrix}
   \mathbf{A}&\mathbf{B}\\\mathbf{C}&\mathbf{D}
   \end{pmatrix}
   \begin{pmatrix}\mathbf{x}\\\mathbf{y}\end{pmatrix}=\begin{pmatrix}\mathbf{e}\\\mathbf{f}\end{pmatrix}\tag{28}.
   $$
   It equivalent to:
   $$
   \begin{cases}
   \mathbf{Ax}+\mathbf{By}=\mathbf{e} \ \ \ (a)\\
   \mathbf{Cx}+\mathbf{Dy}=\mathbf{f} \ \ \ (b)
   \end{cases}\tag{29}.
   $$
   From the under equation of the formula $(29)$, we obtain:
   $$
   \mathbf{y}=\mathbf{D}^{-1}(\mathbf{f}-\mathbf{Cx})\tag{30}.
   $$
   Replace the $(30)$ into the $(29.a)$, we have:
   $$
   \begin{align}
    \mathbf{Ax}+\mathbf{BD}^{-1}(\mathbf{f-Cx})&=\mathbf{e}\tag{31}\\
    \Leftrightarrow\ \ \ \ \ \ \ \ \ (\mathbf{A}-\mathbf{BD}^{-1}\mathbf{C})\mathbf{x}&=\mathbf{e}-\mathbf{BD}^{-1}\mathbf{f}\tag{32}\\
     \Leftrightarrow\ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \mathbf{x}&=(\mathbf{A}-\mathbf{BD}^{-1}\mathbf{C})^{-1}(\mathbf{e}-\mathbf{BD}^{-1}\mathbf{f})\tag{33}\\
       \Leftrightarrow\ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \mathbf{x}&=\mathbf{Me}-\mathbf{MBD}^{-1}\mathbf{f}\tag{34}
   \end{align}
   $$
   where $\mathbf{M}=(\mathbf{A}-\mathbf{BD}^{-1}\mathbf{C})^{-1}$.

   Replace the $(34)$ into the $(30)$, we calculate the $\mathbf{y}$:
   $$
   \begin{align}
   \mathbf{y}&=\mathbf{D}^{-1}[\mathbf{f}-\mathbf{C}(\mathbf{Me}-\mathbf{MBD}^{-1}\mathbf{f})]\tag{35}\\
   &=-\mathbf{D}^{-1}\mathbf{CMe}+(\mathbf{D}^{-1}+\mathbf{D}^{-1}\mathbf{MBD}^{-1})\mathbf{f}\tag{36}
   \end{align}.
   $$
   From the $(34)$ and the $(36)$, we have:
   $$
   \begin{pmatrix}
   \mathbf{x}\\\mathbf{y}
   \end{pmatrix}
   =\begin{pmatrix}
   \mathbf{M}&-\mathbf{MBD}^{-1}\\-\mathbf{D}^{-1}\mathbf{CM}&\mathbf{D}^{-1}+\mathbf{D}^{-1}\mathbf{CMBD}^{-1}
   \end{pmatrix}\begin{pmatrix}\mathbf{e}\\\mathbf{f}\end{pmatrix}\tag{37}.
   $$
   As mentioned at $(28)$, we also have:
   $$
   \begin{pmatrix}\mathbf{x}\\\mathbf{y}\end{pmatrix}=\begin{pmatrix}
   \mathbf{A}&\mathbf{B}\\\mathbf{C}&\mathbf{D}
   \end{pmatrix}^{-1}\begin{pmatrix}\mathbf{e}\\\mathbf{f}\end{pmatrix}\tag{38}.
   $$
   Then, we achieve the goal.

#### Reference:

* 2.3.1| Pattern Recognition and Machine Learning | C.M. Bishop.
* <a href='https://www.cis.upenn.edu/~jean/schur-comp.pdf' style="color:green">The Schur Complement and Symmetric PositiveSemidefinite (and Definite) Matrices</a>.