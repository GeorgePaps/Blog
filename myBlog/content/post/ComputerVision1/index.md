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

The calculations Perceptron performs seem and are simple. 
**They key contribution of Perceptron though, 
lies not in its calculations,
but on its learning algorithm.** 

Let's start with a simple problem of house classification.
Given the square meters, the number of rooms, the construction year,
the price, and an indicator of how expensive an area is,
we want to identify whether a house is a bargain or not.
We can use a Perceptron to help us identify bargains,
in that case the problem can be restated in equation like:
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