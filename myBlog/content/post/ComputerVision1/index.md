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
The Perceptron functions as a simple classifier 
which based on some inputs outputs 0 or 1.
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
for our Perceptron is called training.
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

French machine-learning heavyweight Yann LeCun introduced in 1998 LeNet5,
a convolutional neural network used for image classification[^1].
LeNet5 was pivotal and contributed many innovations in the field 
influencing significantly the field of deep learning.

To those with knowledge of the early stages of deep learning,
LeNet5's architecture should feel familiar.


[^1]: LeNet5 takes 32*32 images and classifies them in categories.
The original application was hand-written digit recognition.

## AlexNet (2012)

...

## VGG-16 (2015)

...

## ResNet (2015)

...

## MobileNet (2017)

...

## Efficient Net (2019)