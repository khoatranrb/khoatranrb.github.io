In this post, we study about the operations on sets that preserve convexity.

#### **1. Intersection**
* ***Theorem 1:*** *If all of $\mathcal{S_i}|_{i=1}^n$ are convex, $\bigcap_{i=1}^n\mathcal{S_i}$ is convex.* ($\text{Appendix 1}$)

#### **2. Affine function**
* ***Definition 1:*** *The function $f:\mathcal{R^n}\to\mathcal{R^m}$ is affine if it is a sum of a linear function and a constant: $f(\mathbf{x})=\mathbf{Ax}+\mathbf{b}$, where $\mathbf{x}\in\mathcal{R^n}$, $\mathbf{b}\in\mathcal{R^m}$ and $\mathbf{A}\in\mathcal{R}^{m\times n}$.*
* ***Theorem 2:*** *Suppose $\mathcal{S\in R^n}$ is convex and $\mathcal{f:R^n\to R^m}$ is an affine function, the image of $\mathbf{S}$ under $\mathcal{f}$: $\mathcal{f(S)=\biggl\{f(\mathbf{x})\biggl|\mathbf{x}\in S\biggl\}}$ is convex.* ($\text{Appendix 2}$)
* Similarity, we can show that the inverse image of $\mathcal{S}$ under $\mathcal{f}$ is preserves convexity because it also is an affine function. ($\text{Appendix 3}$)
* ***Theorem 3:*** *The projection of a convex set on to some of its coordinates is convex. If $\mathcal{S\subseteq R^m\times R^n}$ is convex, then: $\mathcal{T}=\biggl\{\mathbf{x_1}\in\mathcal{R^m} \ \biggl| \ \begin{bmatrix}\mathbf{x_1}\\\mathbf{x_2}\end{bmatrix}\in\mathcal{S}\ \ \text{for some}\  \mathbf{x_2}\in\mathcal{R^n}\biggl\}$ is convex.*
* ***Definition 2:*** *The sum of two sets is defined as:*
    $$
    \mathcal{S_1+S_2}=\biggl\{\mathbf{x_1}+\mathbf{x_2}\ \biggl | \ \mathbf{x_1}\in\mathcal{S_1},\ \mathbf{x_2}\in\mathcal{S_2} \biggl\}.
    $$
* ***Theorem 4:*** *If $\mathcal{S_1}$, $\mathcal{S_2}$ are convex, $\mathcal{S_1+S_2}$ is convex.*
* ***Definition 3:*** *The partial sum of $\mathcal{S_1}$, $\mathcal{S_2\in R^m\times R^n}$ defined as:*
    $$
    \mathcal{S}=\biggl\{\begin{bmatrix}\mathbf{x}\\\mathbf{y_1}+\mathbf{y_2}\end{bmatrix}\ \biggl| \ \begin{bmatrix}\mathbf{x}\\\mathbf{y_1}\end{bmatrix}\in\mathcal{S_1},\ \begin{bmatrix}\mathbf{x}\\\mathbf{y_2}\end{bmatrix}\in\mathcal{S_2}\biggl\}.
    $$
* ***Theorem 5:*** *If $\mathcal{S_1}$, $\mathcal{S_2}$ are convex, its partial sum is convex.*
* From **Appendix 2**, we can easily prove ***Theorem 3, 4, 5***.

#### **3. Perspective function**
* ***Definition 4:*** *The perspective function $\mathbf{P}:\mathcal{R^{n+1}\to R^n}$ with domain $\textbf{dom}\ \mathbf{P}=\mathcal{R^n\times R_{++}}$ takes the form: $\mathbf{P\biggl(\begin{bmatrix}\mathbf{x}\\x_{n+1}\end{bmatrix}\biggl)}=\displaystyle\frac{1}{x_{n+1}}\mathbf{x}$ (where $\mathcal{R_{++}}=\{x\in\mathcal{R}\ |\ x>0\}$).*
* ***Theorem 6:*** *If $\mathcal{C}\in$$\textbf{dom}\ \mathbf{P}$ is convex, then its image under $\mathbf{P}$: $\mathbf{P}(\mathcal{C})=\biggl\{\mathbf{P}(\mathbf{x})\ \biggl|\ \mathbf{x}\in\mathcal{C}\biggl\}$ is convex.* *($\text{Appendix 4}$)*
* ***Theorem 7:*** *The inverse image of a convex set under the perspective function $\mathbf{P}$: $\mathbf{P}^{-1}(\mathcal{C})=\biggl\{\begin{bmatrix}\mathbf{x}\\x_{n+1}\end{bmatrix}\in\mathcal{R^{n+1}}\ \biggl|\ \displaystyle\frac{1}{x_{n+1}}\mathbf{x}\in\mathcal{C},\ x_{n+1}>0\biggl\}$ is convex.* *($\text{Appendix 5}$)*

