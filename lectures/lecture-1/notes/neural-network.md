# Neural Networks: Zero to Hero

## Micrograd
Its an github repo to know how neural networks work with simple and easy basic parameter to be understood.

Some of the mathematical things in this:
- derrivative -> to get the gradient of the function and the slope will be used to backpropagation
- how some very different node impact the lass output -> chain rule of the derrivation (dL / dc = dL / df * df / dc) - the recursive of chain rule means is the backpropagation
- each of the node will save the value of gradient, what is this for? -> the current value will be added by learning rate * gradient that is saved
- topological sort is sorting the node from last node to the first node in the context of backpropagation. This is used in DAG (Directed Acyclic Graph) to get the right order of the node to be calculated.
- if some neuron have linetwo node to one node, then the gradient just added value of the first node and the second node
- layer of neuron is a bunch of neuron that is calculated independently ( array on neuron)
- Multi layer perceptron
- gradients in the input is useless because the input will not changing, only the weight value in the deepen neuron will have gradient effecting the value
- parameter is the weight in bias in the neural network
- after backward, you need to zero grad the value of the gradient in the neuron because if not, its not flush the grad, it will added the last gradient with the new gradient value.