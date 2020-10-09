# Week 4

## No Free Lunch

> 所以如果我們堅持, 大家記得我們要堅持甚麽? 堅持之一是 $f$ 是不知道的。 $f$ 不知道, 所以我們在我們看過的 Data 以外的點我們對 f 是一無所知。 如果我們只堅持 $f$ 是不知道,那麼我要在 Data 以外的部份去說我一定學到了甚麽東西這件事情是*做不到*的, 這個是這個 __No Free Lunch__, 天下沒有白吃的餐這樣的 philoshophy, 這樣的哲學告訴我們的事情

## Hoeffding's Inequality

Suppose $X$ is Bernoulli's random variable with expected value $\mu$, consider $\text{i.i.d.}$ sequence $\{ X_i \}$ where $S = \frac{ \sum\limits_{i=1}^{N} X_i }{ N }$ begin empirical average, then:
$$\mathbb{P}{ \llbracket \lvert S-\mu \rvert \geq \epsilon \rrbracket \leq 2 \cdot \exp{ \left( -2 \epsilon^2 N \right) } }$$

## Apply Hoeffding's Inequality to the learning problem

### Why use probability model?

- So that we can assume that "drawing a data point in $X$ and testing if $h$ and $f$ agree" is a Bernoulli random variable $X$
- We assume that randomly drawing multiple example is $\text{i.i.d.}$ $\{ X_i \}$
- We can use Hoeffding's Inequality on Bernoulli $\text{i.i.d.}$ to convince us if we have enough data point, we have a *PAC* F.

## Question

- > N marbles sampled independently
  How exactly do you sample independently?
  $\text{i.i.d.}$ vs finite bin?
- The Hoeffding model explaining the learning problem is kinda vague...
  - How to describe a *good* data selection?
    > 如果你假設這個 Data 是這個隨機而獨立地從這個罐子裏面做若干的抽樣的話, 那麼這個資料就代表了一把橘色或者是綠色的彈珠, 就跟我們剛才左邊在做的事情一樣。
    Define $\text{i.i.d.} ~ \{x_i\}$?
- Definition of $E_\text{out}$
  - $\underset{x \sim P}{\varepsilon}{ \llbracket h(x) \neq f(x) \rrbracket}$
    - If $\varepsilon$ is used as operator of "taking expected value", what do you mean by $x \sim P$?
