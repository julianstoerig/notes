---
title: noise measurement
tags: [ee, measure, signal-analyzer, noise, maths]
date: 2026-05-17T16:35:25
id: qrnm
---

When measuring AWGN noise with a swept spectrum analyzer using

- envelope detector
- log display
- log-domain averaging

the displayed noise level is biased by approximately -2.5dB                                                                                                  .

This bias is the product of two different effects.

## Envelope Detector

The envelope detector averages signal voltage as `mean(v)`, not `root(mean(v**2))`, where `v**2` is proportional to `p`.

## Log Amplifier

Noise power is random. Averaging power `p` in the log-domain falls victim to Jensen's inequality: `mean(log(p))` <= `log(mean(p))` because `log` is concave.

## Solution

Use the RMS detector without averaging, instead increasing sweep time.

If the SA does not support RMS detection, use sample detection and take the mean of the *linear* power measurements.

