# Experimental verification of Signal sampling using various types
# Aim
Write a simple Python program for the construction and reconstruction of ideal, natural, and flattop sampling.
# Tools required
```
Google Colab
Python
NumPy Library
Matplotlib Library
Internet Connection
Computer / Laptop
```
# Theory
# Ideal or Instantaneous or Impulse Sampling:
sampling signal is a periodic impulse train. The area of each impulse in the sampled signal is equal to the instantaneous value of the input signal.

# Natural Sampling:
Natural sampling is also called practical sampling. In this sampling technique, the sampling signal is a pulse train. In natural sampling method, the top of each pulse in the sampled signal retains the shape of the input signal during pulse interval.

# Flat Top Sampling:
The flat top sampling is also the practical sampling technique. In the flat top sampling, the sampling signal is also a pulse train. The top of each pulse in the sampled signal remain constant and is equal to the instantaneous value of the input signal 𝑥(𝑛) at the start of the samples.
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

<img width="1009" height="660" alt="WhatsApp Image 2026-04-21 at 9 01 43 AM" src="https://github.com/user-attachments/assets/31269f5e-21b1-410a-ab41-8928c22071b1" />


# Results

 A simple Python program for the construction and reconstruction of ideal, natural, and flattop sampling is simulated using google colab.
