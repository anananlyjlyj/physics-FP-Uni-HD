## Measurements and evaluation

### 1. Calibration high frequency pulses

### 2. Measurement of relaxation time

#### 2.1 Measurements of relaxation times 

##### 1. Measurement T_2 by spin echo method

We select pulse sequence I-II and $\tau =10​$ ms. (What is repetition rate 1/3 Hz?)

##### 2. Measurement T_2 by Carr-Purcell sequence



##### 3. Measurement T_1



#### 2.2 Systematics of relaxation times for 2 probes

According to the description in last section we do the measurements for probes Gr 500 and Gr 600. 

Table 3.1: 

| Probes\relaxation time | T_2 by spin echo [ms] | T_2 by Carr-Purcell [ms] | T_1 by spin echo [ms] |
| ---------------------- | --------------------- | ------------------------ | --------------------- |
| Gr 500                 | 62.4                  | 66.1                     | 68.1                  |
| Gr 600                 | 78.6                  | 84.0                     | 99.2                  |

### 3. Chemical shift

#### 3.1 Substances identification

First we use a probe to get familiar with the measurement. We can see that the intensity is distributed in broad range because of inhomogeneity of the magnetic field.  Its width is determined by? Then we use the pressure air to put the probe into rotation and repeat the measurement. We observe clearly some peaks, since in that way the inhomogeneity is cancelled out.

We do the measurements for probes A+, B, B+, C, C+, D, D+ and E, E+ (probe A was broken in previous experiment). See Appendix ...(Name) The LabVIEW program shows us the measured amplitude of signal changing with time and plot its Fourier-transform in frequency space next to it. In the lower part of the program we give the approximate range of each peak we see in Fourier plot. The program makes a fit using the data and calculate ppm from the position of each peak.(How did the program calculate it?) Comparing two spectra for every substance, we find out that the mixed reference substance in *+ probe corresponds to the most left peak in every spectrum of *+ probe. Subsequently we calculate the difference of ppm given by the LabVIEW program. 

Table 3.2: 

| relative to TMS peak(0. peak) | A+   | B+   | C+   | D+   | E+   |
| ----------------------------- | ---- | ---- | ---- | ---- | ---- |
| 1. peak chemical shift        | 2.2  | 2.1  | 2.0  | 3.9  | 2.6  |
| 2. peak chemical shift        | 3.9  | 6.9  | 11.6 | 6.3  | 7.5  |
| 3. peak chemical shift        | 6.3  |      |      |      |      |

We use data on Figure 1.1 to match the chemical shift with possible compounds. We associate five probes to the substances: (Do we need to illustrate in detail?)

<img src="https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/F61%20Nuclear%20Magnetic%20Resonance/substances.png" width="280" height="170">

| A             | B       | C           | D                 | E      |
| ------------- | ------- | ----------- | ----------------- | ------ |
| fluoroacetone | p-xylol | acetic acid | fluoroacetonitril | toluol |

where we use the intensity of the measured frequency response to separate Toluol and p-xylol, which have the same chemical shifts because of same compounds. Since -CH_3 replaces one of the H-atom on benzene in p-xylol, we expect two peaks which have less amplitude difference, compared with two peaks of toluol.

Only the peak we measure for FCH_2-CN do not correspond to what we expect. We expect only one peak for 2 H-atoms in -CH_2-, because the resonance frequency for fluor is much higher than the range of our measurement. However, we observe 2 peaks with almost same amplitude close to each other. It can be explained by the spin-spin interaction of F-atom with protons, one parallel and one antiparallel.

#### 2.3 Characteristics quantity of the experiment

From the measured data we can infer some information about the magnetic field inside the coil and about energy.

The external magnetic field $B_0$ can be calculated from the Larmor frequency $\nu_L$, which is assumed to roughly equal the high frequency $\nu_{HF}=19.8 MHz$(woher?), since their difference the working frequency $\nu_w\approx 500 Hz$ is relative small:
$$
B_0 =\frac{\omega_L}{\gamma}=\frac{f_L \cdot 2 \pi}{\gamma}=\frac{19.8\cdot 10^6s^{-1}\cdot 2 \pi}{2.6752\cdot10^8 s^{-1}T^{-1}}\approx 0.48 T
$$
The induced magnetic field $B_1$ can be calculated from the pulse time difference we set to achieve 90° pulse $\Delta t=1.29\mu s$ , which we read from oscilloscope:
$$
B_1 = \frac{\alpha}{\gamma\cdot\Delta t}=\frac{\pi/2}{2.6752\cdot10^8 s^{-1}T^{-1}\cdot 1.29\cdot10^{-6}s}\approx 4.3 mT
$$
The energy resolution of our measurements can be calculated from the FWHM of a peak $\Delta f_{FWHM}=19.9 Hz$ taken from the first peak of A+ using 2 cursors in the program:
$$
\Delta E_{res} = \Delta f_{FWHM} \cdot h \approx 8\cdot10^{-14} eV
$$
The energy difference for the different fluor states can be calculated from the frequency difference of second peak and third peak of A+ $\Delta f=48 Hz$:
$$
\Delta E_{dipol}=\Delta f \cdot h\approx 2\cdot10^{-13} eV
$$

### 4. Imaging with NMR

#### 4.1 1d imaging

First we measure the image of 15mm oil (Appendix ...).

#### 4.2 2d imaging





