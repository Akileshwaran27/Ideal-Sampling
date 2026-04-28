# Ideal, Natural, & Flat-top -Sampling
# Aim
Write a simple Python program for the construction and reconstruction of ideal, natural, and flattop sampling.
# Tools required
# Program
# Impulse Sampling
import numpy as np
import matplotlib.pyplot as plt
from scipy.signal import resample

fs = 100
t = np.arange(0, 1, 1/fs) 
f = 5
signal = np.sin(2 * np.pi * f * t)

# Sampled signal
t_sampled = np.arange(0, 1, 1/fs)
signal_sampled = np.sin(2 * np.pi * f * t_sampled)

# Reconstructed signal
reconstructed_signal = resample(signal_sampled, len(t))

# Create subplots
plt.figure(figsize=(12, 8))

# 1. Continuous Signal
plt.subplot(3,1,1)
plt.plot(t, signal, label='Continuous Signal')
plt.title('Continuous Signal (fs = 100 Hz)')
plt.xlabel('Time [s]')
plt.ylabel('Amplitude')
plt.grid(True)
plt.legend()

# 2. Sampled Signal
plt.subplot(3,1,2)
plt.stem(t_sampled, signal_sampled, linefmt='r-', markerfmt='ro', basefmt='r-', label='Sampled Signal (fs = 100 Hz)')
plt.title('Sampling of Continuous Signal (fs = 100 Hz)')
plt.xlabel('Time [s]')
plt.ylabel('Amplitude')
plt.grid(True)
plt.legend()

# 3. Reconstructed Signal
plt.subplot(3,1,3)
plt.plot(t, reconstructed_signal, 'r--', label='Reconstructed Signal (fs = 100 Hz)')
plt.title('Reconstruction of Sampled Signal (fs = 100 Hz)')
plt.xlabel('Time [s]')
plt.ylabel('Amplitude')
plt.grid(True)
plt.legend()

plt.tight_layout()
plt.show()
# Parameters
fm = 5                      # Message frequency (Hz)
fs = 50                     # Sampling frequency (Hz)

t = np.linspace(0, 1, 1000)   # Continuous time axis
ts = np.arange(0, 1, 1/fs)    # Sampled time axis

# Original analog signal
x = np.sin(2 * np.pi * fm * t)

# Sampled values (ideal samples)
xs = np.sin(2 * np.pi * fm * ts)

# -------- Natural Sampling --------
pulse_width = 0.01
natural = np.zeros_like(t)

for i in range(len(ts)):
    idx = np.where((t >= ts[i]) & (t < ts[i] + pulse_width))
    natural[idx] = x[idx]

# -------- Flat-top Sampling --------
flat_top = np.zeros_like(t)

for i in range(len(ts)-1):
    idx = np.where((t >= ts[i]) & (t < ts[i+1]))
    flat_top[idx] = xs[i]

# -------- Plotting --------
plt.figure(figsize=(12, 8))

# 1. Original Signal
plt.subplot(4,1,1)
plt.plot(t, x)
plt.title("Original Analog Signal")
plt.xlabel("Time (s)")
plt.ylabel("Amplitude")
plt.grid()

# 2. Ideal Sampling
plt.subplot(4,1,2)
plt.stem(ts, xs, basefmt=" ")
plt.title("Ideal Sampling")
plt.xlabel("Time (s)")
plt.ylabel("Amplitude")
plt.grid()

# 3. Natural Sampling
plt.subplot(4,1,3)
plt.plot(t, natural)
plt.title("Natural Sampling")
plt.xlabel("Time (s)")
plt.ylabel("Amplitude")
plt.grid()

# 4. Flat-top Sampling
plt.subplot(4,1,4)
plt.plot(t, flat_top)
plt.title("Flat-top Sampling")
plt.xlabel("Time (s)")
plt.ylabel("Amplitude")
plt.grid()

plt.tight_layout()
plt.show()
# Output Waveform
<img width="1527" height="492" alt="image" src="https://github.com/user-attachments/assets/20e23e8a-dcab-4200-b112-72376db93173" />
<img width="1519" height="467" alt="image" src="https://github.com/user-attachments/assets/b0f2f73c-a121-42b7-9298-f87e2faa11ff" />

# Results
a simple Python program for the construction and reconstruction of ideal, natural, and flattop sampling is succesfully generated.................................................................
# Hardware experiment output waveform.
