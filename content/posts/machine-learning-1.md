---
title: Machine Learning 01 := Basics of Linear Algebra
date: 2026-09-29
draft: true
tags:
  - machine-learning
---

As this year, my final year project at university is about comparing different machine learning algorithms, I thought I would start a series of blog posts exploring machine learning from the start!

- 01 := Basics of Linear Algebra <== **You are here**
- 02 := AI and ML Fundamentals
- 03 := ...

The target audience for these is anyone; regardless of whether you have a maths/computer science background, or you only went as far as GCSE Maths. Ultimately, as someone who's maths is okay but not a strong point, I aim to make these posts into what I wish I would've read when I was first learning about machine learning.

This is the first part, which covers the mathematics behind machine learning: linear algebra! We won't talk much about machine learning that much here; that's for future posts. 

## Table of Contents

1. What is Linear Algebra?
2. So what is a vector? 

# What is Linear Algebra?
Linear algebra is the area of maths that is all about **vectors**. It's an extremely important area of maths that is responsible for many areas of our modern world, such as machine learning, making movies and playing games on our computers and phones, solving problems in engineering and physics, to name a few!

When people hear the words "linear algebra" for the first time, they think of rearranging formulas and solving equations. However, this is not used at all in machine learning and therefore not useful to know. So you won't find any of that here!
# So what is a vector?
A vector is a structure containing a set of numbers. Each number in the list represents a unique dimension. 

All of these numbers come together to describe two important properties: **magnitude** and **direction**. But what do these mean?

Let's see what this looks like by starting with a number line and a one-dimensional vector.
$$\begin{pmatrix}5\end{pmatrix}$$
- The **direction** of a vector is which way it is pointing towards. 
  In the number line above, you can see that the vector is pointing towards the right. If the vector was a negative number (e.g. $-5$), the vector would be pointing towards the left.
- The **magnitude** of a vector is how far it points in a direction. 
  If a vector's arrow is shorter, it has a smaller magnitude. If a vector's arrow is longer, it has a larger magnitude.

{{< details title="**Exercise 1**: Which direction will this vector point on a number line?$$\begin{pmatrix}-2\end{pmatrix}$$Click to reveal the answer." >}}
**Answer**: It will point left.
{{< /details >}}

Okay, that makes sense. Now how about we scale up to a two-dimensional vector!
$$\begin{pmatrix}4\\4\end{pmatrix}$$
Since we now have two dimensions, the direction of the vector can now go upwards or downwards, in addition to left or right. The magnitude changes too, since we now have a diagonal line.

We can keep going; what about a three-dimensional vector?
$$\begin{pmatrix}3\\2\\6\end{pmatrix}$$
We can still keep going even further; how about a ten-dimensional vector?
$$\begin{pmatrix}5\\2\\6\\6\\9\\4\\1\\3\\7\\8\end{pmatrix}$$
Well, okay, I can't create a visualisation for that one. But they absolutely still have direction and magnitude! Vectors with more than three dimensions are very common in machine learning.
# Vectors vs Co-ordinates
At this point, you may be questioning "okay, so vectors are just like co-ordinates". Not at all.

Although on the surface they look very similar, co-ordinates are a set of numbers that describe a position of a point. Co-ordinates do not have direction or magnitude, whereas vectors do!
# Writing out vectors
There's a few different ways of writing vectors. Different websites, books, videos etc may use different ways to write the same thing.

We'll call a vector the letter $u$. These are some of the common various ways to write this vector:
$$\text{Arrow style: }\vec{u}$$$$\text{Bold style: }\mathbf{u}$$$$\text{Underline style: }\underline{u}$$
I'm most familiar with the latter underlined style, so that is what I'll be using. It is also easier to read when there are some extra symbols later on. However, all of these mean the same thing and are all correct to use!

I've hidden out a small detail about what we've already covered; so far, we've only worked with **column vectors**, where the numbers are stacked on top of each other like a column. 
$$\begin{pmatrix}3\\5\\2\end{pmatrix}$$
Did you know there is also **row vectors**, which are also important?
$$\begin{pmatrix}3&5&2\end{pmatrix}$$
Numerically, they are identical to each other. The main difference between them is their structure, and the purpose of this will be crystal clear when we get to matrix multiplication later.

Let's learn a new operation: **Transpose**. It looks like a slightly funny capital T.
$$\top$$
Transposing a vector means changing it to the other type of vector we just mentioned, without changing anything else about it. We write the transpose operator on the top right side of a vector.$$\begin{pmatrix}1\\2\\3\end{pmatrix}^\top=\begin{pmatrix}1&2&3\end{pmatrix}$$
We can also do this the other way round...$$\begin{pmatrix}4&5&6\end{pmatrix}^\top=\begin{pmatrix}4\\5\\6\end{pmatrix}$$
And that's all there is to it!

