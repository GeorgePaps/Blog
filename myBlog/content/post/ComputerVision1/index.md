+++
author = "George Paps"
title = "Computer Vision: From the Perceptron to EfficientNet"
date = "2025-10-08"
math = true
categories = [
    "articles","machine-learning",
]
image = "Cézanne -Mont Sainte-Victoire.jpg"
+++

This essay outlines some major developments in the field of computer vision, 
beginning with Perceptron and progressing to more recent advances such as EfficientNet. 

## Perceptron (1958)


<!-- - Rosenblatt [1957].
- **Key Contribution**: Learn weights step by step.
- Earliest and simplest type of artificial neural network.
- Works only for linearly separable problems. -->

Our journey starts in the late 1950s.
In 1958 Frank Rosenblatt [1], an erudite psychologist, 
conceived the earliest and simplest type of artificial neural network - 
the **Perceptron**.
The Perceptron is a **binary classifier**:
given some input and a set of trainable parameters,
it outputs 0 or 1.
The following equation describes Perceptron's calculations:

$$
z=\sum_{i=1}^n w_{i}*x_i + b \newline
\text{output:}\\
$$
$$
\text{if } z>= 0 \to 1 \newline
\text{if } z < 0 \to 0 
$$

where $w_{i}$ denotes the trainable parameters, 
$x_{i}$ the input vector's components,
and $b$ a parameter called bias. 

**The computations the Perceptron performs are simple,
yet its most important contribution lies in its learning algorithm.**
The learning algorithm determines 
how the Perceptron adjusts its parameters during training.
The learning process is simple,
each training example is presented to Perceptron
and whenever it misclassifies one,
it updates its parameters accordingly.
These adjustments gradually steer the model towards classifying more examples correctly 
and reducing errors.

This simple, example-driven learning process — try, make mistakes, and adjust — 
which to some extend is reminiscent of how humans learn, 
combined with some biological inspiration behind the idea of Perceptron 
gave it a distinct aura and made it very popular.
An important limitation though 
is that Perceptron can find a correct solution only on linearly separable training sets.
If the data are not linearly separable (for example the XOR problem), 
the perceptron cannot represent a correct solution. 
Minsky and Paper famously highlighted this limitation 
contributing significantly towards the arrival of the first AI winter in research.

## LeNet-5 (1998)

It was known that overcoming the limitations of Perceptron
required more complicated network architectures:
networks with many layers of Perceptrons stacked
(known as multilayer Perceptrons - MLP).
An important problem with these architectures 
is that the simple training algorithm mentioned for Perceptron
is not applicable  
and finding an efficient and scalable algorithm 
for training more complicated networks proved to be a rather daunting task.

In 1989 French machine-learning heavyweight Yann LeCun 
introduced LeNet-5 [2].
On a high level LeNet-5 shares many similar characteristics with Perceptron:
both receive inputs, 
perform calculations based on trainable parameters,
and classify the output[^1].
LeNet-5 though is a significantly more complicated artificial neural network.
The input has much bigger size
and the calculations are multi-layered and complicated.

To get a sense of scale,
LeNet-5 has around 60.000 trainable parameters
while a Perceptron usually has a number in the low tens.
This made training the networks very challenging.
And here lies the main contribution of LeNet-5,
LeCun implemented the efficient and still widely used 
method for training neural networks called **backpropagation**.
This development made feasible the training of networks similar to LeNet-5
and contributed to their widespread adoption.

Aside from the backpropagation training method 
LeNet-5 has made other contributions in the field.
It formalized the convolution operation with weight sharing filters,
it demonstrated that successive convolutional layers 
can effectively capture spatial hierarchies,
and it also introduced the use of pooling layers.
Additionally, the overall architecture introduced by LeNet-5
was used as the basis for subsequent models.
Overall LeNet-5 is considered one of the foundational models of deep learning.

[^1]: LeNet-5 is used to classify handwritten digits between 0 and 9.

## AlexNet (2012)

AlexNet, developed by Krizhevsky, Sutskever, and Hinton [3], 
is a neural network similar to LeNet-5 but implemented on a significantly larger scale[^3], with important technical innovations and remarkable performance. 

The main contribution of AlexNet is that it 
further showcased the feasibility of using deep convolutional neural networks
for real-world computer visions tasks.
It achieved this through a rigorous technical implementation
and through the introduction of many technical innovations as:
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


## VGG-16 (2014)

