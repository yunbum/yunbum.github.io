---
layout: post
read_time: true
show_date: true
title:  Other accessory
date:   2021-02-28 12:32:20 -0600
description: 다양한 모바일 로봇 악세사리.
img: posts/20210228/trailer-1-c.png 
tags: [accessory, trailer, speaker, led]
author: Ybbaek
github: amaynez/GenericNeuralNetwork/ # amaynez/GenericNeuralNetwork/
---
모바일 로봇에 장착하거나 연결해서 사용할 수 있는 다양한 악세사리를 제공하고 있습니다.
<center><img src="./assets/img/posts/20210228/trailer-1-c.png" width="480px"></center>
Let me try to explain; I am in the process of immersing myself into the world of Machine Learnin.

Another benefit of doing this is that since I am also learning Python, the experiment brings along good exercise for me.

<center><img src="./assets/img/posts/20210228/nnet_flow.gif"></center>

The library started very narrowly, with just the following functionality:
- **create** a neural network based on the following parameters:
    - number of inputs
    - size and number of hidden layers
    - number of outputs
    - learning rate
- **forward propagate** or predict the output values when given some inputs
- **learn** through back propagation using gradient descent

I restricted the model to be sequential, the only activation function I implemented was sigmoid:

<center><img src="./assets/img/posts/20210228/nn_diagram.png"></center>

With my neural network coded, I tested it with a very basic problem, the famous XOR problem.

XOR is a logical operation that cannot be solved by a single perceptron because of its linearity restriction:

<center><img src="./assets/img/posts/20210228/xor_problem.png"></center>

As you can see, when plotted in an X,Y plane, the logical operators AND and OR have a line that can clearly separate the points that are false from the ones that are true.

As you can see, the z values array is reshaped as a 2d array of shape (x,y), since this is the way Matplotlib interprets it as a surface:

```python
axs1.plot_surface(x, y, z,
                  rstride=1,
                  cstride=1,
                  cmap='viridis',
                  vmin=0,
                  vmax=1,
                  antialiased=True)
```

The end result looks something like this:
<center><img src="./assets/img/posts/20210228/Surface_XOR.jpg"></center>

Then we reshape the z array as a one dimensional array to use it to color the scatter plot:

<center><img src="./assets/img/posts/20210228/Final_XOR_Plot.jpg"></center>

So my baby ML library is completed for now, but still I would like to enhance it in several ways:

- include multiple activation functions (ReLu, linear, Tanh, etc.)
- allow for multiple optimizers (Adam, RMSProp, SGD Momentum, etc.)
- have batch and epoch training schedules functionality
- save and load trained model to file

I will get to it soon...