#### **4. Linear fractional function**
* ***Definition 5:*** *Linear fractional function is formed by composing the perspective function with an affine function.*
    * Suppose that we have $g:\mathcal{R^m\to R^{n+1}}$ is affine:
        $$
        g(\mathbf{x})=\begin{bmatrix}\mathbf{A}\\\mathbf{c^\top}\end{bmatrix}\mathbf{x}+
        \begin{bmatrix}\mathbf{b}\\d\end{bmatrix}
        $$
    where $\mathbf{A\in}\mathcal{R^{m\times n}}$, $\mathbf{c\in}\mathcal{R^n}$, $\mathbf{b\in}\mathcal{R^m}$ and $d\in\mathcal{R}$.
    * The linear fractional function $f:\mathcal{R^n\to R^m}$ is given by $f=\mathbf{P}\circ g$:
            $$
            f(\mathbf{x})=\frac{\mathbf{Ax}+\mathbf{b}}{\mathbf{c^\top x}+d}
            $$
    where $\textbf{dom}\ f=\{\mathbf{x}\ |\ \mathbf{c^\top x}+d>0\}$.
* Because the linear fractional function is the combination between an affine function and a perspective function, so it also preserves the convexity.
#### **Appendix:**

1. *If all of $\mathcal{S_i}|_{i=1}^n$ are convex, $\bigcap_{i=1}^n\mathcal{S_i}$ is convex.*
    **Proof:**
    * Consider two sets $\mathcal{S_1}$ and $\mathcal{S_2}$ are convex. We define $\mathcal{S_{12}}=\mathcal{S_1\cap S_2}$.
    * With $\mathbf{x_1},\mathbf{x_2}\in\mathcal{S_{12}}$ (belong to both $\mathcal{S_1,S_2}$), we assume that $\mathcal{S_{12}}$ is non-convex, it means that exist a $\theta\in[0,1]$ such that $\mathbf{x_{12}}=\theta\mathbf{x_1}+(1-\theta)\mathbf{x_2}\notin\mathcal{S_{12}}$. And we have to demonstrate it is wrong.
        * The $\mathbf{x_{12}}\notin\mathcal{S_{12}}$ means: $\mathbf{x_{12}}\notin\mathcal{S_1}$ $(1)$ or $\mathbf{x_{12}}\notin\mathcal{S_2}$ $(2)$ or $\mathbf{x_{12}}\notin\mathcal{S_1}\cup\mathcal{S_2}$ $(3)$.
        * Because of $\begin{cases}\mathbf{x_1},\mathbf{x_2}\in\mathcal{S_1}\\\mathcal{S_1}\text{ is convex}\end{cases}$, then $\mathbf{x_{12}}$ must belong to $\mathcal{S_1}$. So $(1)$ is impossible.
        * Similar to the above, we can show that $(2)$ is wrong. Then $(3)$ also is wrong.
    * Therefore, $\mathcal{S_{12}}$ is certainly convex. And in general, the intersection of the convex sets is convex.

2. *If $\mathcal{S\in R^n}$ is convex and $\begin{cases}\mathcal{f:R^n\to R^m}\\f(\mathbf{x})=\mathbf{Ax}+\mathbf{b}\end{cases}$ is an affine function, the image of $\mathcal{S}$ under $\mathcal{f}$: $\mathcal{f(S)=\biggl\{f(\mathbf{x})\biggl|\mathbf{x}\in S\biggl\}}$ is convex.*
    **Proof:**
    * With $\mathbf{x_1}$, $\mathbf{x_2}$ $\in\mathcal{S}$, we have a $\theta\in[0,1]$ such that $\theta\mathbf{x_1}+(1-\theta)\mathbf{x_2}\in\mathcal{S}$. Consider the image of $\mathcal{S}$ under $\mathcal{f}$:
    
    $$
    \begin{align}
    f\biggl(\theta\mathbf{x_1}+(1-\theta)\mathbf{x_2}\biggl)&=\mathbf{A}(\theta\mathbf{x_1}+(1-\theta)\mathbf{x_2})+\mathbf{b}\\
    &=\theta\mathbf{Ax_1}+(1-\theta)\mathbf{Ax_2}+\mathbf{b}\\
    &=\theta\mathbf{Ax_1}+\theta\mathbf{b}+(1-\theta)\mathbf{Ax_2}+(1-\theta)\mathbf{b}\\
    &=\theta f(\mathbf{x_1})+(1-\theta) f(\mathbf{x_2}).
    \end{align}
    $$
