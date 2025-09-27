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
starting from Perceptron and up to more recent developments like EfficientNet. 

## Perceptron (1957)


<!-- - Rosenblatt [1957].
- **Key Contribution**: Learn weights step by step.
- Earliest and simplest type of artificial neural network.
- Works only for linearly separable problems. -->

Our journey will start in the late 50s.
In 1957 Rosenblatt, an erudite psychologist, 
conceived the earliest and simplest type of artificial neural network, the Perceptron.
Its functionality is straightforward: 
take a set of inputs, 
calculate their weighted average based on some weights,
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
z>= 0 \to 1 \\
z < 0 \to 0 
$$
or in condensed form $z$ can be calculated as:

$$z=\sum_{i=1}^n w_{i}*x_i + b $$

The calculations seem and are simple. The key contribution of Perceptron though is not in its calculations but on its learning algorithm. In order to understand the Perceptron's learning algorithm we need to formalize the type of problems Perceptron attempts solving.



## Le Net (1998)

French machine-learning heavyweight Yann LeCun introduced in 1998 LeNet5.
...
<!-- LeNet is a deep convolutional neural network used for image recognition.
It consists of a convolutional layer, followed by a average pool, 
followed by another convolutional layer, followed by another average pool
and finally two fully connected layers with a softmax(not really) in the end. -->

## AlexNet (2012)

...

## VGG-16 (2015)

...

## ResNet (2015)

...

## MobileNet (2017)

...

## Efficient Net (2019)