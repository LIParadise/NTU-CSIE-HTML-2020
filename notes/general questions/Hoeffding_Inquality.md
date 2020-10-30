# Towards Learning: The Multi-Bin Problem

How does one formalize the problem when we want to apply the Hoeffding's Inequality?

The problem itself is re-stated as the following:
Known (Hoeffding): Do $\text{i.i.d.}$ experiment $n$ times with random variable $Z$, the derived random variable $E_\text{in} \overset{\Delta}{=} { \frac{1}{n}\sum\limits_{i=1}^{n}{z_i} }$ describes the empirical mean of the $\text{i.i.d.}$ sequence $\{z_i\}$ of which length is $n$, then Hoeffding guarantees that $E_\text{in}$ is *good*, that is
$$\mathbb{P} \llbracket \lvert E_\text{in} - \mathbb{E}_Z \rvert \rrbracket \geq \varepsilon \leq 2\exp{-2\varepsilon^2 n}$$
Whereas in the learning scheme, seems that we can't quite use the same problem setup now, since we're effectively choosing in-between many $Z_i$ to be the real random variable behind the $\text{i.i.d.}$...: $Z$ is composed of the real coloring and the sampling distribution.

# The Sampling Distribution Used in The Learning Problem

Hoeffding needs $\text{i.i.d.}$ distribution, which means *with replacement*. But in data we don't quite have this property. Glitch in our problem setup?
