# Starting Strength
_This_ repository will contain detailed explanation on weight initialisation for deep learning but the inspiration for the name of this repository comes from [this](https://www.athlegan.com/starting-strength) article that I was reading. If you are are into gains do check it out, If you are not please do exercise (This repo is written in 2020 when exercise is necessary for human beings). 

# Weight Initialisation
One we have defined a neural network and have our dataset our next job is to set the weights initial weights for the network. Our go to stategy for this would be to set random weights and train another way to think about this is by taking consideration about transfer learning. (if you dont know much about it read [this](https://github.com/abhijitramesh/Transfer-Learning)) For transfer learning we generaly freez the parameters of the part of the network which means the network would already have the weights that are aligned with the classification task that we are trying to perfrom then we just tweek the model a little bit to work for us. 

Similarly let us see what are the different techniques that we can apply to initialise weights.