---
title: IEEE floating-point representation
date: 2014-08-15 09:16:00
categories:
- Data Science
- Programming

tags:
- programming
- float point number

---

### Representing and manipulating float point number 
IEEE floating-point representation  $ V= (-1)^s  M 2^E $
- `s` determines whether the number is negative or positive 
- The significand `M` is a fractional binary number that ranges either between 1 and $2-\epsilon $ or between 0 and $1- \epsilon$
- The exponent `E` weights the value by power of 2
- In a single-precision floating-point format, fields `s`, `exp` and `frac` are `1`, `k=8` and `n=23`; for a double-precision floating-point format, fields `s`, `exp` and `frac` are `1`, `k=11`, and `n=52` bit
- Normalized value: when the bit pattern of `exp` is neither all zeros nor all ones. In this case, the exponent field is interpreted as representing a signed integer in biased form $E=e-Bias$ , where $Bias=2^{k-1}-1$. The fraction field is interpreted as representing the fractional value f, where `0<f<1`. The significand is defined to be `M=1+f`. 
- Denormalized value: when the exponent field is all zeros. In this case, the exponent value $E=1-Bias$, and $M=f$.
- Special value: when the exponent field is all ones. 


  

