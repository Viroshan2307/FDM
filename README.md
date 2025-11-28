# SIMULATION OF FREQUENCY DIVISION MULTIPLEXING (FDM) AND DEMULTIPLEXING USING SCILAB
### AIM:

To write a Scilab program to simulate frequency division multiplexing and demultiplexing for six different frequencies, and verify the demultiplexed outputs correspond to the original signals.

### EQUIPMENTS Needed

Computer with Scilab installed

### ALGORITHM

Define six different frequencies to generate six sine wave signals.

Generate the time vector to represent time samples.

Compute six sine signals for each frequency over the time vector.

Frequency Division Multiplexing: sum all six sine signals to make one multiplexed signal.

Frequency Division Demultiplexing: for each frequency, multiply the multiplexed signal by a sine wave of that frequency (mixing), then apply a lowpass filter to extract the baseband (original) signal.

Plot original signals, multiplexed signal, and demultiplexed signals for verification.

### PROGRAM

```
t = linspace(0, 1, 1000);
fs = 1000; 

freqs = [4, 8, 12, 16, 20, 24];

signals = zeros(6, length(t));
for i = 1:6
    signals(i, :) = sin(2 * %pi * freqs(i) * t);
end

fdm_signal = zeros(1, length(t));
for i = 1:6
    fdm_signal = fdm_signal + signals(i, :);
end

order = 50;
cutoff_freq = 8 / (fs/2); 
h = ffilt("lp", order, cutoff_freq);

demux_signals = zeros(6, length(t));
for i = 1:6
    mixed = fdm_signal .* sin(2 * %pi * freqs(i) * t);
    demux_signals(i, :) = filter(h, 1, mixed);
end

scf(1);
clf;
for i = 1:6
    subplot(3,2,i);
    plot(t, signals(i, :));
    title('Original Signal f=' + string(freqs(i)));
end

scf(2);
clf;
plot(t, fdm_signal);
title('FDM Signal');

scf(3);
clf;
for i = 1:6
    subplot(3,2,i);
    plot(t, demux_signals(i, :));
    title('Demultiplexed Signal f=' + string(freqs(i)));
end

```

### GRAPH:

<img width="1834" height="1019" alt="image" src="https://github.com/user-attachments/assets/5589c46a-59c2-42ed-81ed-f82303f26da8" />
<img width="1793" height="1003" alt="image" src="https://github.com/user-attachments/assets/cfa58e97-d548-4439-9dea-2a5b75cfe560" />
<img width="1564" height="902" alt="image" src="https://github.com/user-attachments/assets/21cc0e9d-04f4-4410-9fb7-2660c5d9554b" />


### TABULATION:

![WhatsApp Image 2025-11-28 at 16 34 39_9b9c1784](https://github.com/user-attachments/assets/c39e93b0-4bf7-4887-ad87-da1fbf0ade71)
![WhatsApp Image 2025-11-28 at 16 34 35_f9e1c093](https://github.com/user-attachments/assets/2090c228-1c5c-4d38-968d-f262293a4025)

### RESULTS:

The program successfully simulates FDM and demultiplexing for multiple frequency signals with filtering to recover original signals accurately in Scilab.
