+++
author = "George Paps"
title = "Glimpses of Computer Vision (Draft)"
date = "2025-09-27"
math = true
categories = [
    "articles"
]
+++

This essay outlines some major developments in the field of computer vision, 
beginning with Perceptron and progressing to more recent advances such as EfficientNet. 

## Perceptron (1958)


<!-- - Rosenblatt [1957].
- **Key Contribution**: Learn weights step by step.
- Earliest and simplest type of artificial neural network.
- Works only for linearly separable problems. -->

Our journey will start in the late 50s.
In 1958 Rosenblatt [1], an erudite psychologist, 
conceived the earliest and simplest type of artificial neural network, the Perceptron.
The Perceptron functions as a simple classifier 
which based on some inputs, outputs 0 or 1.
Its calculations are straightforward: 
take the inputs, 
calculate their weighted average,
add a parameter called bias,
and check the sign of the result.
If the result is greater or equal to zero the neuron outputs 1, 
otherwise if the result is less than 0 it outputs 0.

In mathematical notation the equation described above for four inputs is:

$$
z = w_{1}*x_{1} + w_{2}*x_{2} + w_{3}*x_{3} + w_{4}*x_{4} + b \\
$$
$$
\text{output:}\\
$$
$$
\text{if } z>= 0 \to 1 \newline
\text{if } z < 0 \to 0 
$$
or in condensed form $z$ can be calculated as:

$$z=\sum_{i=1}^n w_{i}*x_i + b $$

The calculations Perceptron performs seem and are simple. 
**They key contribution of Perceptron though, 
lies not in its calculations,
but on its learning algorithm.** 

To get a better understanding of how Perceptron works, 
let's start with a simple house classification problem.
We want, given the square meters, the number of rooms, the construction year,
the price, and an indicator of how expensive the area is,
to identify whether a house is a bargain or not.
Since Perceptron is a classifier
we can use it to help us identify bargains.
The problem statement mentioned above can be restated in the following way:
$$
z = w_{1}*x_{1} + w_{2}*x_{2} + w_{3}*x_{3} + w_{4}*x_{4} + w_{4}*x_{4} + b \\
$$

$$
\text{where:}
$$

$$
x_{1} \text{: square meters of the house} \newline 
x_{2} \text{: number of rooms} \newline 
x_{3} \text{: construction year} \newline 
x_{4} \text{: price} \newline 
x_{5} \text{: area indicator} \newline 
$$

Now, if $z > 0$ we'll say that the house is a bargain, otherwise it is not. 

In the problem statement there are five $x$ variables describing each house,
and  6 parameters $w_{1},w_{2},w_{3},w_{4},w_{5}, w_{6}$, and $b$
that affect the outcome. 
These parameters, 
when selected appropriately,
can result in the equation correctly identifying 
whether a house is a bargain or not.
For the houses that are bargains 
their weighted average plus b would be greater than zero
for the rest it will be less than zero.
But how do we decide what values these 6 parameters will take?

The process of picking the appropriate parameters 
for our Perceptron is called **training**.
For the training process to take place
we need training examples,
houses with known values for the 5 variables describing them
and knowledge of whether they are a bargain or not.
Having these training examples we can tune the parameters 
in order to classify a house as a bargain or not.
Without getting into many details,
here is the high level training algorithm used by Perceptron.

```
1) pick random values for the parameters w1,w2,w3,w4,w5,b

2) pick an example house:

    a) calculate z based on house variables and parameters
    b) if z > 0 the algorithm predicts the house is a bargain, otherwise not
    c) does the prediction agree with the example?
        i) yes -> continue to next example
        ii) no ->  update the parameters and continue to next example
```

The second loop continues until we go through all examples being correctly classified 
or some other stopping condition if it takes too many iteration to classify all houses correctly.

**One of the main contributions of Perceptron 
is the training algorithm described in step 2.**
This step-by-step learning by example process captured the imagination 
of the scientist of the time.
It might felt reminiscent on some level to how we learn;
we make attempts towards our goal
and when we make a mistake we learn from it
and adjust our strategy.


## Le Net (1998)

<!-- LeNet is a deep convolutional neural network used for image recognition.
It consists of a convolutional layer, followed by a average pool, 
followed by another convolutional layer, followed by another average pool
and finally two fully connected layers with a softmax(not really) in the end. -->

