---
title: "Wiener attack"
---




Few years ago I wrote a brief paper regarding the RSA protocol and the attack M.J. Wiener published in 1990. I tried to create a self-contained work, emphasising the power of playing with [continued fractions](https://en.wikipedia.org/wiki/Continued_fraction) using *Legendre theorem*. The attack states that when there is a small private exponent, the RSA module $N$ could be factorized in $\mathcal{O}\big(log_2(N)\big)$, let's take a peak on how it works using an example.

There are three numbers you need to know when we talk about the RSA cryptosystem: the module $N$ plus the exponents $e$ and $d$. So, given the public key $(e,N)$ of an RSA with a small private exponent $d$

$$(e,N) = (58549809,2447482909)$$

the expansion of $\frac{e}{N}$ and its convergents will be

$$\frac{e}{N} = \bigl[\,0;\,41,\,1,\,4,\,23,\,\dots\,\bigr]$$
$$\{ c_i \}_{i{\leq}15} = \biggl\{0,\,\frac{1}{41},\,\frac{1}{42},\,\frac{5}{209},\,\frac{116}{4849},\,\dots\biggr\}$$

Using the search algorithm derived from Wiener Theorem, we notice that the fourth convergent $c_3{=}\frac{5}{209}$ is the right candidate $\widetilde{\phi}$ for the Euler function $\phi(N)$:

$$\biggl\lfloor \frac{e}{c_3} \biggr\rfloor = \biggl\lfloor \frac{58549809}{\frac{5}{209}} \biggr\rfloor = 2447382016$$

Now that we found a possible value for $\phi$, we won: the two prime factors of the RSA module have to be $60317$ and $40577$. Was it too quick? Take a look at [this](https://matteogiorgi.github.io/wiener_attack/src/wiener_attack.pdf) paper below, it will satisfy any doubts and show you some magic in Wolfram Mathematica.

<p align="center" style="margin-top:30px">
  <embed style="border:1px solid #CCCCCC; border-radius:5px" src="https://matteogiorgi.github.io/wiener_attack/src/wiener_attack.pdf" type="application/pdf" width="100%" height="600px"/>
</p>
