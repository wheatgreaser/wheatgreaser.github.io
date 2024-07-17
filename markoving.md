# can you markov my chain?

## july 17, 2024:
markov chains are simple. the future state only depends on the current state. its as simple as that. look at this image (its an order):

![markovchain](/images/imagesformarkov/1.png)
source: towardsdatascience

ok lets look at the node labelled as rainy, the arrows basically just give the probability of the future state given the current state(rainy). so, for example the probabiltiy of it raining tomorrow (future state) given that its raining today (current state) is is 60% (indicated by the arrow pointing to itself).  its that simple. and obviously the sum of the outgoing arrows should be 100% or if you're talking about fractions it should be 1. 

ok so in essence, i want to program something that will find the probability of a random state, for example what is the probabiltiy that it will rain on a random day given a "directed graph" (the image).




