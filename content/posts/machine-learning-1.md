---
title: Machine Learning 01 := Getting Started with Linear Algebra
date: 2026-10-06
draft: false
tags:
  - machine-learning
---

As this year, my final year project at university is about comparing different machine learning algorithms, I thought I would start a series of blog posts exploring machine learning from the start!

- 01 := Getting Started with Linear Algebra <== **You are here**
- 02 := AI and ML Fundamentals
- ...

The target audience for these is anyone; regardless of whether you have a maths/computer science background, or you only went as far as GCSE Maths. Ultimately, as someone who's own maths is okay but not strong, I aim to make these posts into what I wish I would've read when I was first learning about machine learning.

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
# 01. What is Linear Algebra?
Linear algebra is the area of maths that is all about **vectors**. It's an extremely important area of maths that is responsible for many areas of our modern world, such as machine learning, making movies and playing games on our computers and phones, solving problems in engineering and physics, to name a few!

When people hear the words "linear algebra" for the first time, they think of rearranging formulas and solving equations. However, we don't need to calculate this by hand much in machine learning, therefore it's not super useful to know. So you won't find any of that here!
# 02. So then, what is a vector?
A vector is a structure containing a list of numbers. Each number in the list represents a unique dimension. 

All of these numbers come together to describe two important properties: **magnitude** and **direction**. But what do these mean?

Let's see what this looks like by starting with a number line and a one-dimensional vector.
$$\begin{pmatrix}5\end{pmatrix}$$
![Visualisation of (5)](/images/machine-learning/01/02-example-1d.png)
- The **direction** of a vector is which way it is pointing towards. 
  In the number line above, you can see that the vector is pointing towards the right. If the vector was a negative number (e.g. $-5$), the vector would be pointing towards the left.
- The **magnitude** of a vector is how far it points in a direction. 
  If a vector's arrow is shorter, it has a smaller magnitude. If a vector's arrow is longer, it has a larger magnitude.

{{< details title="**Exercise 1**: Which direction will this vector point on a number line?$$\begin{pmatrix}-2\end{pmatrix}$$Click to reveal the answer." >}}
**Answer**: It will point left.
![Visualisation of (-2)](/images/machine-learning/01/02-exercise-01.png)
{{< /details >}}

Okay, that makes sense. Now how about we scale up to a two-dimensional vector!
$$\begin{pmatrix}4\\3\end{pmatrix}$$
Since we now have two dimensions, the direction of the vector can now go upwards or downwards, in addition to left or right. The magnitude changes too, since we now have a diagonal line.

![Visualisation of (4\\4)](/images/machine-learning/01/02-example-2d.png)

We can keep going; what about a three-dimensional vector?
$$\begin{pmatrix}5\\6\\4\end{pmatrix}$$
![Visualisation of (5\\6\\4)](/images/machine-learning/01/02-example-3d.png)

We can still keep going even further; how about a ten-dimensional vector?
$$\begin{pmatrix}5\\2\\6\\6\\9\\4\\1\\3\\7\\8\end{pmatrix}$$
Well, okay, I can't create a visualisation for that one. But they absolutely still have direction and magnitude! Vectors with more than three dimensions are very common in machine learning.
# 03. Vectors vs Co-ordinates
At this point, you may be questioning "okay, so vectors are just like co-ordinates".

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
$$\text{Transpose: }\top$$
Transposing a vector means changing the shape of the vector to the other type we just mentioned, without changing anything else about it. We write the transpose operator on the top right side of a vector.$$\begin{pmatrix}1\\2\\3\end{pmatrix}^\top=\begin{pmatrix}1&2&3\end{pmatrix}$$
The shape of this vector was 3 rows and 1 column before, but now after transposing, it is 1 row and 3 columns.

We can also do this the other way round...$$\begin{pmatrix}4&5&6\end{pmatrix}^\top=\begin{pmatrix}4\\5\\6\end{pmatrix}$$
And that's all there is to it!

