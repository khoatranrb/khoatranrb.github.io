---
layout: post
title:  "CV_3: Image Sharpening."
date:   2020-02-29 15:12:13 +0700
categories: CV
tags: cv image_processing sharpen
comments: 14
---

#### 1. Introduction

* *Sharpending* highlights transition in intensity. This technical uses in electronic printing and medical imaging. As we know, smoothing filters make output image could be accomplished in the spatial domain by pixel averaging in a neighborhood, it make the range of edges pixels and around pixels smaller. It that mean derivative at that point decreases. Thus, image differentiation enhances edges, noise and de-emphasizes with slowly varying intensities.

  

#### 2. Foundation

* Next, we will discuss about *first-* and *second- derivatives*. There are various ways to define them. However, we require some properties in there:

  * *First-derivative*:
    * Must be zero in areas of constant intensity.
    * Must be non zero at onset of an intensity step or ramp.
    * Must be nonzero along intensity ramps.

  * *Second-derivative*:
    * Must be zero in areas of constant intensity.
    * Must be nonzero in the onset and end of an intensity step or ramp.
    * Must be zero along intensity ramps.

* According to defined earlier, we have formula derivative of a <em>1-dimension</em> function $f(x)$:
  $$
  \frac{\partial f}{\partial x}=f(x+1)-f(x)
  \tag1
  $$
   and

$$
\frac{\partial^2 f}{\partial x^2}=f(x+1)+f(x-1)-2f(x) \tag2
$$



* Note: In formula $(1)$,  we use called <em>&quot;look ahead&quot;</em>. So we can also use $f(x)-f(x-1)$. Both are satisfies all terms we list above.

#### 3. Second derivative for image processing - The Laplacian

* In previous section, we define derivative for one-dimension function. In there, out object is image, a 2-dimensions function. Therefore, we will show second-derivative formula knows as the name *Laplacian*:
  $$
  \nabla^2 f=\frac{\partial^2 f}{\partial x^2}+\frac{\partial^2 f}{\partial y^2}\tag3
  $$
  with:
  $$
  \frac{\partial^2 f}{\partial x^2}=f(x+1,y)+f(x-1,y)-2f(x,y) \tag4
  $$
  and
  $$
  \frac{\partial^2 f}{\partial y^2}=f(x,y+1)+f(x,y-1)-2f(x,y) \tag5
  $$

* So we have:
  $$
  \nabla^2 f=f(x+1,y)+f(x-1,y)+f(x,y+1)+f(x,y-1)-4f(x,y) \tag6
  $$

* Base on $(6)$, we can create a kernel to compute <em>second-derivative</em> uses for convolution: $\begin{bmatrix}0&1&0 \\ 1&-4&1 \\ 0&1&0\end{bmatrix} (7)$. In many situation, we can use diagonal derivative or some variant, we may be have $\begin{bmatrix}0&-1&0 \\ -1&4&-1 \\ 0&-1&0\end{bmatrix}(8) $, $\begin{bmatrix}1&1&1 \\ 1&-8&1 \\ 1&1&1\end{bmatrix} (9)$, $\begin{bmatrix}-1&-1&-1 \\ -1&8&-1 \\ -1&-1&-1\end{bmatrix} (10)$.

* L<em>aplacian</em> is a derivative operator, it highlights sharp intensity transitions in image and de-emphasizes region of slowly varying intensities. This tend to produce image that have grayish edge lines and featureless background.

* If we define kernel with negative center coefficient, then we <em>subtract</em> the <em>Laplacian</em> image from the original. Thus, basic way to use <em>Laplacian</em> for image sharpening is:
  $$
  g(x,y)=f(x,y)+c[\nabla^2f(x,y)]\tag{11}
  $$
  where $f(x,y), \ g(x,y)$ is the input and sharpened image, respectively. We let $c=-1$ if the center Laplacian kernel is negative and $c=1$ in the rest.

* Ví dụ:

<p>
    <img src="https://github.com/khoablog/img/blob/master/sharpen.png?raw=true" style="zoom:100%,">
    </p><center><b>a b</b></center> 
<center><b>c d</b></center>
<center><i>a. Original image</i></center>
<center><i>b. Laplacian image</i></center>
<center><i>c. Image sharpened using c=-1, kernel (7)</i></center>
<center><i>d. Image sharpened using c=-1, kernel (9)</i></center>

