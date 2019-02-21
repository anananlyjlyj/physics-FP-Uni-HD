# F61 Nuclear Magnetic Resonance

- [F61 instruction](https://www.physi.uni-heidelberg.de/Einrichtungen/FP/anleitungen/F61.pdf)

- Literature: [Online book by Joseph P. Hornak](http://www.cis.rit.edu/htbooks/nmr/)

  Short lecture: [NMR Spectroscopy](https://www.youtube.com/watch?v=SBir5wUS3Bo&t=150s)

- Applications of NMR

  - [Spectroscopy of ^31P](http://www.nmr.uni-duesseldorf.de/main/menergie.html): study energy balance when transforming ATP into ADP in living cells
  - [MRI brain atlases](https://www.uantwerpen.be/en/research-groups/bio-imaging-lab/research/mri-atlases/)
  - [Digital fish library](http://www.digitalfishlibrary.org/)
  - MRI
    
    <img src="https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/F61%20Nuclear%20Magnetic%20Resonance/Banana.jpg" width="300" height="300">

- [Protocol]

  Experimental devices: Bruker minispec p20 for parts I & II, [Bruker minispec mq7.5](https://www.bruker.com/products/mr/td-nmr/minispec-mq-series/mq75-large-seed-analyzer/overview.html) for parts III.

- Data and evaluation as below

## Preparation: NMR Signal

### § Calibration high frequency pulses

* See the high frequency pulses on the oscilloscope

  The modulation frequency of **Puls I** for 1000 pulses per second is: 

  The modulation frequency of **Puls II** for 1000 pulses per second is: 

- Define the 90° and 180° pulses for 1 pulse every 3 seconds, using probe 1 :

  Puls I is a 90° pulse when its time duration is set to: ~ 1.29 $\mu s$

  Puls II is a 180° pulse when its time duration is set to: 

## Part I: Relaxation time

### § Measurements of relaxation times 

The time evolution of transverse magnetization is given by eq. 17 on the script
$$
M_{\perp}(t)=M^{0}_{\perp}e^{-\frac{t}{T_2}}
$$
where $T_2​$ is the spin-spin relaxation time.

#### 1. Measurement T_2 by spin echo method

* 

#### 2. Measurement T_2 by Carr-Purcell sequence

- 


The time evolution of longitudinal magnetization is given by eq. 18 on the script
$$
M_{\parallel}(t)=M^{0}(1-2e^{-\frac{t}{T_1}})
$$
where $T_1​$ is the spin-lattice relaxation time.

#### 3. Measurement T_1

* 

### § Systematics of relaxation times for 2 probes

| Probes\relaxation time | T_2 by spin echo | T_2 by Carr-Purcell | T_1  |
| ---------------------- | ---------------- | ------------------- | ---- |
| Gr 500                 |                  |                     |      |
| Gr 600                 |                  |                     |      |



## Part II: Chemical shift

### § Measurement chemical shift

The proton chemical shift in organic compounds relative to the reference substance Tetra-Methyl-Silan (TMS) is given by eq. 21 and shown in figure 10 on the script:
$$
\delta_i=\frac{\omega_{TMS}-\omega_i}{\omega_L}
$$
where $\omega_L=\gamma B_0$ is the free Larmor frequency (given by eq. 10 on the script, with $\gamma$ the gyromagnetic ratio of the nucleus, for the case of protons $\gamma=2.6752\cdot10^8 sec^{-1}Tesla^{-1}$ given by eq. 2), $\omega_i$ is the frequency modified by the chemical shift. 

<img src="https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/F61%20Nuclear%20Magnetic%20Resonance/ChemShift.png" width="280" height="280">

First we use probe 3 to get familiar with the measurement. We can see that the intensity is distributed in broad range because of inhomogeneity of the magnetic field.  Its width is determined by? Then we use the pressure air to put probe 3 into rotation and repeat the measurement. We observe clearly some peaks.



Then we do the measurements for probes A, B, C, D and E. Read from data on Figure 10 we can associate five probes to the substances:

<img src="https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/F61%20Nuclear%20Magnetic%20Resonance/substances.png" width="280" height="170">

| A             | B      | C       | D                 | E           |
| ------------- | ------ | ------- | ----------------- | ----------- |
| fluoroacetone | toluol | p-xylol | fluoroacetonitril | acetic acid |

where we use the intensity of the measured frequency response to separate Toluol and p-xylol, which have the same chemical shifts. Since -CH_3 replaces one of the H-atom on benzene in p-xylol, we expect two peaks which has less amplitude difference, compared with two peaks of toluol.

Only the peak we measure for FCH_2-CN do not correspond to what we expect. We expect only one peak for 2 H-atoms. However, we observe 2 peaks with almost same amplitude close to each other. It can be explained by the interaction of F-atom with protons, one parallel and one antiparallel.

## Part III: Imaging with NMR

### § One dimensional imaging in vertical direction

* [15mm oil in glass tube](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/F61%20Nuclear%20Magnetic%20Resonance/1d_image/Oil_15ml.txt)
* [50mm oil in glass tube](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/F61%20Nuclear%20Magnetic%20Resonance/1d_image/Oil_50_middle.txt)
* [Teflon structure immersed in oil in glass tube](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/F61%20Nuclear%20Magnetic%20Resonance/1d_image/Oil_Teflon.txt)
* 15mm sand + 4mm oil in glass tube: \1d_image\Oil_sand_*.txt

### § Two dimensional imaging

* [15mm oil in glass tube](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/F61%20Nuclear%20Magnetic%20Resonance/2d_image/Oil_Vertical_15.PNG)
* [A peanut with shell in glass tube](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/F61%20Nuclear%20Magnetic%20Resonance/2d_image/peanut_5avg_2_3d.PNG)
* [A piece of celery](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/F61%20Nuclear%20Magnetic%20Resonance/2d_image/celery_medium_3d.PNG)
* [A hot peper](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/F61%20Nuclear%20Magnetic%20Resonance/2d_image/pepper_2mm.PNG)

