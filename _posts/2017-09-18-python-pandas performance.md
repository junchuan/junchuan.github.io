---
title: Some tips for speeding up python data processing 
date: 2017-09-18 19:29:00
categories:
- Data Science

tags:
- python
- programming
- data science

---

## python pandas performance optimization
- Crude loop should never be used. 
- `iterrows` is a bit faster.
- `apply()` is even faster. It takes advantage of internal optimization such as iterators in Cython.
- Vectorization over Pandas series is even faster.Instead of passing individual scalar values into function, we can pass entire series. 
- The fastest is vectorization with Numpy arrays. When possible, we should use numpy `ufunc` feature. Simply converting from the pandas representation to a numpy representation via the `Series.values` field yields an almost full order of magnitude performance improvement.  

## python pandas boolean evaluation 
- `and` and `or` perform a single boolean evaluation on an entire object, while `&` and `|` perform multiple boolean evaluations on the content (the individual bits or bytes) of an object. For boolean numpy arrays, the latter is nearly always the desired operation.
```
x=np.arange(10)
(x > 4) & (x < 8) # right
(x > 4) and (x < 8) # error
```

## using numba in python
- Numba gives you the power to speed up your applications with high performance functions written directly in Python. With a few annotations, array-oriented and math-heavy Python code can be just-in-time compiled to native machine instructions.
- [Numba tutorial 1](https://github.com/gforsyth/numba_tutorial_scipy2017/tree/master/notebooks)
- [Numba tutorial 2](https://github.com/ContinuumIO/gtc2018-numba)