{{< details title="**Exercise 2**: Below is a vector $\underline{u}$. Write on paper what $\underline{u}^\top$ would be.$$\underline{u}=\begin{pmatrix}10\\4\\6\end{pmatrix}$$Click to reveal the answer." >}}
**Answer**: $$\underline{u}^\top=\begin{pmatrix}10&4&6\end{pmatrix}$$
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
It's possible for us to add two vectors together, or subtract one vector from another, just like in everyday maths. However, there is one important constraint that must be followed:

**Vectors MUST have the same number of rows and columns to be added or subtracted**

Vectors with different dimensionality are incompatible!

{{< details title="**Exercise 14**: Below are two vectors $\underline{u}$ and $\underline{v}$. Can $\underline{u}+\underline{v}$ be calculated?$$\underline{u}=\begin{pmatrix}3\\9\\7\\6\end{pmatrix}\qquad\underline{v}=\begin{pmatrix}41\\8\\77\\0\end{pmatrix}$$Click to reveal the answer." >}}
**Answer**: Yes. $\underline{u}$ and $\underline{v}$ have the same amount of rows and columns.
{{< /details >}}

{{< details title="**Exercise 15**: Below are two vectors $\underline{u}$ and $\underline{v}$. Can $\underline{u}+\underline{v}$ be calculated?$$\underline{u}=\begin{pmatrix}41714\\86827\\90019\\47547\\9865\\22938\end{pmatrix}\qquad\underline{v}=\begin{pmatrix}63592\\52055\\38177\\5381\\39738\end{pmatrix}$$Click to reveal the answer." >}}
**Answer**: No. $\underline{v}$ has one less row than $\underline{u}$, so it is impossible to calculate $\underline{u}+\underline{v}$ without changing their dimensions.
{{< /details >}}



Now lets try adding two vectors together, with $\underline{u}$ and $\underline{v}$ below as an example.$$\underline{u}=\begin{pmatrix}3\\2\end{pmatrix}\qquad\underline{v}=\begin{pmatrix}1\\4\end{pmatrix}$$
To do this, we add each corresponding component together, and the final result is one single vector.$$\underline{u}+\underline{v}=\begin{pmatrix}3+1\\2+4\end{pmatrix}$$$$=\begin{pmatrix}4\\6\end{pmatrix}$$We can also visualise how these vectors are added together. The red line represents $\underline{u}$, the blue line represents $\underline{v}$ and the green line represents $\underline{u}+\underline{v}$.
![Visualisation of u+v](/images/machine-learning/01/06-example-addition.png)
Not so hard, right? Try these exercises for yourself!

{{< details title="**Exercise 17**: Below are two vectors $\underline{u}$ and $\underline{v}$. Write out on paper $\underline{u}+\underline{v}$.$$\underline{u}=\begin{pmatrix}10\\6\\5\\8\\-1\end{pmatrix}\qquad\underline{v}=\begin{pmatrix}5\\3\\2\\0\\3\end{pmatrix}$$Click to reveal the answer." >}}
**Answer**: $$\underline{u}+\underline{v}=\begin{pmatrix}15\\9\\7\\8\\2\end{pmatrix}$$
{{< /details >}}

Subtracting one vector from another vector is almost an identical process to adding two vectors. Let's use a new $\underline{u}$ and $\underline{v}$ below:$$\underline{u}=\begin{pmatrix}7\\9\\3\end{pmatrix}\qquad\underline{v}=\begin{pmatrix}4\\5\\5\end{pmatrix}$$To calculate $\underline{u}-\underline{v}$, we subtract each component of $\underline{v}$ from the corresponding component of $\underline{u}$, like this:
$$\underline{u}-\underline{v}=\begin{pmatrix}7-4\\9-5\\3-5\end{pmatrix}$$$$=\begin{pmatrix}3\\4\\-2\end{pmatrix}$$

