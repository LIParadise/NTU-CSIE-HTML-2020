# Week 3

## Different Output Set

- 單選
- multi-class
- Structured
- Regression

- batch
- online
- active

## Different Output Set Tags

- Supervised Learning
- Semi-Supervised Learning
- Un-Supervised Learning
- Reinforcement Learning

## Different Input Set

*Concrete*: previous discussions focus on *concrete* input data (*concrete feature*), that is, we assume these input are somehow related to the desired output
More often than not these features are derived with help of *domain knowledge*: pre-processing

By contrast, we may also use *raw features*. Notice it's generally more 抽象 for machine, since the domain knowledge often compress the raw data somehow, and this means it's harder for the machines.

*Feature Engineering*

*Deep Learning*: from a (large) set of data, sometimes un-supervised, extract concrete features

Sometimes we don't have features!
For example, in the KDDCup Song Recommendation problem, the input are just song IDs and user IDs! This 2-dimensional feature is basically a mess, and we need to somehow extract more feature from them!

> 「必須幫每個使用者抽取出他真正的特徵…，幫每個歌曲抽取出它的特徵」