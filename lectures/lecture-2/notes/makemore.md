# Makemore

its make more name, its learn to generate more from dataset

- A bigram language model is a type of statistical language model that predicts the probability of a word in a sequence based on the previous word. This can start with two character and try to predict what the next character will be.

step by step what you do:

1. you mapping each input name and add start and end character to each name
2. you mapping it to by 2 charachter each and count how many that 2 character is total to all of the names in names.txt
3. after that,  you mapping it to 27 x 27 map tensor (because added one character (.)) to get the imagination of the mapping to number of counter 2 characters
4. we use a torch.Generator() with seeding to generate a random number and then we divide it by total number to get the probability of the total, then we use torch.multinomial to generate index based on the probability created by torch.Generator() and generate number of samples based on the input is given
5. have respect to broadcasting, make sure you know which column and row
6. in the map 27 x 27, we will count the probability for each of the character and the next character by each rom sum. The probability is got from the current value to the sum value of the row. Then after we convert to normalize probaility for the matrix,  we can get to know what is the maximum l ikelihood of generated word
7. we can add 27 x 27 matrix with number 1 value so the probability of number is not zero and this called smoothing
8. Generated word we can know is from the torch.Generator() and torch.multinomial() function that generate a word based on the probability of the matrix created before.
9. to get the loss from this is we can get the log of the probability after each of the bigram character. Log likelihood of that will give us an almost 0 value if it  near  1 value and - infinity if its near  0 (0 - 0.5), we will use negative log likelihood to be our loss function becuase log likelihood is negative value.
10. Because the result is not really that representative with the maximum likelihood, we will try to implement neural network to fix this

Neural Network step by step bigram:
1. We create a training set with input and result (xs, ys), the input is the first character and the  output is the second character if it compared to last example
2. because the value of the input is an index of the character, we can't just use this value, we need to encode it before we input it to the neural network. To encode it we use torch.nn.functional.one_hot() to encode the value to the one hot encoding, we create array of zeros and give one in the number integer it valued
3. after we encode it, if for example the input is (5,27), we create matrix multiplication to the value of matrix (27, 27) -> random value weight -> to get the probability of the next character 
4. it will result in will be (5,27) with new probability for each input to the result with ability to guess the next character
5. we then use softmax of all the probability to get the best result from all of th probability
6. note from before, loss also need smothing so the value of loss not too impacting the value of the weight. We can use regularization to make the value of the weight not too big -> gives penalty to the loss value based on weight to make loss not overfitting 