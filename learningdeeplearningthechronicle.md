# chronicles of learning deeplearning (i'm chronicling so hard rn):  

i wanted to learn deep learning so that i could become a multi ultra mega zillion bajillionaire. no, really.  
i learnt from the fundamentals(as one does). first principles are really important. i think. but i dont want to get swamped in the intricacies. i also want to learn the fun stuff.  
i watched the 3blue1brown series(here's the [link](https://www.youtube.com/watch?v=aircAruvnKk&list=PLZHQObOWTQDNU6R1_67000Dx_ZCJB-3pi)). it was so fucking godly. i semi-understood it the first time but still it was so fucking good.    
the thing is, i already knew a bit about deep learning, i read that book Artifcial Intelligence: A guide for Thinking Humans, so i went in with a bit of background.  
i wanted to build a neural net from scratch. but i wanted to get used to the rough overview before going all in.  

here's the [repo](https://github.com/wheatgreaser/learning-deep-learning)

alright. if i could ramble on, i would ramble on, i would like to sort my rambling so i could ramble more cohesively. so i loosely divded this into chapters (i'll update them as i learn).
here's the deal. deep learning is huge. i'm small (by which i mean im a beginner). so ill leave a list of things that i want to pursue in the future at the end of each chapter.
also. as i previously mentioned im a newbie. a noob if you will. so dont take my word for it, most of the topics that ive rambled about are the way that i understand them. so yes.
ive listed the chapters in the order that i learnt them.

## 1.backprop:
this is where i started. (ofc after learning about the general overview idiot, (the training data, testing data split, the input layer, hiden layer, loss function, basics(theory) of grad descent, activation functions ,etc).  

so i watched andrej karpathy's vid (about halfway(ok slightly more than half)) where he remade micrograd. backprop is basically the chain rule from differentiation. how does the loss function change with respect to the weights and biases of nodes of the previous layer and layer before that going up till the input layer. he explained this using expression graphs. which was nice. basically if two things are being multiplied taking the derivative of something wrt to one gives the other (for example: if c is the output and a * b = c then dc/da = b and dc/db = a. in the context of a neuron, weight * data = value, and d(value)/ d(weight) = data.). and during addition the derivative basically gets split into two(for example: c = a + b, dc/da = 1 and dc/b = 1, so during chain rule the derivative just splits into two and goes to a and b (what i mean is e= c* d, c= a + b, de/dc = d and de/da = (de/dc) * (dc/da), dc/da = 1 so de/da = d, similarly de/db = d (splitting!!))).

so i manually computed the chain rule for an expression graph and then for a neuron. this gave me a bit of insight. this is also where i stopped. i could have recursivle programmed it to execute the chain rule. but i stopped here.

shit i wanna learn: gradient descent(from mathematical fundamentals)

## 2.convynetty
convynettys are simple. theyre just feature extractors, hey what distinguishing features do i need to know to know to make a good prediction i dunno find it yourself. feature extractor. i was inspired by 3blue1brown again. god i fuxkign love that guy. he made a video on convolutions. it was genius. after the 3rd watch i finally got what convynettys are all about. hey to recognize a face i need to know what features to train on, monstrously difficult task, just extract the features yourself bitch. wow. i love cnns.

basically a convolutional layer extracts the features and you 'downgrade' the image using pooling (maxpool, avgpool i dont care) then do it again and again till youre satisfied then flatten it and pass it into a traditional neural net badabing badaboom you just trained a convnet model.

the way i like to understand feature extraction (it doesnt technically happen but what i like to think happens) is basically you extracts fearures like eyes, nose and the n you extract even general fearures till you have a face. (feature from a feature??) 

shit i wanna do: cnn from scratch, experiment with the different architectures(lenet, alexnet, resnet, etc).

## 3.recursyvursy  
heres where things get gipptic(gpt). i dont like how chat gippity gets so attention. nlp is the future. i mean turing himself proposed imitation game to be the test for sentience which involves nlp.  

rnns are easy enough. q: how do you deal with inputs of variable size, a: rnn, dipshit. basically a neuron connected to itself with a weighted a connection. you can temporally modify the weight after each new inout. the stock market example is really good.

imagine i want to predict the price of the stock tomorrow and i have access to today's and yesterday's record. now i take yesterday's data and then make a predoction now i take today's data and pass it into the neuron as a new input i take the output of the prevoous step and multiply it with a weight and pass it into the neuron and get a prediction for today. then repeat it to get the prediction for tomorrow. easy. we use Back Propogation Through Time to do the weight modification. wow. 

but the real nut crusher is the fact that rnns are not really used cuz of the vanishing exploding gradient problem, for ex if you have the weight of the output connecting itself to be 2 (lets just consider this weight and not the weight of the input) lets assume we have data for 50 days now for the first day the output is multiplied by 2 and passed into itself now the value passed in is (lets say 2 * 1(output value = 1)) now lets do it again for the 2nd day, now its 4 now do it again for 50 days, for 51st day which we have to predict, 2^50 is passed into itself.
if we deal with data values that huge the gradients are going to be huge (d(output)/dw = data value) which means if we take a teeny step to the right or left the graph will fluctuate wildly.

