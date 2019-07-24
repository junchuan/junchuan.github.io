---
title: Understand Fourier Transform
date: 2013-07-02 09:16:00
categories:
- Notes

tags:
- data science

---

## What does Fourier transform do?

- Find the separate component (cycle ingredient ,i.e., the cycle strength,delay and speed) from a signal.
- The Fourier transform finds the set of *cycle speeds, strength and phases(starting angles)* to match any time signal.
- Fourier transform changes our perspective from “consumer” to “producer”, turning “what did I see” into “how was it made”

## The amazing euler's formula:  
$$ e^{ix} = cos(x)+isin(x)$$
- $e^{i\pi}$ means starting at 1 and rotating  to $\pi$ get to -1
- $e^x$ means starting from e and grow continuously at 100% for x seconds
- real growth: pushing a number in the same, real direction it was going
- imaginary growth: grows at different direction. Instead of going forward, imaginary growth rotates the number. Taking any number and multiplying by $i$ will not change its magnitude, just the direction it points.  

## How do we grow $e$ to $a + bi$? 
- it is a mix of real and imaginary growth. The real part $a$ means growing at 100% for $a$ seconds, and the imaginary part $b$ means rotate for $b$ seconds.