3. *With $f(\mathbf{x})=\mathbf{Ax}+\mathbf{b}$ is an affine function, then the inverse function $\mathbf{x}=f^{-1}(\mathbf{x})$ is also affine function.*
    **Proof:**
    $$
    \begin{align}
    f(\mathbf{x})&=\mathbf{Ax}+\mathbf{b}\\
    \iff\ \ \ \ \  \ \ \ \ \ \ \mathbf{Ax} &=f(\mathbf{x})-\mathbf{b}\\
    \iff\ \ \ \ \ \mathbf{A^\top Ax}&=\mathbf{A^\top}\biggl(f(\mathbf{x})-\mathbf{b}\biggl)\\
    \iff\ \ \ \ \ \ \ \ \ \ \ \ \ \ \mathbf{x} &=(\mathbf{A^\top A})^{-1}\mathbf{A^\top}\biggl(f(\mathbf{x})-\mathbf{b}\biggl)\\
    &=\biggl((\mathbf{A^\top A})^{-1}\mathbf{A^\top}\biggl)f(\mathbf{x})-(\mathbf{A^\top A})^{-1}\mathbf{A^\top}\mathbf{b}.
    \end{align}
    $$
4. *With the perspective function $\mathbf{P\biggl(\begin{bmatrix}\mathbf{x}\\x_{n+1}\end{bmatrix}\biggl)}=\displaystyle\frac{1}{x_{n+1}}\mathbf{x}$ (with $x_{n+1}>0$) and a convex set $\mathcal{C}$, $\mathbf{P}(\mathcal{C})$ is convex.*
    **Proof:**
    * Suppose $\mathbf{x}=\begin{bmatrix}\overline{\mathbf{x}}\\x_{n+1}\end{bmatrix}$, $\mathbf{y}=\begin{bmatrix}\overline{\mathbf{y}}\\y_{n+1}\end{bmatrix}\in\mathcal{C}$ (with $x_{n+1},y_{n+1}>0$), we always have a $\theta\in[0,1]$ such that $\theta\mathbf{x}+(1-\theta)\mathbf{y}\in\mathcal{C}$. Let consider the image of $\mathcal{C}$ under $\mathbf{P}$:
    $$
    \begin{align}
    \mathbf{P}\biggl(\theta\mathbf{x}+(1-\theta)\mathbf{y}\biggl)&=\frac{\theta\overline{\mathbf{x}}+(1-\theta)\overline{\mathbf{y}}}{\theta x_{n+1}+(1-\theta)y_{n+1}}\\
    &=\frac{\theta\overline{\mathbf{x}}}{\theta x_{n+1}+(1-\theta)y_{n+1}}+\frac{(1-\theta)\overline{\mathbf{y}}}{\theta x_{n+1}+(1-\theta)y_{n+1}}\\
    &=\frac{\overline{\mathbf{x}}}{x_{n+1}}\frac{\theta x_{n+1}}{\theta x_{n+1}+(1-\theta)y_{n+1}}+\frac{\overline{\mathbf{y}}}{y_{n+1}}\frac{(1-\theta) y_{n+1}}{\theta x_{n+1}+(1-\theta)y_{n+1}}\\
    &=\mathbf{P}(\mathbf{x})\frac{\theta x_{n+1}}{\theta x_{n+1}+(1-\theta)y_{n+1}}+\mathbf{P}(\mathbf{y})\frac{(1-\theta) y_{n+1}}{\theta x_{n+1}+(1-\theta)y_{n+1}}\\
    &=\mathbf{P}(\mathbf{x})\frac{\theta x_{n+1}}{\theta x_{n+1}+(1-\theta)y_{n+1}}+\mathbf{P}(\mathbf{y})\biggl(1-\frac{\theta x_{n+1}}{\theta x_{n+1}+(1-\theta)y_{n+1}}\biggl)\\
    &=\lambda\mathbf{P}(\mathbf{x})+(1-\lambda)\mathbf{P}(\mathbf{y})\\
    \end{align}
    $$
    where $\lambda=\displaystyle\frac{\theta x_{n+1}}{\theta x_{n+1}+(1-\theta)y_{n+1}}$. Because $x_{n+1},y_{n+1}>0$ and $\theta\in[0,1]$, we can show that $\lambda\in[0,1]$.

