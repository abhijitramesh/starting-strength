# Starting Strength
_This_ repository will contain detailed explanation on weight initialisation for deep learning but the inspiration for the name of this repository comes from [this](https://www.athlegan.com/starting-strength) article that I was reading. If you are are into gains do check it out, If you are not please do exercise (This repo is written in 2020 when exercise is necessary for human beings). 

# Weight Initialisation
One we have defined a neural network and have our dataset our next job is to set the weights initial weights for the network. Our go to stategy for this would be to set random weights and train another way to think about this is by taking consideration about transfer learning. (if you dont know much about it read [this](https://github.com/abhijitramesh/Transfer-Learning)) For transfer learning we generaly freez the parameters of the part of the network which means the network would already have the weights that are aligned with the classification task that we are trying to perfrom then we just tweek the model a little bit to work for us. 

Similarly let us see what are the different techniques that we can apply to initialise weights.

## The Network 
We will be doing our reserch on Weight Initialisation using the Fashion MNIST dataset because it is the toy dataset good enough to test out all Image Classification Netoworks on its intial stages. We will be using an MLP here with 3 layers with hidden dimensions of 256 and 128. And also the MLP accepts inputs as flattended images and produces outputs with 10 class scores.

checkout the network in the notebook above.

## Constant Weights
This is one way of initialising weights, what we do here is set a constant weights in all the nodes and train the network, but the problem is we would have a huge training loss. Why is this happening ?

Well let us take a look under the hood.

First we set all the weights to 0 or 1 (Let us say).

Then we do a foward pass then we calculate the error. Then we do a backpropogation now here is what happens in this step all the weights are giving the same error and the neural network finds it difficult to see which node is contributing more error.

The code explantaiton for this is shown in the _All Zeros or Ones_ Session in the notebook.