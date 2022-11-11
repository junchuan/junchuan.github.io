---
title: Deep Learning Notes 
date: 2021-02-20 22:14:08
categories:
  - Data Science
  - Deep Learning

tags:
  - deep learning

published: false
---

This post takes notes about deep learning.

---

## RNN

Networks that are able to connect previous information to the present task. The gradients can either vanish or explode over many stages of propagation. 

## LSTM

LSTM was designed to overcome vanishing and exploding gradients problem in the RNN model. But there is still a sequential path for the data and is difficult to parallelize the computation. 

## Transformer

This model consists of two components, encoder and decoder. The encoder will take a variable-length input and convert it into a hidden state with a fixed length. Then the decoder will convert the fixed-length state into an output of variable length. 

## Layer

The fundamental building block of a neural network is the layer. A layer is a data-processing module that takes as input one or more tensors and outputs one or more tensors. Layer's weights are where the knowledge of the network is stored.  
Different layers are appropriate for different types of data processing. For example, simple vector data, stored in 2D tensors of shape `(samples, features)`, is often processed by `densely connected layers`, a.k.a., `fully connected or dense layers`. Sequence data is typically processed by `recurrent` layers. 

## Model

A deep learning model is a directed, acyclic graph os layers. The most common instance is a linear stack of layers. The topology of a network defines a hypothesis space. Picking the right network architecture is more of an art than a science. Practice helps. 

## Loss function 




## References

1. [asyncio official documentation](https://docs.python.org/3/library/asyncio.html)