5. *Given a convex set $\mathcal{C}$. For every pair ($\mathbf{x}$, p) with p>0 such that $\displaystyle\frac{\mathbf{x}}{p}\in\mathcal{C}$, we obtain a set is constituted by all of $\biggl\{\begin{bmatrix}\mathbf{x}\\ p\end{bmatrix}\biggl\}$ is convex.*
    **Proof:**
    * With $\mathbf{x}=\displaystyle\frac{\overline{\mathbf{x}}}{x_{n+1}}$, $\mathbf{y}=\displaystyle\frac{\overline{\mathbf{y}}}{y_{n+1}}\in\mathcal{C}$ (with $x_{n+1},y_{n+1}>0$) and $\theta\in[0,1]$, we have $\theta\mathbf{x}+(1-\theta)\mathbf{y}\in\mathcal{C}$.
    * Set $\mathbf{P}^{-1}\biggl(\displaystyle\frac{\overline{\mathbf{x}}}{x_{n+1}}\biggl)=\begin{bmatrix}\overline{\mathbf{x}}\\x_{n+1}\end{bmatrix}$ (with $x_{n+1}>0$), similar to $\text{Appendix 4}$, we consider:
    
    $$
    \begin{align}
    \mathbf{P}^{-1}\biggl(\theta\mathbf{x}+(1-\theta)\mathbf{y}\biggl)&=\mathbf{P}^{-1}\biggl(\displaystyle\frac{\theta\mathbf{\overline{x}}}{x_{n+1}}+\displaystyle\frac{(1-\theta)\mathbf{\overline{y}}}{y_{n+1}}\biggl)\\
    &=\mathbf{P}^{-1}\biggl(\displaystyle\frac{\theta y_{n+1}\mathbf{\overline{x}}+(1-\theta) x_{n+1}\mathbf{\overline{y}}}{x_{n+1}y_{n+1}}\biggl)\\
    &=\begin{bmatrix}\theta y_{n+1}\mathbf{\overline{x}}+(1-\theta) x_{n+1}\mathbf{\overline{y}}\\ x_{n+1}y_{n+1}\end{bmatrix}\\
    &=\begin{bmatrix}\theta y_{n+1}\mathbf{\overline{x}}+(1-\theta) x_{n+1}\mathbf{\overline{y}}\\ \theta x_{n+1}y_{n+1}+(1-\theta)x_{n+1}y_{n+1}\end{bmatrix}\\
    &=\begin{bmatrix}\theta y_{n+1}\mathbf{\overline{x}}\\ \theta x_{n+1}y_{n+1}\end{bmatrix}+\begin{bmatrix}(1-\theta) x_{n+1}\mathbf{\overline{y}}\\ (1-\theta)x_{n+1}y_{n+1}\end{bmatrix}\\
    &=\theta y_{n+1}\begin{bmatrix}\mathbf{\overline{x}}\\ x_{n+1}\end{bmatrix}+(1-\theta) x_{n+1}\begin{bmatrix}\mathbf{\overline{y}}\\ y_{n+1}\end{bmatrix}\\
    \text{$\biggl($let $\begin{cases}\alpha_x=\theta y_{n+1}\\ \alpha_y=(1-\theta) x_{n+1}\\ \alpha=\alpha_x+\alpha_y\end{cases}$ $\biggl)$}&=\alpha_x\begin{bmatrix}\mathbf{\overline{x}}\\ x_{n+1}\end{bmatrix}+\alpha_y\begin{bmatrix}\mathbf{\overline{y}}\\ y_{n+1}\end{bmatrix}\\
    &=\frac{\alpha_x}{\alpha}\begin{bmatrix}\mathbf{\alpha\overline{x}}\\ \alpha x_{n+1}\end{bmatrix}+\frac{\alpha_y}{\alpha}\begin{bmatrix}\mathbf{\alpha\overline{y}}\\ \alpha y_{n+1}\end{bmatrix}\\
    &=\frac{\alpha_x}{\alpha}\mathbf{P}^{-1}\biggl(\displaystyle\frac{\alpha\overline{\mathbf{x}}}{\alpha x_{n+1}}\biggl)+\frac{\alpha_y}{\alpha}\mathbf{P}^{-1}\biggl(\displaystyle\frac{\alpha\overline{\mathbf{y}}}{\alpha y_{n+1}}\biggl)\\
    &=\frac{\alpha_x}{\alpha}\mathbf{P}^{-1}\biggl(\displaystyle\frac{\overline{\mathbf{x}}}{x_{n+1}}\biggl)+(1-\frac{\alpha_x}{\alpha})\mathbf{P}^{-1}\biggl(\displaystyle\frac{\overline{\mathbf{y}}}{ y_{n+1}}\biggl).\\
    \end{align}
    $$

#### **Reference:**

* Chapter 2 | Convex Optimization.