VGG-16 introduced by Simonyan and Zisserman in 2015 
comprises another important step in the evolution of deep learning models[4].
Compared to AlexNet, 
the size of the model increases
from around 60 million to around 138 million trainable parameters, 
while the depth of the model increases
from 12 layers to 16 layers.
Another important difference 
is that VGG-16 uses the same filter in all layers[^4],
this simplifies the model architecture,
while some related architectural tricks 
help decrease the number of parameters.
Overall though the architecture of the VGG-16 is similar to that of AlexNet.

The main contribution of VGG-16 consists 
in showing that increased model depth(more layers)
is a viable path towards increased model accuracy.
Additionally, its uniform and simplified architecture 
was later used as the basis for many deep learning models
and the pre-trained model 
was used as the backbone of many computer vision tasks.

[^4]: AlexNet uses convolutional filters of varying size and stride, their size for example ranges from 3x3 to 11x11. VGG-16 uses only 3x3 convolutional filters with same padding and stride of 1. It often uses many of those in a row if necessary. The latter trick reduces the number of necessary model parameters.

## ResNet (2015)

VGG-16 demonstrated the effectiveness of training increasingly deeper networks.
However, as the depth of the networks increased,
researchers and practitioners encountered a new challenge:
vanishing and exploding gradients.
This is a problem related to how backpropagation operates.
As the name suggests, backpropagation,
attempts to "propagate" the error made in the output layer
back through all the involved layers, 
estimate each layer's "contribution" to the error, 
and adjust the respective parameters accordingly.
This process for very deep networks is rather challenging
and often results in overestimation or underestimation
of the contribution distant layers have in the error.

An elegant solution to the problem of vanishing and exploding gradients 
was introduced with ResNet[5].
In a typical neural network,
the information propagates through each layer until it reaches the output,
which can cause the contributions of early layers to diminish significantly.
In Resnet, the authors introduced skip connections (or shortcuts), 
which allow information from a layer 
to bypass some subsequent layers. 
These skip connections reduce the effective depth of calculations
and increase the effectiveness of backpropagation in deeper networks.

## Conclusion

The improvements from one model to the next are mostly incremental 
and even VGG-16 bears many similarities to LeNet-5.
Following this development arc of computer vision models 
one should naturally mention MobileNet[6] and EfficientNet[7],
which emphasize efficiency and scalability in convolutional networks.
After that however, there is a clear paradigm shift 
with the introduction of Vision Transformers (ViTs),
which replace convolution operations with attention mechanisms.

## References

[1] F. Rosenblatt, "The Perceptron: A Probabilistic Model for Information Storage and Organization in the Brain," *Psychological Review*, vol. 65, no. 6, pp. 386–408, 1958. [DOI: 10.1037/h0042519](https://doi.org/10.1037/h0042519)

[2] Y. LeCun, L. Bottou, Y. Bengio, and P. Haffner, "Gradient-based learning applied to document recognition," *Proceedings of the IEEE*, vol. 86, no. 11, pp. 2278–2324, 1998. [DOI: 10.1109/5.726791](https://doi.org/10.1109/5.726791)

[3] A. Krizhevsky, I. Sutskever, and G. E. Hinton, "ImageNet Classification with Deep Convolutional Neural Networks," *Advances in Neural Information Processing Systems (NeurIPS)*, 2012. [PDF](https://papers.nips.cc/paper/4824-imagenet-classification-with-deep-convolutional-neural-networks.pdf)

[4] K. Simonyan and A. Zisserman, "Very Deep Convolutional Networks for Large-Scale Image Recognition," arXiv preprint arXiv:1409.1556, 2014. [arXiv:1409.1556](https://arxiv.org/abs/1409.1556)

[5] K. He, X. Zhang, S. Ren, and J. Sun, "Deep Residual Learning for Image Recognition," *Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition (CVPR)*, 2016. [DOI: 10.1109/CVPR.2016.90](https://doi.org/10.1109/CVPR.2016.90)

[6] A. G. Howard, M. Zhu, B. Chen, D. Kalenichenko, W. Wang, T. Weyand, M. Andreetto, and H. Adam, "MobileNets: Efficient Convolutional Neural Networks for Mobile Vision Applications," arXiv preprint arXiv:1704.04861, 2017. [arXiv:1704.04861](https://arxiv.org/abs/1704.04861)

[7] M. Tan and Q. V. Le, "EfficientNet: Rethinking Model Scaling for Convolutional Neural Networks," *Proceedings of the International Conference on Machine Learning (ICML)*, 2019. [arXiv:1905.11946](https://arxiv.org/abs/1905.11946)