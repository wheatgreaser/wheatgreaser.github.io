# making an autograd engine
so what i want to make is an autograd engine. im following the [messiah](https://www.youtube.com/watch?v=VMj-3S1tku0&list=PLAqhIrjkxbuWI23v9cThsA9GvCAUhRvKZ), ofc. 

## 5th Aug, 2024:
an autograd engine implements backpropogation. you can imagine the loss function as a function that takes in a lot (say, n) of weights as input, and gives "loss" as an output. now we want to tweak the weights such that the loss is minimal (gradient descent). now, we do this weight tweaking using backprop. now, let's look at how each individual node is designed, each middle layer node basically has a set of inputs that is multiplied by a weight (think of weight as the importance of that particular input) then if the sum of all the values is above a certain threshold, this node emits an output. 

![neural network](/images/imagesforneuralnet/1.png)

now what we want to do is iteratively tune the weights to minimize the loss. 

the autograd engine im building allows you to build an expression graph. like:

```
a = 3
b = 4

c = a + b
d = a * b
e = c ** d

```
and after that using the chain rule from calculus we can find de/da and de/de , i.e, how the value of the input affects the output. 

neural networks are nothing but mathematical expressions and so we're going to be dealing with expression graphs like this (but simpler). it should be apparent by now that the concept of backprop is independent of neural networks, we're just iteratively modifying the weights to minimize a function.

you might have notcied that we deal with scalars, not tensors (like my competitor tensorflow, im coming for your throat google). the concept is the same, these scalars are packaged into tensors (arrays) so that we take advantage of the parallelism. BUT REMEMBER, THE MATH AND THE CONCEPTS ARE THE SAME.


