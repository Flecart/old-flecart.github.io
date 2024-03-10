---
layout: page
permalink: notes/inverse-transform
tags: italian
title: Inverse Transform
---

How can we transform a uniform into a random variable?
It is true that we have 

$$
F(x) = \int _{-\infty}^{x} f(t) \, dt 
$$

A volte la densità non è definita, mentre la funzione cumulativa lo è , per questo spesso cominciamo a definire partendo dalla definizione.

Suppose we have a $$x \sim F_{X}(x)$$ where $$F$$ is a cumulative distribution function, same thing, we just need to take the set, normal *cumulative distribution function* that we saw a lot in other courses.

$$
F_{X}(x) = \mathbb{P}(X \leq x)
= \int_{-\infty}^{x} f_{X}(z) \, dz
$$

### Generalized inverse
#### Definition
We want to have an **inverse of the cdf**, but i don't know why.
By some definition the transformation is still a random variable.
The definition of the generalized inverse is:

$$
F_{X}^{-1}(u) = inf \left\{ x; F_{X}(x) \geq u \right\} 
$$

This has sense because we know that the inverse is a continuous function (we do or not?).
This is useful because when we have a *cumulative probability distribution this allows to recreate the original random variable distribution*, and it's quite easy to get it in this way.

#### Probability Inverse transform
Sample from $$X$$ when it's difficult to sample from that distribution (for example function difficult to calculate?, Difficult to implement function?)

**Requirements**:
1. I know the functional form of $$F_{X}(x)$$
2. $$X$$ in continuous.

For the exam you will be given the cumulative distribution and you need to use this theorem to sample
#### Theorem
The inverse distribution the cumulative of the uniform distribution is the same for that random variable

$$
U \sim F_{X}(x) \iff \mathbb{P}(Y \leq x) =X
$$

Where $$Y = F_{X}^{-1}(U)$$ this is just the definition of the cumulative function, the catch is the ???