French machine-learning heavyweight Yann LeCun introduced in 1998 [2]
a convolutional neural network used for image classification, LeNet5.
On a high level LeNet5 shares some similar characteristics with Perceptron:
both receive inputs[^1], 
perform calculations based on trainable parameters,
and classify the output[^2].
LeNet5 though is a significantly more complicated artificial neural network.
The input has much bigger size
and the calculations are more complicated and consist of many successive layers.

The main problem networks similar to LeNet5 faced 
was the significantly higher number of trainable parameters
due to bigger input size and more calculations.
To get a sense of scale,
LeNet5 has around 60.000 trainable parameters,
while the Perceptron example discussed earlier has 6.
This made training the networks very challenging.
And here lies the main contribution of LeNet5,
LeCun implemented the efficient and still widely used 
method for training neural networks called backpropagation.
This development made feasible the training of networks similar to LeNet5
and contributed to their widespread adoption.

LeNet5 can be considered a foundational neural network for deep learning,
and has made other contributions in the field, aside of the backpropagation method. 
It formalized the convolution operation with weight sharing filters,
it demonstrated that successive convolutional layers 
can effectively capture spatial hierarchies,
and it also introduced the use of pooling layers.
Additionally the overall architecture introduced by LeNet5
was used as the basis for subsequent models.




[^1]: In the case of LeNet5 the inputs are 32x32 black and white images, so the input has $32*32 = 1024$ data points for every example compared to the $5$ points for each Perceptron example. 
[^2]: In the Perceptron example it classified the house as a bargain or not,
LeNet5 recognizes hand-written digits which is equivalent to classifying the images to the classes: 0,1,2,3,4,5,6,7,8,9


## AlexNet (2012)

AlexNet, developed by Krizhevsky, Sutskever, and Hinton [3], 
is a neural network similar to LeNet-5 but implemented on a significantly larger scale[^3], with important technical innovations and remarkable performance.
The overall network architecture is rather similar to LeNet5,
an indication of its lasting influence.

The main contribution of AlexNet is that it 
further showcased the feasibility of using deep convolutional neural networks
for real-world computer visions tasks.
It achieved this through a rigorous technical implementation
and by using a number of technical innovations as:
(1) ReLU activation functions,
(2) parallel training in 2 GPUs,
(3) dropout regularization and creative data augmentation techniques to avoid overfitting,
and (4) overlapping max-pooling filters.


[^3]: The jump in the scale of the model is impressive.
The input size increases from 32x32 black and white images to
227x227 color images,
thus from 1024 data points per example to 154.587 data points per example. 
The number of trainable parameters climbs from 60 thousand to 60 million.
The number of layers increases from 7 to 12 
and the network classifies the images between a 1000 categories instead of 10.


## VGG-16 (2015)

...

## ResNet (2015)

...

## References

[1] F. Rosenblatt, "The Perceptron: A Probabilistic Model for Information Storage and Organization in the Brain," *Psychological Review*, vol. 65, no. 6, pp. 386–408, 1958. [DOI: 10.1037/h0042519](https://doi.org/10.1037/h0042519)

[2] Y. LeCun, L. Bottou, Y. Bengio, and P. Haffner, "Gradient-based learning applied to document recognition," *Proceedings of the IEEE*, vol. 86, no. 11, pp. 2278–2324, 1998. [DOI: 10.1109/5.726791](https://doi.org/10.1109/5.726791)

[3] A. Krizhevsky, I. Sutskever, and G. E. Hinton, "ImageNet Classification with Deep Convolutional Neural Networks," *Advances in Neural Information Processing Systems (NeurIPS)*, 2012. [PDF](https://papers.nips.cc/paper/4824-imagenet-classification-with-deep-convolutional-neural-networks.pdf)

[4] K. Simonyan and A. Zisserman, "Very Deep Convolutional Networks for Large-Scale Image Recognition," arXiv preprint arXiv:1409.1556, 2014. [arXiv:1409.1556](https://arxiv.org/abs/1409.1556)

[5] K. He, X. Zhang, S. Ren, and J. Sun, "Deep Residual Learning for Image Recognition," *Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition (CVPR)*, 2016. [DOI: 10.1109/CVPR.2016.90](https://doi.org/10.1109/CVPR.2016.90)
