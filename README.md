# Design-of-FIR-Filters-using-hamming-window

# DESIGN OF LOW PASS FIR DIGITAL FILTER 

# AIM: 
          
  To generate design of high pass FIR digital filter using SCILAB 

# APPARATUS REQUIRED: 

  PC Installed with SCILAB 

# PROGRAM 
```
clc;
clear;
close;

// Input parameters
M = input('Enter the Odd Filter Length = ');
Wc = input('Enter the Digital Cutoff Frequency (in radians) = ');
alpha = (M - 1) / 2;   // Center value

// Ideal Low-Pass Filter impulse response (Fourier series)
for n = 1:M
    if (n == alpha + 1) then
        hd(n) = Wc / %pi;
    else
        hd(n) = sin(Wc * ((n - 1) - alpha)) / (%pi * ((n - 1) - alpha));
    end
end

// Hamming Window
for n = 1:M
    W(n) = 0.54 - (0.46 * cos((2 * %pi * (n - 1)) / (M - 1)));
end

// Apply window to ideal response
h = hd .* W;

// Display filter coefficients
disp(h, 'Filter Coefficients are');

// Compute and plot frequency response
[hzm, fr] = frmag(h, 256);

subplot(2, 1, 1);
plot(2 * fr, hzm);
xlabel('Normalized Digital Frequency (ω)');
ylabel('Magnitude');
title('Frequency Response of FIR LPF using Hamming Window');
xgrid();

hzm_dB = 20 * log10(hzm + 1e-12);
subplot(2, 1, 2);
plot(2 * fr, hzm_dB);
xlabel('Normalized Digital Frequency (ω)');
ylabel('Magnitude (dB)');
title('Frequency Response (dB) of FIR LPF using Hamming Window');
xgrid();

```

# OUTPUT

<img width="1920" height="853" alt="image" src="https://github.com/user-attachments/assets/c9809da2-467b-4c7c-b931-e3defd8243a0" />


# RESULT
To generate design of low pass FIR digital filter using SCILAB completed sucessfully.


