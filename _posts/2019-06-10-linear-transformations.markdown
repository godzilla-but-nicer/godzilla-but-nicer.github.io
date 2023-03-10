---
layout: post
title:  "An Aside on Linear Transformations"
date:   2019-06-10 00:00:00 -0500
categories: methods
---


One of the most interesting features of matrices is their ability to serve as
both a container for data and a tool for transforming data. When a vector is
multiplied by a matrix, the matrix is said to perform a linear transformation
on that vector. We get a vector back that is a distorted version of the
original vector. The vector could be rotated or stretched or flipped, but it is
always based on the original vector. We can also always get the original vector
back.

Let's say we have a matrix $$A$$ and a vector $\mathbf{v}$

$$
A = \begin{bmatrix}
    a_{1,1} & a_{1,2} \\
    a_{2,1} & a_{2,2}
    \end{bmatrix}
$$

$$
\mathbf{v} = \begin{bmatrix}
             v_1 \\
             v_2
             \end{bmatrix}
$$

Our linear transformation will look something like this:

$$ A\mathbf{v}=\mathbf{v’} $$

$$
\begin{bmatrix} a_{1,1} & a_{1,2} \\ a_{2,1} & a_{2,2} \end{bmatrix} \begin{bmatrix} v_1 \\ v_2 \end{bmatrix} = \begin{bmatrix} a_{1,1} v_1 + a_{1,2} v_2 \\ a_{2,1} v_1 + a_{2,2} v_2 \end{bmatrix} = \begin{bmatrix} v’_1 \\ v’_2 \end{bmatrix}
$$

We get the original vector back using:

$$ \mathbf{v} = \mathbf{v’}A^{-1} $$

Let’s take a look at a more concrete example using some arbitrary values:

$$ A = \begin{bmatrix} 2 & 1  \\ -1 & 1  \end{bmatrix} $$

$$ \mathbf{v} = \begin{bmatrix} 2 \\ 1 \end{bmatrix} $$

First of all, let’s take a look at this vector:

![a vector and its basis](/assets/linear-transformations/before_trans-1.png)

Note that in the image I’ve also included the basis vectors $\hat{i}$ and
$\hat{j}$.

$$ \hat{i}=\begin{bmatrix} 1\\ 0 \end{bmatrix} \; \hat{j} = \begin{bmatrix} 0 \\ 1 \end{bmatrix} $$

We can think of our vector $\mathbf{v}$ as a linear combination of these two 
basis vectors

$$ \mathbf{v} = 2\hat{i} + 1\hat{j} = 2\begin{bmatrix} 1 \\ 0 \end{bmatrix} + 1 \begin{bmatrix} 0 \\ 1 \end{bmatrix} = \begin{bmatrix} 2 \\ 1 \end{bmatrix} $$

This will be important later.

Of course, we can perform the transformation by hand by plugging our numbers
into the general solution shown above.

$$ \begin{bmatrix} 2 & 1 \\ -1 & 1 \end{bmatrix} \begin{bmatrix} 2 \\ 1 \end{bmatrix} = \begin{bmatrix} (2) (2) + (1) (1) \\ (-1) (2) + (1) (1) \end{bmatrix} = \begin{bmatrix} 5 \\ -1 \end{bmatrix} $$

However, it’s probably more enlightening, and certainly more interesting to
look at this transformation visually. Here is our vector (and our basis
vectors) after the transformation.

![holy fucking shit](/assets/linear-transformations/after_trans.png)

We’ve kind of rotated and squished things together. Our basis vectors are no
longer orthogonal and Our vector has been stretched and rotated. One thing 
hasn’t changed, however: $\mathbf{v'} is still the exact same linear
combination of basis vectors. When we look at things this way we find that
what we’ve really changed is the basis.

Our new basis consists of the vectors:

$$ \hat{i}' = \begin{bmatrix} 2 \\ -1 \end{bmatrix} \; \hat{j}' = \begin{bmatrix} 1 \\ 1 \end{bmatrix} $$

These vectors are the columns of our transformation matrix! Our new vector can
be calculated by hand by the same linear combination as before but from these
new basis vectors:

$$ \mathbf{v}_{new} = 2\hat{i}' + 1\hat{j}' = 2 \begin{bmatrix} 2 \\ -1 \end{bmatrix} + 1 \begin{bmatrix} 1 \\ 1 \end{bmatrix} = \begin{bmatrix} (2)(2) + (1)(1) \\ (2)(-1) + (1)(1) \end{bmatrix} = \begin{bmatrix} 5 \\ -1 \end{bmatrix} $$

This provides some major intuition that I lacked after being told to simply
memorize how matrix-vector multiplication worked in linear algebra class. When
we perform a linear transformation we are always simply expressing *the same
linear combination in terms of a different basis.*

Because we are changing the basis, and not really our vector, we can think of
this as changing space and all of the vectors that it may contain.

Consider a regular grid of points

![a regular grid of points](/assets/linear-transformations/before_grid.png)

We can think of each of these points mathematically as vectors that reach out
from the origin. The points show only the endpoints of these vectors. When we
transform each of these points with our matrix, we get a new version of space

![an irregular grid of points](/assets/linear-transformations/after_grid.png)

Our new space is rotated and stretched, just like the arbitrary vector we put
inside of it in the earlier example. This is, of course, a consequence of our
changing basis.

We can do a lot of different things with linear transformations. Here are some
examples of how different matrices affect both our regular grid and our
arbitrary vector.

## Scaling

$$ A=\begin{bmatrix} 1 & 0 \\ 0 & 1 \end{bmatrix} $$

![scaling transformation](/assets/linear-transformations/scale.png)

## Reflection

$$ A=\begin{bmatrix} -1 & 0 \\ 0 & 1 \end{bmatrix} $$

![reflection transformation](/assets/linear-transformations/reflection.png)

## Transposition (or something)

$$ A=\begin{bmatrix} 0 & 1 \\ 1 & 0 \end{bmatrix} $$

![transposition transformation](/assets/linear-transformations/transpose.png)

## Shear

$$ A=\begin{bmatrix} 1 & 1.5 \\ 0 & 1 \end{bmatrix} $$

![Shear transformation](/assets/linear-transformations/shear.png)

## Rotation

$$ A=\begin{bmatrix} \cos{\frac{\pi}{4}} & -\sin{\frac{\pi}{4}} \\ \sin{\frac{\pi}{4}} & \cos{\frac{\pi}{4}} \end{bmatrix} $$

![rotation transformation](/assets/linear-transformations/rotation.png)

## Projection

$$ A=\begin{bmatrix} 1 & 0 \\ 0 & 0 \end{bmatrix} $$

![projection transformation](/assets/linear-transformations/projection.png)

## Single-dimension Scale

$$ A=\begin{bmatrix} 0.5 & 0 \\ 0 & 1 \end{bmatrix} $$

![single-dimensional scale](/assets/linear-transformations/dim_change.png)

## [Squeeze](https://www.youtube.com/watch?v=RQciegmLPAo)

$$ A=\begin{bmatrix} 1 & 0.5 \\ 0.5 & 1 \end{bmatrix} $$

![squeeze transformation](/assets/linear-transformations/squeeze.png)

### (Re)sources

- [3Blue1Brown's definitive video on the topic](https://www.youtube.com/watch?v=kYB8IZa5AuE&list=PLZHQObOWTQDPD3MizzM2xVFitgF8hE_ab&index=3)
- [A better version of this post with fancy animations!](https://dododas.github.io/linear-algebra-with-python/posts/16-12-29-2d-transformations.html)