{{< details title="**Exercise 19**: Below are two vectors $\underline{u}$ and $\underline{v}$. Write out on paper $\underline{u}-\underline{v}$.$$\underline{u}=\begin{pmatrix}10\\10\\10\\10\\10\\10\end{pmatrix}\qquad\underline{v}=\begin{pmatrix}7\\9\\6\\9\\5\\1\end{pmatrix}$$Click to reveal the answer." >}}
**Answer**: $$\underline{u}-\underline{v}=\begin{pmatrix}10-7\\10-9\\10-6\\10-9\\10-5\\10-1\end{pmatrix}$$$$=\begin{pmatrix}3\\1\\4\\1\\5\\9\end{pmatrix}$$
{{< /details >}}
# 07. Scalars and scalar multiplication
Scaling vectors is very important in linear algebra, as we often need to stretch out a vector to be longer, or squash it so that it's shorter. In other words, we can use **scalars** to scale a vector to be larger or smaller. 

But what is a scalar, you might ask? 

Simple - a scalar is just a number! It doesn't need to be anything special.

Let's go through an example with a vector $\underline{u}$.$$\underline{u}=\begin{pmatrix}4\\6\end{pmatrix}$$If we want to scale this vector to be double the size, we can put $2$ as a scalar like shown below:$$2\underline{u}=\begin{pmatrix}2\times4\\2\times6\end{pmatrix}$$$$=\begin{pmatrix}8\\12\end{pmatrix}$$
Effectively, we multiply all the components of a vector by the scalar.

{{< details title="**Exercise 22**: If we want to make $\underline{u}$ half the size, what can we use as a scalar?$$$$Click to reveal the answer." >}}
**Answer**: $\frac{1}{2}$ or $0.5$.$$\frac{1}{2}\underline{u}=\begin{pmatrix}2\\3\end{pmatrix}$$
{{< /details >}}

{{< details title="**Exercise 23**: Below is a vector $\underline{v}$. Write on paper what $3\underline{v}$ would be.$$\underline{v}=\begin{pmatrix}2\\1\\4\\3\end{pmatrix}$$Click to reveal the answer." >}}
**Answer**: $$3\underline{v}=\begin{pmatrix}6\\3\\12\\9\end{pmatrix}$$
{{< /details >}}

{{< details title="**Exercise 25**: Below is a vector $\underline{x}$. Write on paper what $\frac{1}{4}\underline{x}$ would be.$$\underline{x}=\begin{pmatrix}40\\20\\4\end{pmatrix}$$Click to reveal the answer." >}}
**Answer**: $$\frac{1}{4}\underline{x}=\begin{pmatrix}10\\5\\1\end{pmatrix}$$
{{< /details >}}
# 08. Dot product and orthogonality
Everything we've covered so far has been quite standalone, but all of that takes us into our first topic with multiple layers to it... The dot product!

The dot product is an operation we can perform with two vectors and it returns a scalar. Its purpose is to tell us **how much two vectors point in the same direction**. But how?