1. $$F_{X}(u)$$ is continuous then it is invertible
2. If $$U \sim Unif(0, 1)$$ then the c.d.f is easy, and it's equal to 
$$ u \in \left[ 0, 1 \right]: F_{U}(u) =
\begin{cases}
0, u \leq 0 \\
u, 0\leq u\leq 1 \\
1, u \leq 1
\end{cases}
$$
And this is easy. This is proved to be the only distribution with this property, that the CDF is an identify
3. $$F_{X}(X) = U$$ this is also called **PIT** See [here]([https://stats.stackexchange.com/questions/161635/why-is-the-cdf-of-a-sample-uniformly](https://stats.stackexchange.com/questions/161635/why-is-the-cdf-of-a-sample-uniformly)-distributed) for proof (it's cool)

#### Proof 1

$$
\mathbb{P}(F_{X}^{-1}(U) \leq x) = \mathbb{P}(F_{X}\left[ F_{X}^{-1}(U) \right] \leq F_{X}(x))
= \mathbb{P}(U \leq F_{X}(x)) = F_{U}[F_{X}(x)] = F_{X}(x)
$$

In the first passage we used that the cumulative distribution function is monotonically increasing, in the second a clear property for the inverse, and at the end we used a property of the cumulative uniform distribution.

#### Proof 2
Proof of the same fact, so we have:
Proof of the point 3.

$$
U = F_{U}(u) = \mathbb{P}(U \leq u) = \mathbb{P}(F_{X}(X) \leq F_{X}(x))
= \mathbb{P}(F_{X}^{-1}(F_{X}(X)) \leq F_{X}^{-1}(F_{X}(x)) )
= \mathbb{P}(X \leq x)
= F_{X}(x)
$$


After you have this you can just use the inverse ->

$$
F_{X}^{-1}(U) = X
$$

So now you can sample.
#### Example of application

$$
X \sim Exp(\lambda = 1)
$$

And given $$F_{X}(x) = 1 - e^{-x}$$, with $$x \in \mathbb{R}^{+} \cup \left\{ 0 \right\}$$
Find the value of $$X$$ random variable.

**Solution example:**
1. $$F_{X}(X) = U$$, then set up the equation and solve 

$$
1 - e^{-X} = U \implies
e^{-X} = 1 - U \implies
X = -\log (1 - U)
$$

We can notice that $$1 - U$$ and $$U$$ are both uniform distribution, so the above is the same as $$X = -\log(U)$$
And in this way you get the correct random variable. Now we can **sample from the uniform** and get the correct result! -> **Direct transformation method**.
With this process we prooved that $$-\log U \sim Exp(\lambda = 1)$$

### Famous function CDF
#### Logistic function
This is a function very similar to that used in [Logistic Regression](/notes/logistic-regression).
We have $$X \sim \text{Logistic}(\mu ; \beta)$$, then

$$
F_{X}(x) = \frac{1}{1 + e^{-(x - \mu)/\beta}}
$$

Let's make the derivation:

$$
U = F_{X}(X) = \frac{1}{1 + e^{-(X - \mu)/\beta}} \implies
1 + e^{-(X - \mu)/\beta} = \frac{1}{U} \implies
-(X - \mu)/\beta = \log(\frac{1}{U} - 1)
$$


$$
\implies X = -\beta \log\left( \frac{1}{U} - 1 \right) + \mu
$$

Where $$\beta$$ and $$\mu$$ are parameters of the distribution.

#### Cauchy distribution
How to simulate data from a Cauchy distribution?

$$
F_{X}(x) = \frac{1}{2} + \frac{1}{\pi}\arctan((x - \mu) / \sigma)
$$


**The derivation**

$$
U = F_{X}(X) 
= \frac{1}{2} + \frac{1}{\pi}\arctan((X - \mu) / \sigma)
\implies \tan(\pi\left( U - \frac{1}{2} \right)) = (X - \mu)/\sigma
\implies
X = \sigma \cdot \tan(\pi\left( U - \frac{1}{2} \right)) + \mu
$$

So also in this case we have a way to sample a Cauchy distribution by just manipulating a uniform distribution.

How for the Gaussian?

$$
\Phi(x) = \int _{-\infty}^{x}f_{X}(z) \, dz 
\int _{-\infty}^{x} \frac{1}{\sqrt{ 2\pi } \sigma^{2}} \exp \left\{  - \frac{(z - \mu)^{2}}{2\sigma^{2}} \right\}  \, dz
$$

Doesn't have a clear evaluation function because it's difficult, in R it uses the Probability inverse transform.

#### Empirical C.D.F
The definition is simple:, if we have a *i.i.d.* sample 

$$
(X_{1}, \dots, X_{n}) :
\hat{F}_{X, m}(x) = \frac{1}{n} \cdot \sum_{i = 1}^{n} \mathbb{1}(X_{i} \leq x)
$$

It's just the sum of all the sampled data that is lower than a certain value! (unbiased, on average, the emprirical cdf we have the right cdf!).

#### Other famous distributions
[https://math.stackexchange.com/questions/2589506/chi-squared-distribution-related-to-the-mean-of-an-exponential-sample](https://math.stackexchange.com/questions/2589506/chi-squared-distribution-related-to-the-mean-of-an-exponential-sample)
if we have $$X_{i} \sim Exp(1)$$ then it is true that

$$
Y = 2 \sum_{i = 1}^{n}X_{i} \sim \chi^{2}_{2n}
$$

Where $$n$$ is the degrees of freedom, bad thing is that this usually just *even*, so useful for that. (chi square gamma distribution)


$$
Y = \beta \sum_{i=  1}^{n} X_{i} \sim G(a, \beta) : a \in \mathbb{N}^{*}
$$

Which is a Gamma distribution, exponential is special case of gamma?

$$
Y = \frac{\sum_{i=1}^{a} X_{i}}{\sum_{i = 1}^{a + b} X_{i}} \sim Be(a, b)
$$

Which is a *Beta* regression, used for microbiome in the guts, I don't know why.

### Transformation of random variables (no exam)
La cosa strana per questi statistici e che non si capisce per quale fine stiamo facendo queste trasformazioni, che non sono molto utili a primo impatto. Nel senso che non so nemmeno quale sia il problema che stiamo provando a risolvere!

Suppose $$X \sim f_{X}(x)$$, and $$Z= g(X)$$ with $$g$$ an invertible function, then suppose $$Z \sim f_{Z}(z)$$ 
Then the support of the density is in $$X$$ , we have that 

$$
f_{Z}(z) = \frac{\delta F_{Z}(z)}{\delta z} = f_{X}\left[ g^{-1}(z) \right]  \cdot  \frac{\delta g^{-1}(z)}{\delta z}
$$

Non so esattamente cosa mi possa servire questo e non so nemmeno perché funziona.
Dopo:
alla fine la dimostrazione di questo è molto semplice (io sono un po' incapace nelle dimo a quanto pare e tendo ad impararle a memoria)
Comunque lo trovi in [https://en.wikipedia.org/wiki/Random_variable](https://en.wikipedia.org/wiki/Random_variable)
#### Uniform random variable
Permette la creazione di uniform tale per cui non siano sempre nel classico 0, 1

$$
U\sim Unif(0, 1) \implies f_{U}(u) = 
\begin{cases}
0 : u \not\in \left[ 0, 1 \right]  \\
1 : u \in \left[ 0, 1 \right] 
\end{cases}
$$

Allora la trasformazione sarebbe:

$$
X = (b - a)U  + a , \,  b > a
$$

Then 

$$
U = \frac{x - a}{b - a} = g^{-1}(X) \implies \frac{\delta g^{-1}(X)}{\delta x} = \frac{1}{b-a}
\implies
f_{X}(x) = f_{U} \left[ \frac{x- a}{b - a} \right] \cdot \frac{1}{b - a}
$$

and we have that $$f_{U}$$ is in $$\left[ 0, 1 \right]$$ when we need to have $$x \geq a  \land x \leq b$$ in order to have a density different than 0.
$$

$$
#### Standard Gaussian
$$X \sim N(\mu, \sigma^{2})$$ then $$Z = (X - \mu) / \sigma$$ . Which is closed under linear transformations! and $$X = g^{-1}(Z) = \sigma \cdot Z  + \mu$$ 
Then: 

$$
f_{Z}(z) = f_{X}(\sigma z + \mu) \sigma
= \frac{1}{\sqrt{ 2\pi }} \exp \left\{ - \frac{Z^{2}}{2} \right\} 
$$

Where the first part is the density of a Gaussian

### Box-Muller algorithm (no exam)
[https://blog.cupcakephysics.com/computational%20physics/2015/05/10/the-box-muller-algorithm.html](https://blog.cupcakephysics.com/computational%20physics/2015/05/10/the-box-muller-algorithm.html)
[https://math.nyu.edu/~goodman/teaching/MonteCarlo2005/notes/GaussianSampling.pdf](https://math.nyu.edu/~goodman/teaching/MonteCarlo2005/notes/GaussianSampling.pdf)

This algorithm is used to produce Gaussian random variables:
we have $$U_{1}$$ and $$U_{2}$$ that are normal uniform, then we can take

$$
X_{1} = \sqrt{ -2 \log(U_{1}) } \cos(2\pi U_{2}), X_{2} = \sqrt{ -2 \log(U_{2}) } \sin(2\pi U_{1}),
$$

Without any approximation, it is exact for some reason


### Multivariate cases
We can use the re-parametrization trick to gen $$N(\mu, \sigma^{2})$$ just multiplying by the variance and add the mean.
We are asking if we can do the same even for the multivariate case, how can we get $$N_{p}(\mu, \Sigma)$$ ?
Let's take a bi-variate Gaussian for example.
It seems like a result that we have that the **square root of a matrix** is almost the same as a **Cholesky decomposition**. That will be our sigma. it's always possible because we have a positive definite symmetric matrix for the Sigma. See [Algebra lineare numerica](/notes/algebra-lineare-numerica) for cholesky

### The discrete case

Vogliamo andare a prendere molte probabilità in questo modo 

$$
p_{0} = P_{\theta}(X \leq 0) , p_{1} = P_{\theta}(X \leq 1) e via
$$

È sempre come conoscere una CDF discreta. 
Poi prendiamo 

$$
X = k, p_{k-1}  \leq U \leq p_{k}
$$

e così facciamo sampling della variabile per le distribuzioni discrete $$X$$


### Altre cose