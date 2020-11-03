---
title: Python asyncio package
date: 2020-10-17 21:29:08
categories:
  - HPC

tags:
  - async
  - python
  - concurrency
  - parallel computing
---

This post discusses python asyncio module.

---

## async IO

Asynchronous IO is a language-agnostic paradigm that has implementations across a host of programming languages. `asyncio` package in python provides API to run `coroutines`.

async IO gives you a feeling of concurrency despite using a single thread in a single process. Asynchronous routines are able to “pause” while waiting on their ultimate result and let other routines run in the meantime.

For example: 

```python
import asyncio

async def count():
    print("One")
    await asyncio.sleep(1)
    print("Two")

async def main():
    await asyncio.gather(count(), count(), count())

if __name__ == "__main__":
    import time
    s = time.perf_counter()
    asyncio.run(main())
```

This simple code block above, when run, will output: 

```
one
one
one
two
two
two
```

- `async def` introduces either a native `coroutine` or an `asynchronous generator`. To call a coroutine function, you must `await` it to get its results.

- `await` passes function control back to event loop. If Python encounters an `await f()` expression in the scope of `g()`, this is how `await` tells the event loop, *Suspend execution of g() until whatever I’m waiting on*. It is a syntax error to use `await` outside `async def` function.

- It is less common to use `yield` in an `async def` block. This creates an `asynchronous generator`.

- When we use `await f()`, `f()` has to be an object that is *awaitable*. For now, just know that an awaitable object is  another coroutine. 

## Coroutine

A coroutine is a specialized version of a Python generator function. 

## Reference

1. [asyncio official documentation](https://docs.python.org/3/library/asyncio.html)