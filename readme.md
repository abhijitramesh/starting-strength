# Starting Strength
_This_ repository will contain detailed explanation on weight initialisation for deep learning but the inspiration for the name of this repository comes from [this](https://www.athlegan.com/starting-strength) article that I was reading. If you are are into gains do check it out, If you are not please do exercise (This repo is written in 2020 when exercise is necessary for human beings). 

# Weight Initialisation
One we have defined a neural network and have our dataset our next job is to set the weights initial weights for the network. Our go to stategy for this would be to set random weights and train another way to think about this is by taking consideration about transfer learning. (if you dont know much about it read [this](https://github.com/abhijitramesh/Transfer-Learning)) For transfer learning we generaly freez the parameters of the part of the network which means the network would already have the weights that are aligned with the classification task that we are trying to perfrom then we just tweek the model a little bit to work for us. 

Similarly let us see what are the different techniques that we can apply to initialise weights.

## The Network 
We will be doing our reserch on Weight Initialisation using the Fashion MNIST dataset because it is the toy dataset good enough to test out all Image Classification Netoworks on its intial stages. We will be using an MLP here with 3 layers with hidden dimensions of 256 and 128. And also the MLP accepts inputs as flattended images and produces outputs with 10 class scores.

checkout the network in the [notebook](https://github.com/abhijitramesh/starting-strength/blob/master/weight_initialization_exercise.ipynb) above.

## Constant Weights
This is one way of initialising weights, what we do here is set a constant weights in all the nodes and train the network, but the problem is we would have a huge training loss. Why is this happening ?

Well let us take a look under the hood.

First we set all the weights to 0 or 1 (Let us say).

Then we do a foward pass then we calculate the error. Then we do a backpropogation now here is what happens in this step all the weights are giving the same error and the neural network finds it difficult to see which node is contributing more error.

The code explantaiton for this is shown in the _All Zeros or Ones_ Session in the [notebook](https://github.com/abhijitramesh/starting-strength/blob/master/weight_initialization_exercise.ipynb).

## Uniform Random
Uniform Distribution has equal probability of picking up any number from a set of numbers. So what we can do is use a uniform distribution of random numbers and use those as our weights and train the model and hence this will lead to out model causing mistakes and these mistakes would help the model to learn correctly.

In the part of the [notebook](https://github.com/abhijitramesh/starting-strength/blob/master/weight_initialization_exercise.ipynb) with titile _Uniform Distribution_ We can see the implementation of this in code and how the loss is decreasing over the epocs faster since the gradient descent is working properly.
Also we can see we get improved performance when we look at the accuracy.

## General Rule

If we learned something from both the above cases it is that we should never use 0 and 1 as constant weights and also we could use a uniform distribution as our weights. Well let us combile these two ideas and also a rule of thumb while selecting the weights would be to have tha values in the range -y to y, where y = 1/squareroot(n) where n is the number of nodes in network.

Check out the part of the [notebook](https://github.com/abhijitramesh/starting-strength/blob/master/weight_initialization_exercise.ipynb) with heading _General rule for setting weights_ to see how this tremendosly improve our performance the loss is not only decreasing but it is faster compared to the Uniform Random Distribution.

## Normal Distribution

Another way to try out is to use a normal distribution by doing so there is a higher likelihood of picking number close to it's mean. Here also we would use a the general rule. 

If you check out the [notebook](https://github.com/abhijitramesh/starting-strength/blob/master/weight_initialization_exercise.ipynb) session _Normal Distribution_ you can see that the it has similar perfomance to uniform distribution but it starts out better this is probaby becuase the dataset we are using is small and if we use a bigger dataset the change would also be magnified.

## Automatic Initialisation

In the [notebook](https://github.com/abhijitramesh/starting-strength/blob/master/weight_initialization_exercise.ipynb) _Automatic Initialization_ shows how the model would train without any initialisation of weights that would be done by us to our suprise it is as good as our uniform distribution becuse if you checkout the source code for linear layers in pytorch you can understand that the weights are actually set by default with a unifrom distribution which might workout in some cases but in other we need to use Normal distribution or maybe even something else.