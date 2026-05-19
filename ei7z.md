---
title: combine numpy arrays
tags: [pr, python, numpy]
date: 2026-05-19
id: ei7z
author: Julian Stoerig
---

## Combine vectors to a matrix 

To stack multiple numpy arrays, e.g. `xs` and `ys`, use the `np.stack(<iterable-of-arrays>, axis)` function.

```python
x = np.array([1,2,3])
y = np.array([4,5,6])
z = np.stack((x,y), axis=0)
```

You should avoid using stack in a loop, because it causes redundant copies. Instead push into a python list and stack at the end:

```python
l = []
for k in range(5):
    x = np.linspace(0, k, 5)
    l.append(x)
y = np.stack(l)
```

Better: if the size is known beforehand, preallocate a single array for all partial arrays.

```python
n_points = 5
k_iterations = 5
partial_shape = (n_points,)
y = np.empty((k_iterations,) + partial_shape)
for k in range(k_iterations):
    y[k] = np.linspace(0, k, n_points)
```
