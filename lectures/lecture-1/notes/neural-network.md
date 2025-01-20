# Neural Networks: Zero to Hero

## Micrograd
Its an github repo to know how neural networks work with simple and easy basic parameter to be understood.

Some of the mathematical things in this:
- derrivative -> to get the gradient of the function and the slope will be used to backpropagation
- how some very different node impact the lass output -> chain rule of the derrivation (dL / dc = dL / df * df / dc) - the recursive of chain rule means is the backpropagation
- each of the node will save the value of gradient, what is this for? -> the current value will be added by learning rate * gradient that is saved
- - topological sort is sorting the node from last node to the first node in the context of backpropagation. This is used in DAG (Directed Acyclic Graph) to get the right order of the node to be calculated.