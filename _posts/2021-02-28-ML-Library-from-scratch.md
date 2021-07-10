---
layout: post
read_time: true
show_date: true
title:  Other accessory
date:   2021-02-28 12:32:20 -0600
description: 다양한 모바일 로봇 악세사리.
img: posts/20210228/MLLibrary.jpg 
tags: [accessory, trailer, speaker, led]
author: Ybbaek
github: amaynez/GenericNeuralNetwork/
---
모바일 로봇에 장착하거나 연결해서 사용할 수 있는 다양한 악세사리를 제공하고 있습니다.
<center><img src="./assets/img/posts/20210228/ML_cloud.jpg" width="480px"></center>
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

For the test I created a neural network with my library:
```python
import Neural_Network as nn

inputs = 3
hidden_layers = [2, 1]
outputs = 1
learning_rate = 0.03

NN = nn.NeuralNetwork(inputs, hidden_layers, outputs, learning_rate)
```

Then I created the learning data, which is quite trivial for this problem, since we know very easily how to compute XOR.

```python
training_data = []
for n in range(learning_rounds):
    x = rnd.random()
    y = rnd.random()
    training_data.append([x, y, x * y, 0 if (x < 0.5 and y < 0.5) or (x >= 0.5 and y >= 0.5) else 1])
```

The ML library can only train on batches of 1 (another self-imposed coding restriction), therefore only one "observation" at a time, this is why the train function accepts two parameters.

```python
fig = plt.figure()
fig.canvas.set_window_title('Learning XOR Algorithm')
fig.set_size_inches(11, 6)

axs1 = fig.add_subplot(1, 2, 1, projection='3d')
axs2 = fig.add_subplot(1, 2, 2)
```

Then we need to prepare the data to be plotted by generating X and Y values distributed between 0 and 1, and having the network calculate the Z value:

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