{{< details title="**Exercise 2**: Below is a vector $\underline{u}$. Write on paper what $\underline{u}^\top$ would be.$$\underline{u}=\begin{pmatrix}10\\4\\6\end{pmatrix}$$Click to reveal the answer." >}}
**Answer**: $$\underline{u}^\top=\begin{pmatrix}10&4&6\end{pmatrix}$$
{{< /details >}}

{{< details title="**Exercise 3**: Below is a vector $\underline{v}$. Write on paper what $\underline{v}^\top$ would be.$$\underline{v}=\begin{pmatrix}a\\b\\c\end{pmatrix}$$Click to reveal the answer." >}}
**Answer**: $$\underline{v}^\top=\begin{pmatrix}a&b&c\end{pmatrix}$$
{{< /details >}}

{{< details title="**Exercise 4**: Below is a row vector $\underline{w}$. Write on paper what $\underline{w}^\top$ would be.$$\underline{w}=\begin{pmatrix}5.25&4.0&2.37\end{pmatrix}$$Click to reveal the answer." >}}
**Answer**: $$\underline{w}^\top=\begin{pmatrix}5.25\\4.0\\2.37\end{pmatrix}$$
{{< /details >}}

Now is also a good time to talk about a special vector, called the **null vector**, or also sometimes called a zero vector. 

A null vector is made up entirely of zeros. A three dimensional null vector is shown below.
$$\underline{0}=\begin{pmatrix}0\\0\\0\end{pmatrix}$$
We always refer to it with an underlined zero, and we reserve the number zero for using the null vector.

{{< details title="**Exercise 5**: What would a six dimensional null vector look like?$$$$Click to reveal the answer." >}}
**Answer**: $$\underline{0}=\begin{pmatrix}0\\0\\0\\0\\0\\0\end{pmatrix}$$
{{< /details >}}

# How to access individual components of a vector
So you have a vector with all these dimensions, but sometimes we want to grab only one dimension out of a vector. How do we do that?

Lets work with the vector $\underline{u}$ below.
$$\underline{u}=\begin{pmatrix}15\\20\\5\end{pmatrix}$$
We can treat each dimension as an individual component of this vector. In the case of $\underline{u}$, we can write out $u_i$ where $i$ is which dimension we want, with 1 being the first at the top. 

$$u_1=15\qquad u_2=20\qquad u_3=5$$

Notice how it's no longer underlined - this is because it's no longer a vector! It's just one single number from this vector.

{{< details title="**Exercise 6**: Below is a new vector $\underline{u}$. Write on paper what $u_1$ would be.$$\underline{u}=\begin{pmatrix}123\\456\\789\end{pmatrix}$$Click to reveal the answer." >}}
**Answer**: $$u_1=123$$
{{< /details >}}

{{< details title="**Exercise 7**: Below is a vector $\underline{v}$. Write on paper what $v_6$ would be.$$\underline{v}=\begin{pmatrix}2.39\\1.67\\3.12\\5.01\\0.62\\2.55\\991000\\0.01\end{pmatrix}$$Click to reveal the answer." >}}
**Answer**: $$v_6=2.55$$
{{< /details >}}

{{< details title="**Exercise 8**: Below is a vector $\underline{w}\^\top$. Write on paper what $w_3$ would be.$$\underline{w}^\top=\begin{pmatrix}125&250&375&500\end{pmatrix}$$Click to reveal the answer." >}}
**Answer**: $$w_3=375$$
The process is not any different, just because it's transposed!
{{< /details >}}

{{< details title="**Exercise 9**: Below is a vector $\underline{x}$. Write on paper what $x_1+x_2+x_3$ would be.$$\underline{x}=\begin{pmatrix}2\\5\\3\\6\\1\end{pmatrix}$$Click to reveal the answer." >}}
**Answer**: $$x_1=2\qquad x_2=5\qquad x_3=3$$$$2+5+3=10$$
{{< /details >}}

{{< details title="**Exercise 10**: Below is a vector $\underline{y}$. Write on paper what $y_2\times y_4$ would be.$$\underline{y}=\begin{pmatrix}5\\20\\15\\10\end{pmatrix}$$Click to reveal the answer." >}}
**Answer**: $$y_2=20\qquad y_4=10$$$$20\times10=200$$
{{< /details >}}

# Adding and subtracting with vectors

# Scalars and scalar multiplication

# Dot product and orthogonality

# Length of a vector

# Unit vectors and normalisation

# Summary

// end part 1 here

# Vector spaces

# Properties of vectors

# Projection of a vector

# Linear combinations and span

# Basis vectors

# Linear dependence and independence

# Summations (Not linear algebra)

