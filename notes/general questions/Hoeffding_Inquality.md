# Towards Learning: The Multi-Bin Problem

How does one formalize the problem when we want to apply the Hoeffding's Inequality?

The problem itself is re-stated as the following:
Known (Hoeffding): Do $\text{i.i.d.}$ experiment $n$ times with random variable $Z$, the derived random variable $E_\text{in} \overset{\Delta}{=} { \frac{1}{n}\sum\limits_{i=1}^{n}{z_i} }$ describes the empirical mean of the $\text{i.i.d.}$ sequence $\{z_i\}$ of which length is $n$, then Hoeffding guarantees that $E_\text{in}$ is *good*, that is
$$\mathbb{P} \llbracket \lvert E_\text{in} - \mathbb{E}_Z \rvert \rrbracket \geq \varepsilon \leq 2\exp{-2\varepsilon^2 n}$$
Whereas in the learning scheme, seems that we can't quite use the same problem setup now, since we're effectively choosing in-between many $Z_i$ to be the real random variable behind the $\text{i.i.d.}$...: $Z$ is composed of the real coloring and the sampling distribution.

## Partial Answer

If we want to apply Hoeffding's Inequality, we need the assumption that there's observations of $\text{i.i.d.}$ sequences; in our original discussions, this comes from the joint result of our *unknown sampling distribution* and the *inherent, determined result of comparing the fixed hypothesis versus the oracle*, that is, the coloring of the bin observed by some unknown biased lens.
In the multi-bin or learning setup, we choose $g$ and thus changes the coloring *after* we see the data, which is kinda weird...
The question now becomes, *why can't we assume the data comes from $\text{i.i.d.}$ sampling in this case*? Or we can *still* assume they are from $\text{i.i.d.}$ distribution, however we can no longer assume the sampling distribution here, say, $P^{'}$, is the same as the $P$ for the external, real world data? If either of the above 2 statements is true, why? I'm now more towards the latter, though.
Re-state the latter statement: suppose when we choose $g$ among the hypothesis set $H$, we effectively *forced* the underlying sampling distribution $P$, combined with $g$, to *behave like* the $E_\text{in}$ as observed, or to put it in another way, we had more assumptions on the sampling distribution, however this is very likely *not* the sampling probability for the external, real world works; from yet another perspective, if we insist the same sampling distribution for all the cases, then the $P$ and $g$ may not in general give us such data, instead it's possible that this is a horribly wrong, *BAD* data.

# The Sampling Distribution Used in The Learning Problem

Hoeffding needs $\text{i.i.d.}$ distribution, which means *with replacement*.
But in data we don't quite have this property.
Glitch in our problem model?
