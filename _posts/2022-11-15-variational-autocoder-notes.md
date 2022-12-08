---
title: Understanding Variational Autocoder 
date: 2022-11-15 22:14:08
categories:
  - Data Science
  - Deep Learning

tags:
  - deep learning
  - generative learning

published: false
---

This post takes notes about autocoder.

---

## AutoEncoders as Anomaly Detectors

1. Map the training data into a latent space. In other words, use dimension reduction methods to map high-dimensional training data samples to low dimension representation. $P_{train}($X$)$.
2. Map a data sample $X_{test}$ to latent space and reconstruct it.
3. Calculate the reconstruction loss. If the reconstruction loss is big, i.e., the reconstructed data sample does not look like the original data sample at all, it's really unlikely that the test data sample is from the training data set used to train the autoencoder. 

## Variational AutoEncoder

Instead of mapping a training data sample to a point in the latent space, VAE maps it to probability distribution in the latent space. 




## References

1. [asyncio official documentation](https://docs.python.org/3/library/asyncio.html)