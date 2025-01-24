# Batch Norm

## Restart what Multi Layer Perceptron

- RNN is hard to optimizable, to know why, we need to know about activation, batchnorm dkk
- magic number is embedding dimesional number and hidden layer number
- @torch.no_grad() is used to make sure the gradient is not calculated in the context of the code block
- its easier to start with uniform distribution to weight and bias, so it easily to be optimized. But, when initialized and start from 0, don't just use 0 for weights
- its not good if the result of  tanh is 1 or -1, because the gradingt not impact anything in  backward propagation
- in activation function, there are some flat tails in sigmoid, tanh, ReLU, and ELU, we need to make sure the value is not in the flat tails, because the effect of the gradient is not impact anything in the backward propagation.
- for initialization neural network torch.nn.init.kaiming_normal_() is used to make sure the value is not in the flat tails, we can use gain and fan_in to generate better standard deviation
- before, we need to adjust the activation function and gradient properly, but now, we have many property to use like batch norm, optimizer (RMSprop, Adam, SGD)


Modern Innovation:
- Batch Normalization (2015): we can train Deep neural network and work properly -> how? because in each layer, it will normalize result of each input the normalize data is still give impact in the gradient function in the backpropagation 
- there is batch normalization running to save the result of the batch normalization in training, so its for normalizing the data for the testing because batch normalization in training is a bit noisy so we need accumulate bit by bit
- batch normalization have its own bias, so bias before batch normalization is not needed and will not impact anything after bn
- BN usually used after mathematical layer like convolutional and matrix multiplication layer for smoothing result

