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
  - Under what circumstance do such probablistic statement work?
- Definition of $E_\text{out}$
  - $\underset{x \sim P}{\varepsilon}{ \llbracket h(x) \neq f(x) \rrbracket}$
    - If $\varepsilon$ is used as operator of "taking expected value", what do you mean by $x \sim P$?
    - Taking expected value could be represented as $\varepsilon \llbracket P \rrbracket$, isn't it?

### About verification versus learning...

  - Knowing that Hoeffding's inequality statement works for single $h$, why does this bother our learning?
    - Yep, we're using different $h$ in our algorithms like PLA, but don't we effectively "verified" all of them, that is, checked their error rate on $D$ on all of them?

  Since an algorithm is choosing an $h$ in a large hypothesis set, that Hoeffding guarantees us "when fixed hypothesis, probabily approximately we have $h \sim f$" isn't so strong so to speak: we have many hypothesis, and it's very possible that there's one hypothesis that's very bad, in that it's far from $f$ but on the data $D$ it seems good.
  That if $h$ behaves and $N$ large implies $h$ $\text{PAC}$ don't directly imply we can just use the best performer on $D$ in $H$, since there's probably some *bad* $h$ inside $H$.
  For example, if we let $150$ people toss coin for $5$ times, it's very likely that there's one European guy that have $5$ heads and $0$ tails. This don't mean the coin of his is superior; they are all the same. It's just that he is European. In this case, all coins (hypothesis) are the same; there's no hypothesis better or worse than one another, hence the naive "choose the best behaving coin/hypothesis" is misleading in this case.

  >  Hoeffding 告訴我們是什麼事情? Hoeffding 告訴我們事情是我取樣出來的跟我罐子裏的大部分的時候是一樣的, 只有小部分的時候是不好的, 不好這個就是我取樣出來跟我罐子裏的那兩個 μ 跟 ν 差的非常遠, 不好的我們把它叫做 BAD 就是不好的。
  > 好, 然後它說 Hoeffding 說不好的這一件事情很小, 那現在怎麼樣呢, 我們現在發現有選擇的時候, 這些選擇會惡化這些不好的情形, 對不對, 你原來你原來只有一顆銅板的時候, 好, 你這個這個銅板的機率是 $\frac{1}{2}$ , 那麼那個最不好的就是你拿到五個正面的那個機率就是 $\frac{1}{32}$ 而已, 現在你有 $150$ 個選擇的時候, 你的這個不好發生不好的事情, 也就是說你選到那個全部是全部是正面, 那它其實沒有比較好的那一個銅板, 這一件事情發生的機率超過 $99\%$, 也就是不好的機率就惡化了。 

#### Thoughts That Need Check

  For a hypothesis $h$, in the universal set, there are points where $h$ and $f$ agree, and points that $h$ and $f$ don't agree. Suppose the universal set could be modeled as generated from some $\text{i.i.d.}$ Bernoulli random variable $P$. Suppose further that data $D$ can also be modeled as observations generated from the $\text{i.i.d.}$ $P$, even though for every data point in the universal set it's a definite value, no probablistic theory involved (?).
  That is, different hypothesis corresponds to different bin.