Lets start by going through how to calculate the dot product. This is how the dot product operator looks when used with two vectors (who could've guessed!).$$\text{Dot product: }\underline{u}^\top\cdot\underline{v}$$ We'll use these two vectors below.$$\underline{u}=\begin{pmatrix}4\\4\end{pmatrix}\qquad\underline{v}=\begin{pmatrix}4\\-4\end{pmatrix}$$Before we start, the dot product has the following important rule:

**The number of columns of the left side must match the number of rows of the right side**

But $\underline{u}$ above has 1 column and 2 rows, and so does $\underline{v}$. What can we do?

Easy - we can transpose $\underline{u}$! It now has 1 row and 2 columns.$$\underline{u}^\top=\begin{pmatrix}4&4\end{pmatrix}\qquad\underline{v}=\begin{pmatrix}4\\-4\end{pmatrix}$$$\underline{u}$'s number of columns match with $\underline{v}^\top$'s number of rows, so now we can calculate the dot product. 

{{< details title="**Exercise 26**: Below are two vectors. Is it possible to calculate their dot product?$$\underline{u}=\begin{pmatrix}27\\21\\64\end{pmatrix}\qquad\underline{v}=\begin{pmatrix}82&17&46&52\end{pmatrix}$$Click to reveal the answer." >}}
**Answer**: No, $\underline{v}$ has more dimensions than $\underline{u}$.
{{< /details >}}

{{< details title="**Exercise 27**: Below are two vectors. Is it possible to calculate their dot product?$$\underline{u}=\begin{pmatrix}51\\321\\5\end{pmatrix}\qquad\underline{v}=\begin{pmatrix}10\\28\\207\end{pmatrix}$$Click to reveal the answer." >}}
**Answer**: In their current state, no. $\underline{u}$'s number of columns does not match $\underline{v}$'s number of rows.

If you transpose $\underline{u}$ then the answer becomes yes!
{{< /details >}}

To calculate the dot product, we multiply each corresponding component together, then at the end, add them all together so that we end up with a scalar. In the example above, we want to run something like this:$$\underline{u}^\top\cdot\underline{v}=\left(u_1\times v_1\right)+\left(u_2\times v_2\right)+\left(u_3\times v_3\right)+\cdots$$Let's write the exact same thing again, but plug the numbers in now:$$\underline{u}^\top\cdot\underline{v}=\left(4\times4\right)+\left(4\times-4\right)$$$$=16+(-16)=0$$
And it equals 0... Wait, that doesn't seem correct, surely? Is that supposed to happen?

Yes! It's not an error, the dot product here is 0. But why?

If we draw these two vectors on a grid, we can see that they are at a perfect $90^\circ$ angle. 
![Visualisation of Orthogonality](/images/machine-learning/01/08-example-orthogonality.png)
This is a clue to what we said earlier about two vectors pointing in the same direction! 

{{< details title="**Exercise 29**: Below are two vectors $\underline{u}^\top$ and $\underline{v}$. Work out on paper $\underline{u}^\top\cdot\underline{v}$.$$\underline{u}^\top=\begin{pmatrix}5&3\end{pmatrix}\qquad\underline{v}=\begin{pmatrix}4\\5\end{pmatrix}$$Click to reveal the answer." >}}
**Answer**: $$\underline{u}^\top\cdot\underline{v}=\left(5\times4\right)+\left(3\times5\right)$$$$=20+15=35$$
{{< /details >}}

{{< details title="**Exercise 31**: Below are two vectors $\underline{y}^\top$ and $\underline{z}$. Work out on paper $\underline{y}^\top\cdot\underline{z}$.$$\underline{y}^\top=\begin{pmatrix}3&-4&5\end{pmatrix}\qquad\underline{z}=\begin{pmatrix}4\\3\\0\end{pmatrix}$$Click to reveal the answer." >}}
**Answer**: $$\underline{y}^\top\cdot\underline{z}=\left(3\times4\right)+\left(-4\times3\right)+\left(5\times0\right)$$$$=12+(-12)+0=0$$
{{< /details >}}

This brings us neatly to the idea of **Orthogonality**. Two vectors are orthogonal to each other if the angle between them is exactly $90^\circ$. This can be extremely useful when calculating geometry!

When you calculate the dot product of two vectors and get 0 as an answer, there is a $90^\circ$ angle between them, which means that those two vectors are **orthogonal**. 

In fact, if the scalar that comes out of a dot product is a positive number (more than 0), it means that the angle between the two vectors is less than $90^\circ$. 

Oppositely, if it results in a negative number (less than 0), then it means that the angle between the two vectors is more than $90^\circ$.

Watch the demo below of a vector rotating around $\begin{pmatrix}0,0\end{pmatrix}$ to see how the dot product changes as the blue vector rotates.

<iframe src="https://www.desmos.com/calculator/ag2pel1vy3?embed" width="500" height="500" style="border: 1px solid #ccc" frameborder=0></iframe>

{{< details title="**Exercise 32**: You've calculated the dot product of two vectors and got the answer $0$. Are the two vectors orthogonal? $$$$Click to reveal the answer." >}}
**Answer**: Yes.
{{< /details >}}

{{< details title="**Exercise 33**: You've calculated the dot product of two vectors and got the answer $-2$. Are the two vectors orthogonal? $$$$Click to reveal the answer." >}}
**Answer**: No. They are orthogonal only if their dot product is 0.
{{< /details >}}

{{< details title="**Exercise 34**: You've calculated the dot product of two vectors and got the answer $0.0001$. Are the two vectors orthogonal? $$$$Click to reveal the answer." >}}
**Answer**: No. Two vectors are orthogonal only if their dot product is 0, no exceptions!
{{< /details >}}

{{< details title="**Exercise 35**: Below are two vectors $\underline{u}^\top$ and $\underline{v}$. Are they orthogonal?$$\underline{u}^\top=\begin{pmatrix}1&2&3&4\end{pmatrix}\qquad\underline{v}=\begin{pmatrix}4\\-3\\2\\-1\end{pmatrix}$$Click to reveal the answer." >}}
**Answer**: Yes, they are orthogonal because their dot product equals 0.$$\underline{u}^\top\cdot\underline{v}=\left(1\times4\right)+\left(2\times-3\right)+\left(3\times2\right)+\left(4\times-1\right)$$$$=4+(-6)+6+(-4)=0$$
{{< /details >}}
# 09. Length of a vector
Earlier, we mentioned that vectors have two properties: **direction** and **magnitude**. With the dot product, we can work out the rough direction between two vectors. It's also possible to work out the precise angle using some fancy trigonometry stuff, which is beyond the scope of this article, but just know it exists!

But how can we work out the other property of a vector, magnitude?

The magnitude of a vector is also known as its length. The greater a vector's magnitude, the longer it will visually be if we draw it out. The lesser a vector's magnitude, the shorter its length will be.

In machine learning, calculating the length of a vector is very important. Especially for the first ML algorithm we'll cover in the next post!

We also need to introduce some new notation. When you add a straight line on both sides of a vector, this means you are referring to its length, which is a scalar.$$\text{Length of }\underline{u}\text{: }\left|\underline{u}\right|$$So how do we calculate the length of $\underline{u}$? 

It's easy and you've likely learned it before in GCSE Maths or at least heard of it - Pythagoras' Theorem!

Pythagoras is the simple rule for finding the length of the longest side of a triangle. However, we can also use it here for finding the length of a vector.

Let's briefly drop linear algebra for a moment and just focus on understanding the Pythagoras Theorem itself. We can start with this triangle below, which has three sides: $a$, $b$ and $c$.
![Triangle example](/images/machine-learning/01/09-example-pythagoras.png)
From just reading the image, we can see that side $a$ has a length of 3 and side $b$ has a length of 2. 

We also have side $c$, but the length is more difficult to measure in this image. So how do we find the length of it?

Easy - there is a simple yet powerful formula for this, i.e. Pythagoras!$$a^2+b^2=c^2$$We basically say that for side $c$'s length, $c^2$ is equal to $a^2+b^2$. 

But this is side $c$'s length squared, not side $c$'s length. So as it is, it's not very useful.

The fix: apply a square root on both the left side and right side of the equals symbol! $$\sqrt{a^2+b^2}=c$$_(When you square root a squared number, that just removes the exponent and you're left with the original number)_

Let's plug in the numbers from our triangle into Pythagoras:$$\sqrt{3^2+2^2}=\sqrt{9+4}=\sqrt{13}$$We're left with square root of 13 as our answer for the length of $c$. 

If you have a calculator, you can work out the precise number with decimals (which would be $3.605$), but if not then leaving it as $\sqrt{13}$ is fine!

Lets move back to linear algebra with a new vector $\underline{u}$.$$\underline{u}=\begin{pmatrix}4\\6\end{pmatrix}$$We need to find out the length of $\underline{u}$, in other words, calculate $\left|\underline{u}\right|$. How do we do this?

Easy again - it's still with Pythagoras! In essence, we can think of the vector's components as sides $a$ and $b$ of a right angled triangle, and the vector itself is side $c$. We just need to adapt Pythagoras slightly to linear algebra, but it's basically the same. 

Instead of $a$ and $b$, we insert the individual components of the vector, $u_1$ and $u_2$.$$\left|\underline{u}\right|=\sqrt{u_1^2+u_2^2}$$Lets plug in the numbers from $\underline{u}$ again:$$\left|\underline{u}\right|=\sqrt{4^2+6^2}$$$$=\sqrt{16+36}$$$$=\sqrt{52}$$And there we have our answer, $\left|\underline{u}\right|$ is $\sqrt{52}$ or $7.211$. Sounds about right!

We can expand this further as it's common to calculate the length of a vector in more than two dimensions. How about five dimensions?

Let's go through another example with a new vector below, we'll call it $\underline{v}$.$$\underline{v}=\begin{pmatrix}5\\2\\4\\3\\1\end{pmatrix}$$How do we calculate the length of a vector with more than two, or even three dimensions? Well, it doesn't change very much, the only difference is we need to square the extra numbers!$$\left|\underline{u}\right|=\sqrt{v_1^2+v_2^2+v_3^2+v_4^2+v_5^2}$$Now lets plug our numbers in from $\underline{v}$.$$\left|\underline{v}\right|=\sqrt{5^2+2^2+4^2+3^2+1^2}$$$$=\sqrt{25+4+16+9+1}$$$$=\sqrt{55}$$Now you know how to calculate the length of a vector!
# 10. Unit vectors and normalisation
This brings us onto the last topic of this post, which is about unit vectors. We need to introduce one more bit of new notation, which looks like a vector wearing a little hat.$$\text{Unit vector: }\underline{\hat{u}}$$A unit vector is a vector that has a length of exactly 1. This means that if you tried to use the previous section to work out the length of a unit vector, you'd end up with exactly $1.0$ recurring!$$\left|\underline{u}\right|\text{ of any vector }\underline{\hat{u}}=1$$This means that the magnitude of unit vectors is fixed, so now they purely represent a direction. Also, because unit vectors cannot extend any longer or shorter than a magnitude of 1, if we map out all possible unit vectors, we actually end up with a circle.
![Unit vector circle example](/images/machine-learning/01/10-example-unit-circle.png)
There is also a way we can turn _any_ vector into a unit vector. This is called **normalisation**.

There's a formula we can use to scale the length of any vector, from anything to 1, and it looks like this:$$\frac{1}{\left|\underline{u}\right|}\underline{u}=\underline{\hat{u}}$$Essentially, what we are doing is:
- Calculating what its length is
- Dividing 1 by that length, so we end up with a scalar
- Applying that number as a scalar on $\underline{u}$ to get $\underline{\hat{u}}$

If a vector's length is already more than 1, we'll end up with a scalar less than 1 and effectively be **shrinking** it to turn it into a unit vector. 

On the other hand, if a vector's length is already less than 1, we'll end up with a scalar bigger than 1 and effectively be **stretching** it to turn it into a unit vector.

Lets go through an example with one last vector below, again called $\underline{u}$.$$\underline{u}=\begin{pmatrix}2\\5\end{pmatrix}$$It's easy to guess that $\underline{u}$ is not a unit vector, even without working out $\left|\underline{u}\right|$, because it already looks like it's length will be longer than 1.

First, let's calculate $\left|\underline{u}\right|$.$$\left|\underline{u}\right|=\sqrt{2^2+5^2}$$$$=\sqrt{4+25}$$$$=\sqrt{29}$$Now lets divide 1 by $\sqrt{29}$. I'll round it to 6 decimals, otherwise it'll continue forever...$$\frac{1}{\sqrt{29}}=0.185695\cdots$$Now we scale $\underline{u}$ by $0.185695$...$$0.185695\underline{u}=\underline{\hat{u}}$$And now our unit vector is complete! It now has a length of 1.
# 11. Summary
- A vector $\underline{u}$ has magnitude and direction
- Vectors are not the same as co-ordinates
- Column vectors display their components vertically
- Row vectors display their components horizontally
- $\underline{u}^\top$ is the transpose operation on $\underline{u}$, which changes a column vector to a row vector, or row vector to a column vector
- A null vector $\underline{0}$ is a special vector with only zeros
- Individual components of a vector can be accessed with $u_n$
- $\underline{u}^\top\cdot\underline{v}$ is the dot product operation, which tells us how much two vectors point in the same direction
- To calculate dot product, the left side must have as many columns as the right side has rows
- Orthogonality is a metric of how perpendicular two vectors are
- $\underline{u}^\top\cdot\underline{v}=0$ means $\underline{u}$ and $\underline{v}$ are orthogonal, i.e. $90^\circ$ angle between them
- $\left|\underline{u}\right|$ is the length of $\underline{u}$, which is a scalar 
- Length can be calculated using Pythagoras' Theorem
- $\underline{\hat{u}}$ is a unit vector, where $\left|\underline{u}\right|=1$
- Any vector can be normalised into a unit vector using $\frac{1}{\left|\underline{u}\right|}\underline{u}=\underline{\hat{u}}$

I hope this has been easy to understand and interesting for you to read, and in the next post we will go over the basics of AI and machine learning! 

If you learned something or found this beneficial, I'd be grateful if you could follow me on GitHub [here](https://github.com/michaelchips) :)

> **Usage of Generative AI**
> 
> Everything in this post was written by me, based on my existing knowledge and online research. After the post was fully written, it was fact-checked by Claude Opus 5.5 to ensure all information presented is as accurate as possible. In total, 3 corrections which it suggested have been implemented.
> 
> Nothing you see is AI generated, and nothing on this website will ever be AI generated. All xyz words and xyz characters were hand-pressed by my fingers on a keyboard and always will be. Images are generated using Desmos.
> 

# Extra Exercises

{{< details title="**Exercise 3**: Below is a vector $\underline{v}$. Write on paper what $\underline{v}^\top$ would be.$$\underline{v}=\begin{pmatrix}a\\b\\c\end{pmatrix}$$Click to reveal the answer." >}}
**Answer**: $$\underline{v}^\top=\begin{pmatrix}a&b&c\end{pmatrix}$$
{{< /details >}}

{{< details title="**Exercise 7**: Below is a column vector $\underline{z}$. Write on paper what $\left(\underline{z}^\top\right)^\top$ would be.$$\underline{z}=\begin{pmatrix}3\\1\\4\end{pmatrix}$$Click to reveal the answer." >}}
**Answer**: $$\left(\underline{z}^\top\right)^\top=\begin{pmatrix}3\\1\\4\end{pmatrix}$$
Transpose a vector, transpose it again, you end up with the same thing as before!
{{< /details >}}

{{< details title="**Exercise 16**: Below are two vectors $\underline{u}$ and $\underline{v}$. Can $\underline{u}+\underline{v}$ be calculated?$$\underline{u}=\begin{pmatrix}1\\3\\5\end{pmatrix}\qquad\underline{v}=\begin{pmatrix}2&4&6\end{pmatrix}$$Click to reveal the answer." >}}
**Answer**: No. $\underline{u}$ has 3 rows and 1 column, while $\underline{v}$ has 1 row and 3 columns.
{{< /details >}}

{{< details title="**Exercise 18**: Imagine you have any two vectors you can think of, $\underline{x}$ and $\underline{y}$. Will $\underline{x}+\underline{y}$ and $\underline{y}+\underline{x}$ always be the same result?$$$$Click to reveal the answer." >}}
**Answer**: Yes. When performing addition, order does not matter, therefore you will always get the same result.
{{< /details >}}

{{< details title="**Exercise 20**: Imagine you have any two vectors you can think of, $\underline{x}$ and $\underline{y}$. Will $\underline{x}-\underline{y}$ and $\underline{y}-\underline{x}$ always be the same result?$$$$Click to reveal the answer." >}}
**Answer**: No. When performing subtraction, order is important, as different orders will return different results.

Example:$$\begin{pmatrix}4\\3\end{pmatrix}-\begin{pmatrix}2\\1\end{pmatrix}=\begin{pmatrix}2\\2\end{pmatrix}$$$$\begin{pmatrix}2\\1\end{pmatrix}-\begin{pmatrix}4\\3\end{pmatrix}=\begin{pmatrix}-2\\-2\end{pmatrix}$$
The only exception to this is when both vectors are the same, then the result of subtracting one from the other will be a null vector, regardless of the order.
{{< /details >}}

{{< details title="**Exercise 21**: Below are two vectors $\underline{w}$ and $\underline{z}$. It is impossible to calculate $\underline{w}+\underline{z}$ or $\underline{w}-\underline{z}$. What could you do to make these calculations possible?$$\underline{w}=\begin{pmatrix}5\\2\\4\\2\end{pmatrix}\qquad\underline{z}=\begin{pmatrix}8&6&9&9\end{pmatrix}$$Click to reveal the answer." >}}
**Answer**: Transpose either $\underline{w}$ or $\underline{z}$.

Either $\underline{w}-\underline{z}^\top$ or $\underline{w}^\top-\underline{z}$ will be working with the same number of rows and columns! 

Which one you choose depends whether you want a column vector or a row vector as the final result.
{{< /details >}}

{{< details title="**Exercise 24**: Below is a vector $\underline{w}$. Write on paper what $10\underline{w}$ would be.$$\underline{w}=\begin{pmatrix}15\\12\\25\end{pmatrix}$$Click to reveal the answer." >}}
**Answer**: $$10\underline{w}=\begin{pmatrix}150\\120\\250\end{pmatrix}$$
{{< /details >}}

{{< details title="**Exercise 28**: Below are two vectors. Is it possible to calculate their dot product?$$\underline{u}^\top=\begin{pmatrix}2673&2411&1164&3151&988\end{pmatrix}\qquad\underline{v}=\begin{pmatrix}7172\\1488\\1612\\6400\\89\end{pmatrix}$$Click to reveal the answer." >}}
**Answer**: Yes. $\underline{u}^\top$ has 5 columns and $\underline{v}$ has 5 rows.
{{< /details >}}

{{< details title="**Exercise 30**: Below are two vectors $\underline{w}^\top$ and $\underline{x}$. Work out on paper $\underline{w}^\top\cdot\underline{x}$.$$\underline{w}^\top=\begin{pmatrix}4&-6\end{pmatrix}\qquad\underline{x}=\begin{pmatrix}-5\\5\end{pmatrix}$$Click to reveal the answer." >}}
**Answer**: $$\left(4\times-5\right)+\left(-6\times5\right)$$$$=-20+(-30)=-50$$
{{< /details >}}

{{< details title="**Exercise 36**: Below are two vectors $\underline{u}$ and $\underline{v}$. Are they orthogonal?$$\underline{u}=\begin{pmatrix}2\\-1\\3\end{pmatrix}\qquad\underline{v}=\begin{pmatrix}4\\5\\-1\end{pmatrix}$$Click to reveal the answer." >}}
**Answer**: Yes, their dot product is 0, therefore they are orthogonal.$$\left(2\times4\right)+\left(-1\times5\right)+\left(3\times-1\right)$$$$=8+(-5)+(-3)=0$${{< /details >}}