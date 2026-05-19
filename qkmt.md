---
title: interpolation
tags: [maths]
date: 2026-05-18
id: qkmt
author: Julian Stoerig
---

Choosing the right algorithm for the situation is fundamentally important to interpolation.

## Linear

```py
def interp_linear(a, b, t):
    """Interpolate between points `a` and `b` on a line where `t` is in [0,1] and represents how far towards b the point is."""
    p = a + (b-a)*t
    return p
```

## Circular

```py
def interp_circular(a, b, t):
    """Interpolate between points `a` and `b` on a circle where `t` is in [0,1] and represents how far towards b the point is."""
    a = np.asarray(a)
    b = np.asarray(b)
    x_a = a[..., 0]
    y_a = a[..., 1]
    x_b = b[..., 0]
    y_b = b[..., 1]
    r = np.hypot(x_a, y_a)
    phi_a = np.arctan2(y_a, x_a)
    phi_b = np.arctan2(y_b, x_b)
    diff_raw = phi_b-phi_a
    diff = (diff_raw+np.pi) % (2*np.pi) - np.pi
    phi_p = phi_a + diff*t
    x_p = np.cos(phi_p) * r
    y_p = np.sin(phi_p) * r
    p = np.stack((x_p, y_p), axis=-1)
    return p
```

