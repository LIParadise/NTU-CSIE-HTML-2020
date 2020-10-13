# Week 5

## Recap

First, we introduced *hidden function* $f$; then the goal is simple: find a way to minimize $E_\text{out}$.

But soon, we find this too far away; rather, we could start from $E_\text{in}$; a simple example is the $\text{PLA}$, *perceptron learning algorithm*, for *linear-separable, binary classification, supervised* problems.

Wait, how did $\text{PLA}$ work exactly? To explain this, we resort to probability and statistics, assuming there's a unknown distribution $P$ governing the whole universal set, including our testing data $D$. In that way, with the help of Hoeffding's inequality, we can say that when our hypothesis set is finite, we can link $E_\text{in}$ with $E_\text{out}$, and that finding best of $E_\text{in}$ is then indeed helping us aiming for the best $E_\text{in}$.

There's still questions remain, though.

### For Infinite-Sized Hypothesis Set? How Exactly, Again, Do $\text{PLA}$ Learn, Though?

  Spolier alert: with $M=\lVert \mathcal{H} \rVert = \infty$, we can sometimes use $m_\mathcal{H} \in \mathbb{R}$ in the modified Hoeffding inequality: $\mathbb{P} \llbracket \lvert E_\text{in} - E_\text{out} \rvert \geq \epsilon \rrbracket \leq 2 \cdot m_\mathcal{H} \cdot \exp{ \left( -2 \epsilon^2 N \right) }$
  And it's related to how better we can either approximate $E_\text{out}$ with $E_\text{in}$ or how small $E_\text{in}$ could be!

## Union Bound

Clearly it's over estimation; but how to tighten the bound?

An intuitive thought is classifying the hypothesis into different groups s.t. hypothesis in each groups are similar to some extent s.t. if the probability distribution isn't so bad, we can have a tighter bound.

### 2-Dimensional Case

If $2$ points, we can classify lines into $2^2=4$ categories; if $3$ points and they don't form a line, we have $2^3=8$ categories. How'bout $3$ points but they form line? Just $6$ left. $8$? It's $14$ at most!

Though this may not seem so regular, say it's *effective number of lines*, we can already see that *this series is of $\mathcal{O}( n^2 )$*; ideally we want $\text{effective} \left( N \right) \in \mathscr{o} \left( 2^N \right)$, s.t. when $N = \lVert D \rVert$ grows, the Hoeffding bound approaches $0$.

### Dichotomy

We've used the notation $\text{effective} \left( N \right)$ for 2D case; Now we consider general case: denote for data $\{ X_i ~|~ i\in\mathbb{N} ,~ i\leq n \}$ and hypothesis set $\mathcal{H}$, we have $\mathcal{H}{ \left( \{ X_i ~|~ i\in\mathbb{N} ,~ i\leq n \} \right) }$ dichotomies. Apparently it's bounded by $2^n$ for any space; the question is, what is the exact bound?

Introduce $\mathscr{m}_\mathcal{H} \left( n \right) \overset{\Delta}{=} \max\limits_{
\{ \bm{x}_i ~|~ i\in\mathbb{N} ,~ i\leq n \} \subset X
}
{ \mathcal{H}{ \left( \{ \bm{x}_i ~|~ i\in\mathbb{N} ,~ i\leq n \} \right)} }$, that is, $\mathscr{m}_\mathcal{H} \left( n \right)$ is the largest possible size of dichotomies obtainable in current possible data input.

#### 1-Dimensional Positive Ray Example of $\mathscr{m}_\mathcal{H} \left( n \right)$

It's just a plain real number line. Given $n=m$, $\mathscr{m}_\mathcal{H} \left( n \right)$ is just $m+1$.

#### 1-Dimensional Positive Interval Example of $\mathscr{m}_\mathcal{H} \left( n \right)$

For $n$ points, $\mathscr{m}_\mathcal{H} \left( n \right) = \frac{1}{2} \cdot n^2 + \frac{1}{2} \cdot n + 1$.
Hint: $n$ points, $n+1$ interval between points, choose two of them and we form a positive interval.

#### 2-Dimensional Convex Hypothesis Example of $\mathscr{m}_\mathcal{H} \left( n \right)$

Given all $n$ points on some circle, we find that we need $2^n$ convex polygons to $\text{shatter}$ the set.

Now, we've seen different $\mathcal{H}$ on different space leads to different $\mathscr{m}_\mathcal{H} \left( n \right)$; what's our $\mathscr{m}_\mathcal{H} \left( n \right)$ for our 2-dimensional $\text{PLA}$?

Introduce $\text{break point}$: first $m\in\mathbb{N}$ such that $\mathscr{m}_\mathcal{H} \left( m \right) < 2^m$; easy to see that if $m$ is break point then for all $(m+k) ,~ k\in\mathbb{N}$ it's also break point.

Claim:
- Break point of $\mathscr{m}_\mathcal{H} \left( n \right)$ is some $m \in \mathbb{N}$ $\implies$ $\mathscr{m}_\mathcal{H} \left( n \right) \in \mathcal{O}{ \left( n^{m-1} \right) }$
  Somehow tricky... (?)
  Notice we don't have tight $\Theta$ here.
- Break point at infinite far $\implies$ $\mathscr{m}_\mathcal{H} \left( n \right) \in \Theta{ \left( 2^n \right) }$
  This one is trivial via definition of break points.

## Question

1. > 因為它們兩條線很接近, 所以, 如果你的這個機率函數不是太糟糕的話, 那它的 $E_\text{out}$ 也會很接近。 所以這兩個 Hypothesis 發生壞事情的 Data Set, 其實通常非常得接近。
  (Quoted from week 5, lecture 2)
  Define good distribution?

