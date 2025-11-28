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
clc;
clear; 
close;
fs=80000; 
N=floor(0.05*fs); 
t=(0:N-1)/fs;
fm=[564,574,584,594,604,614];
fc=[5640,5740,5840,5940,6040,6140];
Am=[6.7,6.8,6.9,7.0,7.1,7.2];
Ac=[13.4,13.6,13.8,14.0,14.2,14.4];
num=length(fm);
for i=1:num
    m(i,:)=Am(i)*sin(2*%pi*fm(i)*t);
end
fdm=zeros(1,N);
for i=1:num
    fdm = fdm + Ac(i)*cos(2*%pi*fc(i)*t).*m(i,:);
end
function h=FIR(fc1,fc2,fs,M,mode)
    n=-M:M; L=length(n);
    x1=2*fc1*n/fs; x2=2*fc2*n/fs;
    s1=ones(1,L); s2=ones(1,L);
    for k=1:L
        if x1(k)<>0 then s1(k)=sin(%pi*x1(k))/(%pi*x1(k)); end
        if x2(k)<>0 then s2(k)=sin(%pi*x2(k))/(%pi*x2(k)); end
    end
    lp1=(2*fc1/fs)*s1; lp2=(2*fc2/fs)*s2;
    w=(0.54-0.46*cos(2*%pi*(n+M)/(2*M)));
    if mode==1 then h=lp1.*w;
    else h=(lp2-lp1).*w; end
    h=h/sum(h);
endfunction
M=300;
for i=1:num
    bp=FIR(fc(i)-600,fc(i)+600,fs,M,2);
    iso=conv(fdm,bp,"same");
    mix=iso.*cos(2*%pi*fc(i)*t);
    lp=FIR(800,0,fs,M,1);
    demod(i,:)= (2/Ac(i))*conv(mix,lp,"same");
end
scf(1); 
clf;
for i=1:num subplot(num,1,i); plot(t,m(i,:)); end
scf(2); 
clf; 
plot(t,fdm);
scf(3); clf;
for i=1:num subplot(num,1,i); plot(t,demod(i,:)); end


### GRAPH:
<img width="1901" height="1004" alt="Screenshot 2025-11-28 221631" src="https://github.com/user-attachments/assets/96d6095e-859e-4872-991b-0e08a31cd9dc" />
<img width="1857" height="994" alt="Screenshot 2025-11-28 221646" src="https://github.com/user-attachments/assets/2d1bd14b-c2d5-46f8-9c29-5d62a31c97d3" />
<img width="1904" height="998" alt="Screenshot 2025-11-28 221657" src="https://github.com/user-attachments/assets/180f52c4-a2a0-4ce6-9405-3eee7368d7ef" />




### TABULATION:
![WhatsApp Image 2025-11-28 at 16 35 00_17a9a07c](https://github.com/user-attachments/assets/f3ac05fa-8c8a-464c-849d-7a9408409a0e)
![WhatsApp Image 2025-11-28 at 16 35 10_0f9a749d](https://github.com/user-attachments/assets/29f6a932-4e55-4206-82db-11bbd071c95e)


### RESULTS:

The program successfully simulates FDM and demultiplexing for multiple frequency signals with filtering to recover original signals accurately in Scilab.
