---
layout: post
read_time: true
show_date: true
title:  RL Connect 프로그램 제공 - Free Ntrip client Network RTK
date:   2021-03-18 15:14:20 -0600
description: Free Ntrip client 'RL Connect'
img: posts/20210318/C94-M8P.png
tags: [GPS, Network rtk, Ntrip client, GNSS, fkp, vrs]
author: Ybbaek
github: amaynez/TicTacToe/
toc: yes # leave empty or erase for no TOC
---

## Background
GPS 의 정밀도를 높이기 위한 RTK mode 중 Network RTK 기능 설정을 위해 필요한 Ntrip client 툴을 직접 개발하여 사용하고, 별로도 독립 툴로 개발하여 배포합니다..

![RL_Connect](./assets/img/posts/20210318/RL_Connect.jpg)
<small>[RL_Connect] Netwrok RTK 모드 설정을 위한 Ntrip client..</small>

<center><img style="float: left;margin-right: 1em;" src='./assets/img/posts/20210318/tm_circle.png' width="310" height="300"></center>

You can read the blog post for it [here](./ML-Library-from-scratch.html).

I created the game quite openly, in such a way that it can be played by two humans, by a human vs. an algorithmic AI, and a human vs. the neural network. And of course the neural network against a choice of 3 AI engines: random, [minimax](https://en.wikipedia.org/wiki/Minimax) or hardcoded (an exercise I wanted to do since a long time).

<ul><li>Basic Ntirp client.</li><li>FKP, VRS mount 기준국 접속 가능.</li><li>After the memory is sizable enough, batches of random experiences sampled from the replay memory are used for every training round</li><li>A secondary </li></ul>

## Designing the neural network

<center><img src='./assets/img/posts/20210318/Neural_Network_Topology.png' width="540"></center><br>

The Neural Network c

I started out with two hidden layers of 36 neurons each.

## The many models...
### Model 1 - the first try

At first the model was trained by playing vs. a "perfect" AI, meaning a [hard coded algorithm](https://github.com/amaynez/TicTacToe/blob/b429e5637fe5f61e997f04c01422ad0342565640/entities/Game.py#L43) that

 I came across a <a href="https://github.com/bckenstler/CLR">technique by Brad Kenstler, Carl Thome and Jeremy Jordan</a> called Cyclical Learning Rate, which appears to solve some cases of stagnating loss functions in this type of networks. 

<center><img src='./assets/img/posts/20210318/lr_formula.jpeg' width="280"></center>

```python
true_epoch = epoch - c.BATCH_SIZE
learning_rate = self.learning_rate*(1/(1+c.DECAY_RATE*true_epoch))
if c.CLR_ON: learning_rate = self.cyclic_learning_rate(learning_rate,true_epoch)
```
```python
@staticmethod
def cyclic_learning_rate(learning_rate, epoch):
    max_lr = learning_rate*c.MAX_LR_FACTOR
    cycle = np.floor(1+(epoch/(2*c.LR_STEP_SIZE)))
    x = np.abs((epoch/c.LR_STEP_SIZE)-(2*cycle)+1)
    return learning_rate+(max_lr-learning_rate)*np.maximum(0,(1-x))
```
```python
c.DECAY_RATE = learning rate decay rate
c.MAX_LR_FACTOR = multiplier that determines the max learning rate
c.LR_STEP_SIZE = the number of epochs each cycle lasts
```
<br>With these many changes, I decided to restart with a fresh set of random weights and biases and try training more (much more) games.

<center><img src='./assets/img/posts/20210318/Loss_function_and_Illegal_moves6.png' width="540">
<small>1,000,000 episodes, 7.5 million epochs with batches of 64 moves each<br>
Wins: 52.66% Losses: 36.02% Ties: 11.32%</small></center>

After **24 hours!**, my computer 
<a name='Model3'></a>
### Model 3 - new network topology

After all the failures I figured I had to rethink the topology of the network and play around with combinations of different networks and learning rates.

**Finally we crossed the 80% mark!** This is quite an achievement, it seems that the change in network topology is working, although it also looks like the loss function is stagnating at around 0.15.

It is quite interesting :
- the rewards policy
- the epsilon greedy strategy
- whether to train vs. a random player or an "intelligent" AI.

And so far the most effective change

<a name='Model4'></a>
### Model 4 - implementing momentum

I [reached out to the reddit community](https://www.reddit.com/r/MachineLearning/comments/lzvrwp/p_help_with_a_reinforcement_learning_project/) and a kind soul pointed out that maybe what I need is to apply momentum to the optimization algorithm. So I did some research and ended up deciding to implement various optimization methods to experiment with:

- Stochastic Gradient Descent with Momentum
- RMSProp: Root Mean Square Plain Momentum


<a name='optimization'></a>[Click here for a detailed explanation and code of all the implemented optimization algorithms.](https://the-mvm.github.io/neural-network-optimization-methods/)

```python
self.PolicyNetwork = Sequential()
for layer in hidden_layers:
    self.PolicyNetwork.add(Dense(
                           units=layer,
                           activation='relu',
                           input_dim=inputs,
                           kernel_initializer='random_uniform',
                           bias_initializer='zeros'))
self.PolicyNetwork.add(Dense(
                        outputs,
                        kernel_initializer='random_uniform',
                        bias_initializer='zeros'))
opt = Adam(learning_rate=c.LEARNING_RATE,
           beta_1=c.GAMMA_OPT,
           beta_2=c.BETA,
           epsilon=c.EPSILON,
           amsgrad=False)
self.PolicyNetwork.compile(optimizer='adam',
                           loss='mean_squared_error',
                           metrics=['accuracy'])
```
As you can see I am reusing all of my old code, and just replacing my Neural Net library with Tensorflow/Keras, keeping even my hyper-parameter constants.

The training function changed to:
```python
reduce_lr_on_plateau = ReduceLROnPlateau(monitor='loss',
                                         factor=0.1,
                                         patience=25)
history = self.PolicyNetwork.fit(np.asarray(states_to_train),
                                 np.asarray(targets_to_train),
                                 epochs=c.EPOCHS,
                                 batch_size=c.BATCH_SIZE,
                                 verbose=1,
                                 callbacks=[reduce_lr_on_plateau],
                                 shuffle=True)
```

With Tensorflow implemented, the first thing I noticed, was that I had an error in the calculation of the loss, although this only affected reporting and didn't change a thing on the training of the network, so the results kept being the same, **the loss function was still stagnating! My code was not the issue.**
<a name='Model7'></a>
### Model 7 - changing the training schedule
Next I tried to change the way the network was training as per [u/elBarto015](https://www.reddit.com/user/elBarto015) [advised me on reddit](https://www.reddit.com/r/reinforcementlearning/comments/lzzjar/i_created_an_ai_for_super_hexagon_based_on/gqc8ka6?utm_source=share&utm_medium=web2x&context=3).

The way I was training initially was:
- Games begin being simulated and the outcome recorded in the replay memory
- Once a sufficient ammount of experiences are recorded (at least equal to the batch 

<center><img src='./assets/img/posts/20210318/ReplayMemoryBefore.png' width="540"></center>

As of today, [self play](https://medium.com/applied-data-science/how-to-train-ai-agents-to-play-multiplayer-games-using-self-play-deep-reinforcement-learning-247d0b440717), and it looks like a viable option to test and a fun coding challenge. 
