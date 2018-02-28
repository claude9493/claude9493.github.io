---
layout: post
title: What we talk about when we're talking about probability I
excerpt_separator:  <!--more-->
---
~~ <script type="text/x-mathjax-config">
~~ MathJax.Hub.Config({tex2jax: {inlineMath:[['$','$']]}});
~~ </script>
~~ <script type="text/javascript" src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML"></script>
 

I have learnt probability last semester, with lecturer Anyue Chen. And finally I
got a 'B'.

I prefer to write an article to summarize all I have learnt from this lecture.
Here is its first part, I wrote it during the winter break in 2018.
<!--more-->

### I. Start with Baby Set theory

In fact, we learnt some set theory at the very beginning of this course, which
seems have little relationship with probability itself. We learnt the following:

-   Elements and sets.

-   Empty set $$\emptyset$$, Universal set $$\Omega$$ and singleton $$\{ 1\}$$

-   the relationship between elements and sets, $$\in \notin$$

-   the union $$\cup$$, intersection $$\cap,$$ difference  and complement
    $$S^{C}$$, operation of sets

    -   their different laws which can be represented clearly by diagrams

    -   De Morgan's law, $$\left( A\cup B\right)^{C} = A^{C}\cap B^{C},$$
        $$\left(A\cap B\right)^{C} = A^{C}\cup B^{C}$$ , which can be extended
        to family of sets.

-   Cartesian Product, which appears in the mathematical analysis course as
    well.

-   Cardinal Number which discuss the "size" of sets.

    -   Two sets have same "size" ,i.e. $$Card\left( A\right) = Card\left(
        B\right)$$, if and only if there is a *one-to-one correspondence*
        between them (their elements).

    -   Countable sets: $$Card\left( B\right) = Card\left(\mathbb{N}\right)$$

-   Many other problems origin from cardinal number which worthies discussion in
    advanced probability.

 

### II. Probability Measure

After the set theory, we came to the real probability theory in common sense.
First, we learnt the concepts of random experiments, sample space and events,
which links strongly with previous section of set theory. Then the definition of
probability measure is given:

For a given sample space $$\Omega$$, the probability measure is a function
$$P(\bullet)$$ from the events to the real numbers that satisfies the following
axioms:

1.  P($$\Omega$$)=1

2.  $$\forall$$ event A, P(A) $$\le$$ 1

3.  if $$A$$ and $$B$$ are disjoint, then $$P(A\cup B)=P(A)+P(B)$$

Generally, probability measure is a kind of set function (a measure) defined on
the measure space$$(\Omega, \mathcal{F})$$, where $$\Omega$$denotes the sample
space and $$\mathcal{F}$$ represents the set of events. In Prof.Chen’s opinion,
$$\mathcal{F}$$ is a stage limiting the boundary of the $$P$$, the dancer.
$$(\Omega, \mathcal{F}, P)$$ is called a probability space or a probability
triple. What’s more, we learnt some of its properties, some of which are obvious
but difficult to prove.

Then combinations and permutations are introduced as methods to compute
probability, also the binomial theorem, $$\left(a+b\right )^n =
\sum_{r=1}^{n}\binom{n}{r}a^rb^{n-r}$$

For memo:

>   $$\binom{n}{0}=\binom{n}{n}=1$$

>   $$\binom{n}{r}=\binom{n}{n-r}$$

>   $$\binom{n}{r}=\binom{n-1}{r-1}+\binom{n-1}{r}$$where$$1\le r\le n$$

After that, we came to conditional probability, one of the most important
concepts.

The probability of event $$A$$ under the condition that $$B$$ has occurred
$$\rightarrow$$ The conditional probability of $$A$$ given $$B$$ $$\rightarrow$$
$$P(A|B)= \frac{P(A\cap B)}{P(B)}$$. Then some points extended from it are
discussed.

-   Multiplication Law: $$P(A\cap B)=P(B)\times P(A|B)=P(A)\times P(B|A)$$

-   $$P\left( \bigcap_{i=1}^{n}A_i\right )=P\left(A_1\cap A_2\cap ...
    \capA_n)=P(A_1)\times P(A_2|A_1)\times P(A_3|A_1\cap A_2)\times ...$$
    $$\times P(A_n|A_1\cap A_2\cap ...\cap A_{n-1})$$

-   Law of total probability, $$P(A)= \sum_{i=1}^{n}P(B_i)\cdot P(A|B_i)$$

