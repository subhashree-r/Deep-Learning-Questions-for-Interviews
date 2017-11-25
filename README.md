## Interesting Why's and How's in Deep Learning for Interviews


1. Is cross entropy better than l2 loss?
Cross entropy is better at learning(faster) when used with sigmoid activation. This is because the derivative of the cross entropy activation cancels the derivative of sigmoid during backpropogation . Since derivative of sigmoid saturates at 1 and zero and slows down training, when the derivative ofsigmoid term is cancelled, learning is faster and prevents vanishing gradient problem.
2. What happens when pooling is removed completely? What are the advantages of removing the pooling? What are the advantages of max pooling?
Advantages of pooling:
 Pooling helps in translational invariance.
 Pooling leads to larger portion of the input image to be represented in the later layers.
If there is no pooling, the network learns its own spatial pooling as usually the pooling layer has no parameters.
3. What is the role of zero padding?
Zero padding is used to not lose the pixels (information) in the boundary and to make the output feature map of fixed dimension.
4. What are 1*1 convolutions and how do they help?
1*1 convolutions help in reducing the number of parameters(features). It was mainly used in Inception network. It helps introduce more non-linearity through activations without making the network deeper.
5. How does batch norm help overcome vanishing gradient?
Batch normalization helps in getting rid of outliers and hence leads to faster convergence.
6. How does relu solve vanishing gradient?
The function is linear and does not saturate.
7. What happens when we decrease the batch size to 1? What happens when we make the batch size equal to size of the dataset?
When batch size is 1, the gradient descent is very random, and might take longer to converge. But the memory requirement is very less. When the batch size is equal to the entire batch, it requires lot of memory. Also, it might lead to sharp convergence due to which the network can overfit. Stochastic gradient descent reaches smooth minimum.
8. What is dilation?
The filters have spaces between cells. Hence there is a gap of 1 when applying the convolution. This helps in more aggressive spatial pooling and the effective receptive field grows much quickly.
9. Can FC be converted to convolutional layer?
If the input of FC layer is 7*7*512, then set the size of filter to be 7. This type of network is called converted convent. Passing a larger image through converted convent is more efficient. This converted convent can give a vector of (series) of class scores across various spatial positions. This computationally more efficient than iterating a single convent over different spatial positions.
10. What happens when we initialize all weights to zero with ReLu activation?
There will be no learning.
11. How to calculate the effective receptive field given filter size, padding and stride? How to calculate the number of FLOPS required?
No. of FLOPS : input depth * output depth * o/p_feature_map_width * o/p_feature_map_height * kernel_width * kernel_height
12. What is the difference between model parallelism and data parallelism?
Model parallelism – when the training is done by sharing the parameters across the different architectures. Data parallelism – when training is done by sharing the data across different GPUs.
13. Can a neural network with single RELU (non-linearity) act as a linear classifier?
No
14. Difference between l1 and l2 loss? Which is better?
L1 loss is more robust to outliers, but has unstable solution and possible multiple solutions. L2 loss has stable solution and one solution.
15. What is the role of filter size? How can it affect accuracy and computational efficiency? What is the ideal filter size to be chosen?
Multiple small filters are better than 1 big filter. For e.g. three 3*3 filters instead of single 11*11 filter.
16. How can you reduce the gap between validation and training loss?
The problem of overfitting. Can be overcome using dropout, data augmentation.
17. How would you increase the speed (fps) when employing deep learning in mobile platforms?
A technique called pruning where at every iteration, the coefficients which are becoming zero or close to zero are checked and removed from being involved in further training. This phase is called inference.
General questions to test if we know to use tensorflow framework (what is the command for session run) / how to access gpu (have you used cluster?)
