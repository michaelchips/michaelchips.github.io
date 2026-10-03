---
title: Machine Learning 01 := Basics of Vectors in Linear Algebra
date: 2026-09-29
draft: true
tags:
  - machine-learning
---

As this year, my final year project at university is about comparing different machine learning algorithms, I thought I would start a series of blog posts exploring machine learning from the start!

- 01 := Basics of Vectors in Linear Algebra <== **You are here**
- 02 := Intermediate Vectors in Linear Algebra
- 03 := AI and ML Fundamentals
- 04 := How To Compare Machine Learning Algorithms

The target audience for these is anyone; regardless of whether you have a maths/computer science background, or you only went as far as GCSE Maths. Ultimately, as someone who's maths is okay but not a strong point, I aim to make these posts into what I wish I would've read when I was first learning about machine learning.

This is the first part, which covers the mathematics behind machine learning: linear algebra! We won't talk much about machine learning that much here; that's for future posts. 

## Table of Contents

1. What is Linear Algebra? [[Jump there]](#01-what-is-linear-algebra)
2. So then, what is a vector? [[Jump there]](#02-so-then-what-is-a-vector)
3. Vectors vs Co-ordinates [[Jump there]](#03-vectors-vs-co-ordinates)
4. Writing out vectors [[Jump there]](#04-writing-out-vectors)
5. How to access individual components of a vector [[Jump there]](#05-how-to-access-individual-components-of-a-vector)
6. Adding and subtracting with vectors [[Jump there]](#06-adding-and-subtracting-with-vectors)
7. Scalars and scalar multiplication [[Jump there]](#07-scalars-and-scalar-multiplication)
8. Dot product and orthogonality [[Jump there]](#08-dot-product-and-orthogonality)
9. Length of a vector [[Jump there]](#09-length-of-a-vector)
10. Unit vectors and normalisation [[Jump there]](#10-unit-vectors-and-normalisation)
11. Summary [[Jump there]](#11-summary)

> There are lots of exercises in this page to help improve your understanding. If you'd prefer all of the exercises at the end of the post instead of scattered throughout, click here.
# 01. What is Linear Algebra?
Linear algebra is the area of maths that is all about **vectors**. It's an extremely important area of maths that is responsible for many areas of our modern world, such as machine learning, making movies and playing games on our computers and phones, solving problems in engineering and physics, to name a few!

When people hear the words "linear algebra" for the first time, they think of rearranging formulas and solving equations. However, this is not used at all in machine learning and therefore not useful to know. So you won't find any of that here!
# 02. So then, what is a vector?
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
# 03. Vectors vs Co-ordinates
At this point, you may be questioning "okay, so vectors are just like co-ordinates". Not at all.

Although on the surface they look very similar, co-ordinates are a set of numbers that describe a position of a point. Co-ordinates do not have direction or magnitude, whereas vectors do!
# 04. Writing out vectors
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
Transposing a vector means changing the shape of the vector to the other type we just mentioned, without changing anything else about it. We write the transpose operator on the top right side of a vector.$$\begin{pmatrix}1\\2\\3\end{pmatrix}^\top=\begin{pmatrix}1&2&3\end{pmatrix}$$
The shape of this vector was 3 rows and 1 column before, but now after transposing, it is 1 row and 3 columns.

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

{{< details title="**Exercise 5**: Below is a vector $\underline{x}$. How many rows **and** columns does it have?$$\underline{x}=\begin{pmatrix}1\\2\\2\\1\\3\\2\end{pmatrix}$$Click to reveal the answer." >}}
**Answer**: $\underline{x}$ has 6 rows, 1 column.
{{< /details >}}

{{< details title="**Exercise 6**: Below is a vector $\underline{y}$. How many rows **and** columns would $\underline{y}^\top$ have?$$\underline{y}=\begin{pmatrix}a\\s\\d\\f\\g\\h\\j\\k\\l\end{pmatrix}$$Click to reveal the answer." >}}
**Answer**: $\underline{y}^\top$ would have 1 row, 9 columns.
$$\underline{y}^\top=\begin{pmatrix}a&s&d&f&g&h&j&k&l\end{pmatrix}$$
{{< /details >}}

{{< details title="**Exercise 7**: Below is a column vector $\underline{z}$. Write on paper what $\left(\underline{z}^\top\right)^\top$ would be.$$\underline{z}=\begin{pmatrix}3\\1\\4\end{pmatrix}$$Click to reveal the answer." >}}
**Answer**: $$\left(\underline{z}^\top\right)^\top=\begin{pmatrix}3\\1\\4\end{pmatrix}$$
Transpose a vector, transpose it again, you end up with the same thing as before!
{{< /details >}}

Now is also a good time to talk about a special vector, called the **null vector**, or also sometimes called a zero vector. 

A null vector is made up entirely of zeros. A three dimensional null vector is shown below.
$$\underline{0}=\begin{pmatrix}0\\0\\0\end{pmatrix}$$
We always refer to it with an underlined zero, and we reserve the number zero for using the null vector.

{{< details title="**Exercise 8**: What would a six dimensional null vector look like?$$$$Click to reveal the answer." >}}
**Answer**: $$\underline{0}=\begin{pmatrix}0\\0\\0\\0\\0\\0\end{pmatrix}$$
{{< /details >}}

# 05. How to access individual components of a vector
So you have a vector with all these dimensions, but sometimes we want to precisely grab only one row or column out of a vector. How do we do that?

Lets work with the vector $\underline{u}$ below.
$$\underline{u}=\begin{pmatrix}15\\20\\5\end{pmatrix}$$
We can treat each dimension as an individual component of this vector. In the case of $\underline{u}$, we can write out $u_i$ where $i$ is which dimension we want, with 1 being the first at the top. 

$$u_1=15\qquad u_2=20\qquad u_3=5$$

Notice how it's no longer underlined - this is because the result is no longer a vector! It's just one single number from this vector.

{{< details title="**Exercise 9**: Below is a new vector $\underline{u}$. Write on paper what $u_1$ would be.$$\underline{u}=\begin{pmatrix}123\\456\\789\end{pmatrix}$$Click to reveal the answer." >}}
**Answer**: $$u_1=123$$
{{< /details >}}

{{< details title="**Exercise 10**: Below is a vector $\underline{v}$. Write on paper what $v_6$ would be.$$\underline{v}=\begin{pmatrix}2.39\\1.67\\3.12\\5.01\\0.62\\2.55\\991000\\0.01\end{pmatrix}$$Click to reveal the answer." >}}
**Answer**: $$v_6=2.55$$
{{< /details >}}

{{< details title="**Exercise 11**: Below is a vector $\underline{w}^\top$. Write on paper what $w_3$ would be.$$\underline{w}^\top=\begin{pmatrix}125&250&375&500\end{pmatrix}$$Click to reveal the answer." >}}
**Answer**: $$w_3=375$$
The process is not any different, just because it's transposed!
{{< /details >}}

{{< details title="**Exercise 12**: Below is a vector $\underline{x}$. Write on paper what $x_1+x_2+x_3$ would be.$$\underline{x}=\begin{pmatrix}2\\5\\3\\6\\1\end{pmatrix}$$Click to reveal the answer." >}}
**Answer**: $$x_1=2\qquad x_2=5\qquad x_3=3$$$$2+5+3=10$$
{{< /details >}}

{{< details title="**Exercise 13**: Below is a vector $\underline{y}$. Write on paper what $y_2\times y_4$ would be.$$\underline{y}=\begin{pmatrix}5\\20\\15\\10\end{pmatrix}$$Click to reveal the answer." >}}
**Answer**: $$y_2=20\qquad y_4=10$$$$20\times10=200$$
{{< /details >}}
# 06. Adding and subtracting with vectors
It's possible for us to add two vectors together, or subtract one vector from another, just like in everyday maths. There is one important restriction however:

**Vectors MUST have the same number of rows and columns to be added or subtracted**

Vectors with different dimensionality are incompatible!

{{< details title="**Exercise 14**: Below are two vectors $\underline{u}$ and $\underline{v}$. Can $\underline{u}+\underline{v}$ be calculated?$$\underline{u}=\begin{pmatrix}3\\9\\7\\6\end{pmatrix}\qquad\underline{v}=\begin{pmatrix}41\\8\\77\\0\end{pmatrix}$$Click to reveal the answer." >}}
**Answer**: Yes. $\underline{u}$ and $\underline{v}$ have the same amount of rows and columns.
{{< /details >}}

{{< details title="**Exercise 15**: Below are two vectors $\underline{u}$ and $\underline{v}$. Can $\underline{u}+\underline{v}$ be calculated?$$\underline{u}=\begin{pmatrix}72381\\81626\\18129\\83453\\41714\\86827\\90019\\47547\\9865\\22938\end{pmatrix}\qquad\underline{v}=\begin{pmatrix}61626\\91827\\63592\\52055\\38177\\5381\\39738\\10571\\14112\end{pmatrix}$$Click to reveal the answer." >}}
**Answer**: No. $\underline{v}$ has one less row than $\underline{u}$, so it is impossible to calculate $\underline{u}+\underline{v}$ without changing their dimensions.
{{< /details >}}

{{< details title="**Exercise 16**: Below are two vectors $\underline{u}$ and $\underline{v}$. Can $\underline{u}+\underline{v}$ be calculated?$$\underline{u}=\begin{pmatrix}1\\3\\5\end{pmatrix}\qquad\underline{v}=\begin{pmatrix}2&4&6\end{pmatrix}$$Click to reveal the answer." >}}
**Answer**: No. $\underline{u}$ has 3 rows and 1 column, while $\underline{v}$ has 1 row and 3 columns.
{{< /details >}}

Now lets try adding two vectors together, with $\underline{u}$ and $\underline{v}$ below as an example.$$\underline{u}=\begin{pmatrix}2\\3\\2\end{pmatrix}\qquad\underline{v}=\begin{pmatrix}1\\2\\2\end{pmatrix}$$
To do this, we add each corresponding component together, and the final result is one single vector.$$\underline{u}+\underline{v}=\begin{pmatrix}2+1\\3+2\\2+2\end{pmatrix}$$$$=\begin{pmatrix}3\\5\\4\end{pmatrix}$$
Not so hard, right? Try these exercises for yourself!

{{< details title="**Exercise 17**: Below are two vectors $\underline{u}$ and $\underline{v}$. Calculate $\underline{u}+\underline{v}$.$$\underline{u}=\begin{pmatrix}10\\6\\5\\8\\-1\end{pmatrix}\qquad\underline{v}=\begin{pmatrix}5\\3\\2\\0\\3\end{pmatrix}$$Click to reveal the answer." >}}
**Answer**: $$\underline{u}+\underline{v}=\begin{pmatrix}15\\9\\7\\8\\2\end{pmatrix}$$
{{< /details >}}

{{< details title="**Exercise 18**: Imagine you have any two vectors you can think of, $\underline{x}$ and $\underline{y}$. Will $\underline{x}+\underline{y}$ and $\underline{y}+\underline{x}$ always be the same result?" >}}
**Answer**: Yes. When performing addition, order does not matter, therefore you will always get the same result.
{{< /details >}}

Subtracting one vector from another vector is almost an identical process to adding two vectors. Let's use a new $\underline{u}$ and $\underline{v}$ below:$$\underline{u}=\begin{pmatrix}7\\9\\3\end{pmatrix}\qquad\underline{v}=\begin{pmatrix}4\\5\\5\end{pmatrix}$$To calculate $\underline{u}-\underline{v}$, we subtract each component of $\underline{v}$ from the corresponding component of $\underline{u}$, like this:
$$\underline{u}-\underline{v}=\begin{pmatrix}7-4\\9-5\\3-5\end{pmatrix}$$$$=\begin{pmatrix}3\\4\\-2\end{pmatrix}$$

{{< details title="**Exercise 19**: Below are two vectors $\underline{u}$ and $\underline{v}$. Calculate $\underline{u}-\underline{v}$.$$\underline{u}=\begin{pmatrix}10\\10\\10\\10\\10\\10\end{pmatrix}\qquad\underline{v}=\begin{pmatrix}7\\9\\6\\9\\1\\8\end{pmatrix}$$" >}}
**Answer**: $$\underline{u}-\underline{v}=\begin{pmatrix}10-7\\10-9\\10-6\\10-9\\10-1\\10-8\end{pmatrix}$$$$=\begin{pmatrix}3\\1\\4\\1\\5\\9\\2\end{pmatrix}$$
{{< /details >}}

{{< details title="**Exercise 20**: Imagine you have any two vectors you can think of, $\underline{x}$ and $\underline{y}$. Will $\underline{x}-\underline{y}$ and $\underline{y}-\underline{x}$ always be the same result?" >}}
**Answer**: No. When performing subtraction, order is important, as different orders will return different results.

Example:$$\begin{pmatrix}4\\3\end{pmatrix}-\begin{pmatrix}2\\1\end{pmatrix}=\begin{pmatrix}2\\2\end{pmatrix}$$$$\begin{pmatrix}2\\1\end{pmatrix}-\begin{pmatrix}4\\3\end{pmatrix}=\begin{pmatrix}-2\\-2\end{pmatrix}$$
{{< /details >}}

{{< details title="**Exercise 21**: Below are two vectors $\underline{w}$ and $\underline{z}$. It is impossible to calculate $\underline{w}+\underline{z}$ or $\underline{w}-\underline{z}$. What could you do to make these calculations possible?$$\underline{w}=\begin{pmatrix}5\\2\\4\\2\end{pmatrix}\qquad\underline{z}=\begin{pmatrix}8&6&9&9\end{pmatrix}$$Click to reveal the answer." >}}
**Answer**: Transpose either $\underline{w}$ or $\underline{z}$.

Either $\underline{w}-\underline{z}^\top$ or $\underline{w}^\top-\underline{z}$ will be working with the same number of rows and columns! 

Which one you choose depends whether you want a column vector or a row vector as the final result.
{{< /details >}}
# 07. Scalars and scalar multiplication
Scaling vectors is very important in linear algebra, as we often need to stretch out a vector longer, or squash it so that it's shorter. In other words, we can use **scalars** to scale a vector to be larger or smaller. But what is a scalar, you might ask? 

Simple - a scalar is just a number! It doesn't need to be anything special.

Let's go through an example with a vector $\underline{u}$.$$\underline{u}=\begin{pmatrix}4\\6\end{pmatrix}$$If we want to scale this vector to be double the size, we can put $2$ as a scalar like shown below:$$2\underline{u}=\begin{pmatrix}2\times4\\2\times6\end{pmatrix}$$$$=\begin{pmatrix}8\\12\end{pmatrix}$$
Effectively, we multiply all the components of a vector by the scalar.

{{< details title="**Exercise 22**: If we want to make $\underline{u}$ half the size, what can we use as a scalar?$$$$Click to reveal the answer." >}}
**Answer**: $\frac{1}{2}$ or $0.5$.$$\frac{1}{2}\underline{u}=\begin{pmatrix}2\\3\end{pmatrix}$$
{{< /details >}}

{{< details title="**Exercise 23**: Below is a vector $\underline{v}$. Write on paper what $3\underline{v}$ would be.$$\underline{v}=\begin{pmatrix}2\\1\\4\\3\end{pmatrix}$$Click to reveal the answer." >}}
**Answer**: $$3\underline{v}=\begin{pmatrix}6\\3\\12\\9\end{pmatrix}$$
{{< /details >}}

{{< details title="**Exercise 24**: Below is a vector $\underline{w}$. Write on paper what $10\underline{w}$ would be.$$\underline{w}=\begin{pmatrix}15\\12\\25\end{pmatrix}$$Click to reveal the answer." >}}
**Answer**: $$10\underline{w}=\begin{pmatrix}150\\120\\250\end{pmatrix}$$
{{< /details >}}

{{< details title="**Exercise 25**: Below is a vector $\underline{x}$. Write on paper what $\frac{1}{4}\underline{x}$ would be.$$\underline{x}=\begin{pmatrix}40\\20\\4\end{pmatrix}$$Click to reveal the answer." >}}
**Answer**: $$\frac{1}{4}\underline{x}=\begin{pmatrix}10\\5\\1\end{pmatrix}$$
{{< /details >}}
# 08. Dot product and orthogonality
Everything we've covered so far has been quite standalone, but all of that takes us into our first topic with multiple layers to it... The dot product!

The dot product is an operation we can perform with two vectors and it returns a scalar. Its purpose is to tell us **how much two vectors point in the same direction**. But how?

Lets start by going through how to calculate the dot product. This is how the dot product operator looks when used with two vectors (who could've guessed!).$$\underline{u}\cdot\underline{v}^\top$$ We'll use these two vectors below.$$\underline{u}=\begin{pmatrix}4\\4\end{pmatrix}\qquad\underline{v}=\begin{pmatrix}4\\-4\end{pmatrix}$$Before we start, the dot product has the following important rule:

**The number of columns of the left side must match the number of rows of the right side**

But $\underline{u}$ above has 1 column and 2 rows, and so does $\underline{v}$. What can we do?

Easy - we can transpose $\underline{v}$! It now has 1 row and 2 columns.$$\underline{u}=\begin{pmatrix}4\\4\end{pmatrix}\qquad\underline{v}^\top=\begin{pmatrix}4&-4\end{pmatrix}$$$\underline{u}$'s number of columns match with $\underline{v}^\top$'s number of rows, so now we can calculate the dot product. To do this, we multiply each corresponding component together, then at the end, add them all together so that we end up with a scalar. In the example above, we want to run something like this:$$\underline{u}\cdot\underline{v}^\top=\left(u_1\times v_1\right)+\left(u_2\times v_2\right)$$Let's write the exact same thing again, but plug the numbers in now:$$\underline{u}\cdot\underline{v}^\top=\left(4\times4\right)+\left(4\times-4\right)$$$$=16+(-16)=0$$
And it equals 0... Wait, that doesn't seem correct, surely? Is that supposed to happen?

Yes! It's not an error, the dot product here is 0. But why?

If we draw these two vectors on a grid, we can see that they are at a perfect $90^\circ$ angle. 

// INSERT DRAWN VECTORS HERE

This is a clue to what we said earlier about two vectors pointing in the same direction! 

{{< details title="Do you like geometry? Here's an explanation with trigonometry! (Optional)" >}}
// TO DO
{{< /details >}}

{{< details title="**Exercise 26**: Below are two vectors. Is it possible to calculate their dot product?$$\underline{u}=\begin{pmatrix}27\\21\\64\end{pmatrix}\qquad\underline{v}=\begin{pmatrix}82\end{pmatrix}$$Click to reveal the answer." >}}
**Answer**: TODO
{{< /details >}}

This brings us neatly to the idea of **Orthogonality**. Two vectors are orthogonal to each other if the angle between them is exactly $90^\circ$. This can be extremely useful when calculating geometry!

When you calculate the dot product of two vectors and get 0 as an answer, there is a $90^\circ$ angle between them, which means that those two vectors are **orthogonal**. 

In fact, if the scalar that comes out of a dot product is a positive number (more than 0), it means that the angle between the two vectors is less than $90^\circ$. 

Oppositely, if it results in a negative number (less than 0), then it means that the angle between the two vectors is more than $90^\circ$.

// ARE THESE TWO VECTORS ORTHOGONAL EXERCISES


# 09. Length of a vector

# 10. Unit vectors and normalisation

# 11. Summary
- A vector $\underline{u}$ has magnitude and direction
- Vectors are not the same as co-ordinates
- Column vectors display their components vertically
- Row vectors display their components horizontally
- $\underline{u}^\top$ is the transpose operation on $\underline{u}$, which changes a column vector to a row vector, or row vector to a column vector
- A null vector $\underline{0}$ is a special vector with only zeros
- Individual components of a vector can be accessed with $u_n$
- $\underline{u}\cdot\underline{v}$ is the dot product operation, which tells us how much two vectors point in the same direction
- To calculate dot product, the left side must have as many columns as the right side has rows
- Orthogonality is a metric of how perpendicular two vectors are
- $\underline{u}\cdot\underline{v}=0$ means $\underline{u}$ and $\underline{v}$ are orthogonal, i.e. $90^\circ$ angle between them
- $\left|\underline{u}\right|$ is the length of $\underline{u}$, which is a scalar 
- Length can be calculated using Pythagoras' Theorem
- $\underline{\hat{u}}$ is a unit vector, where $\left|\underline{\hat{u}}\right|=1$
- Any vector can be normalised into a unit vector using // TODO

> **Usage of Generative AI**
> 
> Everything in this post was written and researched by myself, based on my existing knowledge and past experience. After the post was fully complete, it was fact-checked by Claude Opus 5.5 to ensure all information presented is as accurate as possible.
> 
> Nothing you see is AI generated, and nothing on this website will ever be AI generated. All xyz words and xyz characters were hand-pressed by my fingers on a keyboard and always will be.
> 


// end part 1 here

# Orthonormality

# Vector spaces

# Properties of vectors

# Projection of a vector

# Linear combinations and span

# Basis vectors

# L1 Norm and L2 Norm

# Linear dependence and independence

# Eigenvectors and eigenvalues

# Summations (Not linear algebra)
