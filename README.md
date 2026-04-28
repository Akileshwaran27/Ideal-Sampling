# 1.Experimental verification of Signal sampling using various types
# Aim
Write a simple Python program for the construction and reconstruction of ideal, natural, and flattop sampling.
# Tools required
    Google Colab
    Python
    NumPy Library
    Matplotlib Library
    Internet Connection
    Computer / Laptop / Mobile

# Theory
🔹 Introduction

Sampling is the process of converting a continuous-time signal into a discrete-time signal by taking its values at uniform time intervals. It is a fundamental step in digital signal processing and communication systems.

According to the Nyquist Theorem, a signal can be perfectly reconstructed from its samples if the sampling frequency fs is at least twice the maximum frequency fm present in the signal:
fs ≥ 2fm..
	​This minimum sampling rate is called the Nyquist rate. If this condition is not satisfied, aliasing occurs, leading to distortion.
# Program
```
import numpy as np
import matplotlib.pyplot as plt

fm = 5                      # Message frequency 5hz
fs = 50                     # Sampling frequency 50hz
t = np.linspace(0, 1, 1000) # Continuous time axis
ts = np.arange(0, 1, 1/fs)  # Sampled time axis

# Original analog signal
x = np.sin(2 * np.pi * fm * t)#x=sin(2pifmt)

# Sampled values
xs = np.sin(2 * np.pi * fm * ts)

# Flat-top sampling generation
flat_top = np.zeros_like(t)

for i in range(len(ts)-1):
    idx = np.where((t >= ts[i]) & (t < ts[i+1]))
    flat_top[idx] = xs[i]

# Plotting
plt.figure(figsize=(12,8))

# Original signal
plt.subplot(4,1,1)
plt.plot(t, x)
plt.title("Original Analog Signal")
plt.grid()

# Ideal Sampling
plt.subplot(4,1,2)
plt.stem(ts, xs, basefmt=" ")
plt.title("Ideal Sampling")
plt.grid()

# Natural Sampling (approximated)
plt.subplot(4,1,3)
plt.plot(t, x)
plt.stem(ts, xs, linefmt='r', markerfmt='ro', basefmt=" ")
plt.title("Natural Sampling")
plt.grid()

# Flat-top Sampling
plt.subplot(4,1,4)
plt.plot(t, flat_top)
plt.title("Flat-top Sampling")
plt.grid()

plt.tight_layout()
plt.show()
```
# Output Waveform

<img width="1189" height="790" alt="image" src="https://github.com/user-attachments/assets/7b25e43a-0a76-4f81-b49c-916e4cf0d3b9" />


# Results
The program successfully generated and plotted the original signal along with ideal, natural, and flat-top sampled signals. 

