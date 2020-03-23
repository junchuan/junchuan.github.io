---
title: Dask Notes
date: 2018-01-28 09:16:00
categories:
- Big Data
- Data Science

tags:
- data science
- dask

---

## Dask 

This is another parallel computing framework, but a little more lightweight than apache spark.    
In task scheduling we break our program into many medium-sized tasks or units of computation, often a function call on a non-trivial amount of data. We represent these tasks as `nodes` in a graph with `edges` between `nodes` if one task depends on data produced by another. A `task scheduler` is called to execute this graph. Task scheduling logic often hides within other larger framework.  
Dask uses a specification to encode a graph -- a directed acyclic graph of tasks with data dependencies using common python objects: `dicts`, `tuples`, `callables`. A dask graph is a dictionary that maps keys to computations:  
```
{'x': 1,
 'y': 2,
 'z': (add, 'x', 'y'),
 'w': (sum, ['x', 'y', 'z']),
 'v': [(sum, ['w', 'z']), 2]}
```
A `key` is any hashable value that is not a `task`. A `task` is a `tuple` with a `callable` as first element. The succeeding elements in the task tuple are arguments for that function.  

## Dask collections
### dask.array 
```
import h5py
dataset = h5py.File('myfile.hdf5')['/x']

import dask.array as da
x = da.from_array(dataset, chunks=dataset.chunks)

y = x[::10] - x.mean(axis=0)
y.compute()
```

### dask.dataframe 
```
import dask.dataframe as dd

df = dd.read_csv('data/2016-*.*.csv', parse_dates=['timestamp'])
df.groupby(df.timestamp.dt.hour).value.mean().compute()
```

### dask.bag 
```
import dask.bag as db
import json

records = db.read_text('data/2015-*-*.json').map(json.loads)
records.filter(lambda d: d['name'] == 'Alice').pluck('id').frequencies()
```  
Besides built-in collections, dask also provides a wide variety of ways to parallelize custom applications. 
### Dask delayed
- Call `delayed` on the function, not the result
- Call `compute()` on lots of computation at once. Ideally, you want to make many `dask.delayed` calls to define your computation and then only call `dask.compute` at the end
- Don’t change inputs. If you need to use a mutable operation, then make a copy with your function first. 
- Avoid global state
- You need to break up computations into many pieces.You achieve parallelism by having many `dask.delayed` calls, not by using only a single one. 
- Avoid too many tasks.
- Avoid calling `delayed` within `delayed` functions. 
- Don’t call `delayed` on other Dask collections. When you place a dask array or dask dataframe into a delayed call that function will receive the Numpy or Pandas equivalent. 
Instead, it’s more common to use methods like `da.map_blocks` or `df.map_partitions`, or to turn your arrays or dataframes into many delayed objects. 
``` 
partitions = df.to_delayed()
delayed_values = [dask.delayed(train)(part) for part in partitions]
```
- Avoid repeatedly putting large inputs into delayed calls. Instead, it better to delay your data as well.


