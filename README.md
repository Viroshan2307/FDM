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

<img width="650" height="963" alt="Screenshot 2025-11-28 222226" src="https://github.com/user-attachments/assets/0220b3e6-2914-49c9-9aed-492c79b106fe" />


### GRAPH:
<img width="1901" height="1004" alt="Screenshot 2025-11-28 221631" src="https://github.com/user-attachments/assets/96d6095e-859e-4872-991b-0e08a31cd9dc" />
<img width="1857" height="994" alt="Screenshot 2025-11-28 221646" src="https://github.com/user-attachments/assets/2d1bd14b-c2d5-46f8-9c29-5d62a31c97d3" />
<img width="1904" height="998" alt="Screenshot 2025-11-28 221657" src="https://github.com/user-attachments/assets/180f52c4-a2a0-4ce6-9405-3eee7368d7ef" />




### TABULATION:
![WhatsApp Image 2025-11-28 at 16 35 00_17a9a07c](https://github.com/user-attachments/assets/f3ac05fa-8c8a-464c-849d-7a9408409a0e)
![WhatsApp Image 2025-11-28 at 16 35 10_0f9a749d](https://github.com/user-attachments/assets/29f6a932-4e55-4206-82db-11bbd071c95e)


### RESULTS:

The program successfully simulates FDM and demultiplexing for multiple frequency signals with filtering to recover original signals accurately in Scilab.