-   **Bayes’ Rule**: $$P(B_i|A)=\frac{P(A\cap B_i)}{P(A)}=\frac{P(B_i)\cdot
    P(A|B_i)}{\sum_{k}P(B_k)P(A\cap B_k)}=\frac{P(B_i)\cdot
    P(A|B_i)}{P(B_1)\cdot P(A\cap B_1)+P(B_2)\cdot P(A|B_2)+...+P(B_n)\cdot
    P(A|B_n)}$$

At the end of this chapter, we studied another most important concept:
Independence, whose definition is simple: two events $$A$$and $$B$$ are called
independent events if $$P(A\cap B)=P(A)\cdot P(B)$$. If $$A$$ and $$B$$ are
independent, then so are $$A$$ and $$B^C$$ , and other cases. However, the
independence of n events is much more complex than the simplest one.

>   n events $$A_1, A_2,..., A_n$$ are called (mutually) independent if the
>   following hold

>   For all pairs $$A_i$$ and $$A_j$$ $$(i\neq j)$$ $$P(A_i\cap A_j)=P(A_i)\cdot
>   P(A_j)$$

>   For all triples $$A_i$$, $$A_j$$, $$A_k (i,j,k$$all different$$)$$
>   $$P(A_i\cap   A_j\cap A_k)=P(A_i)\cdot P(A_j)\cdot P(A_k)$$

>   ...... until finally

>   $$P(A_1\cap A_2\cap ...\cap A_n)=P(A_1)\cdot P(A_2)\cdot ...\cdot P(A_n)$$

 

### III. Random Variable

Till now, we have identified what’s probability. So we move to another basement
of probability, random variable. Random variable is a real-valued function
$$X(\omega)$$ defined on the points of sample space. Considering number of the
possible values, there are two kinds of random variable: discrete and
continuous. In the learning path of r.v. the have many similarities and
difference. The definition of c.d.f (Cumulative Distribution Function) for them
are almost totally same.

>   $$F(x)=P(X\le x) x\in \mathbb{R}$$

 

From the definition, we can get some great properties, such as:

-   $$P(a\le X\le b)=F(b)-F(a)$$, $$a\le b$$

-   $$0\le F(x)\le 1$$ , $$F(x)=0$$ when $$X(\omega)=\emptyset$$, $$F(x)=1$$
    when $$X(\omega)=\Omega$$

-   $$F(x)$$ is a non-decreasing function of $$x\in \mathbb{R}$$

-   c.d.f of discrete r.v. is a step-function, c.d.f.s of continuous function is
    continuous

 

But “derivatives” of c.d.f for two kinds of r.v.s have different meanings

-   For discrete r.v., its p.m.f (Probability Mass Function) is defined by:
    $$p(x)=P(X=x)$$, exactly the probability of the event that r.v. takes the
    value of x. Thus $$F(x)=P(X\le x)=\sum_{x_i\lex}p(x_i)$$

-   For continuous r.v., **a** p.d.f (Probability Density Function) is defined
    by $$f(x)=F’(x)$$. Note that $$f(x)\neq P(X=x)$$. Indeed a continuous r.v.
    has infinite number of p.d.f, since we can assign any arbitrary values to
    some points, which has no effect on the c.d.f. And by the way, any r.v. has
    just one c.d.f.

    -   Since $$f(x)=F’(x)$$, $$F(b)-F(a)=\int_a^b f(x)dx$$

    -   From $$F(x)$$ c.d.f’s non-decreasing property, we can detect that p.m.f
        and p.d.f are always non-negative

    -    

Actually, we learnt the three kinds of r.v’s function while learning many
classic random variables. Such as

Bernoulli r.v., Binomial, Poisson, Normal and exponential distribution and so
on.

 

Besides, the function of r.v.s is also important. Usually, function of a random
variable is also a random variable. To get its p.d.f and c.d.f, we can deduce it
by the definition of c.d.f and properties of probability. We can also use the
following theorem:

Let $$X$$ be a continuous random variable having p.d.f $$f(x)$$. Suppose that
$$g(x)$$ is a strictly monotone differentiable function of $$x$$. Then the
random variable $$Y$$ defined by $$Y = g(X)$$ has a p.d.f given by:

$$
f_Y(y) =f_X\left[g^{-1}(y)) \right ]\cdot \left | \frac{d}{dy}g^{-1}(y) \right |
$$

if $$y=g(x)$$for some $$x$$, else $$f_Y(y)=0$$ ($$y\neq g(x)$$ for all $$x$$)

 
