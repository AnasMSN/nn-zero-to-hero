# MLP

steps in this:
1. There is this embedding space which contain 17000 in 30 multi dimensional space that is called embedding space. Each similar word that have pretty similar function semantic will place very close to each other in the space.
2. Here we use the same dataset that is names.txt
3. we define named block size that is a block of character  (in thi example is 3 character) that is used to predict the next character
4. in the (1) it said that we want to make 17000 fit in 30 dimensional space, for an example we will use 2 dimensional space (27, 2) <- example.
5. ![alt text](image.png)
6. In image  (5), the table look-up in C is the same as get the index with using of slicing specific index with onehot embedding with specific number
7. indexing in pytorch is quite powerfull because its ability to not only normal indexing, but also can input a list of index to get more than one index value, and also input a tensor to get index with ability to repeat the index value
   1. why input of torch size for C = torch.Size([27, 2]) and X= torch.Size([228146, 3] # resulted in torch.Size([228146, 3, 2])  when using C[X]? -> its because the use of indexing C and use X as index, then it see the number of rows tahts is 228146 and each rows have 3 values, then it will take the value of C which have 27 rows. Then it take the 2 values and it  created new tensor with torch.Size([228146, 3, 2])
8. some of the useful tensor function is a.view -> which will create a matrix and architect the matrix, for example tensor (9,2) (total 18) -> view(3, 3, 2) (total 18) -> this is the same as concatentate tensor with torch.cat() function using 1 dimension
9. information about pytorch internal: http://blog.ezyang.com/2019/05/pytorch-internals/
10. cross entropy to get the clasificcation, its the same as using the way to calculate logits in the makemore part -> cross entropy is more efficient 
11. overfitting can also means with very small examples of data, we try to fit in very big parameters which to overfit the data
12. to make we don't overfit, we need to make sure the data that we input have a pattern which will generalize a pattern in the potential new data without any thing to overfit the data
13. Its take very long time to do the forward pass and backward pass with all the data because the data is very big, so we need to use the batch size to make the data more efficient called min batch
14. how to get the learning rate? try to find the lowest loss changes and the explode loss changes, then try to find the in between, we can use  the learning rate finder with list all the possibilities and run based on the distribution of learning rate and then check the graph which is result tin the lower lost rate
15. the best way to divide the data is roughly 80% for training split, 10% for validation split, and 10% for test split. The training split is used to traing the parameter like weight and bias, the validation split is to train the hyper parameters like learning rate, and test split is to test the result of the model
16. similar to overfitting, underfitting is happen when the value of loss from the  training and validation is similar and a bit high, so we can add the amount of parameter in the neuron model to find the better result 
17. for evaluation of model, we need to keep track of the learning rate, the loss, to know what do we do wrong in the step we do
18. the size of the batch also important to figure whether the loss result is represent the gradient we want to get to descent