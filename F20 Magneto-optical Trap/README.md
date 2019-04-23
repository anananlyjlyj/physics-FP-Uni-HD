# F20 Magneto-optical trap

- [F20 instruction](https://www.physi.uni-heidelberg.de/Einrichtungen/FP/anleitungen/F20.pdf)

- Literature:

- [Protocol]

- Data and evaluation as below

  Note: when measure and save the data, we found accidently 1 redundant data in Part II, which might be a double measurement of $\Delta \nu=-12$ or $-14$ . Same thing happened for data in Part III, which might be a double measurement of time difference between 11 and 27.

## Introduction

### Not saturated absorption

Lambert-Beer absorption law: 
$$
\frac{dI}{dx}=-\kappa I,\kappa =h\nu n_0 \alpha(P_0 - P_1),\alpha=\alpha_0 \mathcal{L}(\nu,\nu_0), \mathcal{L}(\nu,\nu_0)=\frac{1}{1+4(\nu-\nu_0)^2/\Gamma^2}
$$

$$
dn=n_0 \frac{1}{\sqrt{2\pi}\sigma_v}e^{-v^2/2\sigma_v^2}dv, \sigma_v=\sqrt\frac{k_B T}{m}
$$

Using Doppler shifts, for the atoms:
$$
\nu_0'=\nu_0(1+\frac{v}{c})
$$
Integrate over all velocities in weak laser field($P_0-P_1=1$):
$$
\kappa=\kappa_0e^{-(\nu-\nu_0)^2/2\sigma_\nu^2},\kappa_0=h\nu n_0 \alpha_0 \sqrt\frac{m}{2\pi k_B T}\frac{c}{\nu_0}\frac{\pi \Gamma}{2},\sigma_{\nu}=\nu_0 \sqrt\frac{k_B T}{mc^2}
$$
Populations with spontaneous emission rate $\gamma$, absorption rate $\alpha$:
$$
P_0-P_1=\frac{1}{1+2 I/I_{sat}}, I_{sat}=\frac{\gamma}{\alpha} \Rightarrow \kappa=\kappa_0 \sqrt{P_0-P_1}e^{-(\nu-\nu_0)^2/2\sigma_\nu^2}
$$

### Saturated absorption

-> **Pump beam**(strong), <- **probe beam**(weak)
$$
\alpha=\alpha_0 \mathcal{L}(\nu,\nu_0'')
$$
Doppler shift, for the pump beam:
$$
\nu_0''=\nu_0(1-\frac{v}{c})
$$

$$
\Rightarrow v_{pump}=c(1-\nu/\nu_0)
$$

required velocity for atoms. -> $dn_0=P_0 dn$ density of ground state atoms as function of velocity: Maxwellian with "hole burning" by the pump beam near $v=v_{pump}$.

* For pump beam: 
  * Far from the natural resonance ($|\nu-\nu_0|>>\Gamma$): $P_0-P_1=1$, only for atoms $v=v_{pump}$.
  * Near resonance frequency: A strong resonant laser field($I$ large) causes such rapid transitions in both directions that $P_0=P_1$ -> "saturate" the transition

* For probe beam: 

  * far from the natural resonance: absorption for $v=v_{probe}=-v_{pump}$.  Also because absorption $\propto (P_0-P_1)$, which $\approx1$ except for $v=v_{pump}$. 

    Pump beam not affect probe beam absorption.

  *  $\nu=\nu_0,v_{probe}=v_{pump}=0$ hole burning for v near 0. -> absorption coefficient vs. the laser frequency offset from resonance: Doppler-broadened profile with **Lamb dip** at $\nu=\nu_0$ (increasing intensity leads to power broadening of the Lamb dip)

### Multilevel effects

* **Crossover resonance**: additional narrow absorption dips arising because several upper or lower levels are close enough in energy that their Doppler-broadened profiles overlap. 

  $V$-system and $\Lambda$-system: here V-system

  Without pump beam: net absorption = Gaussian($\nu_1$) + Gaussian($\nu_2$). If separation small compared to the Doppler width -> single broadened absorption profile

  With pump beam: dip at $\nu_1,\nu_2$ and at crossover frequency $\nu_{12}=(\nu_1+\nu_2)/2$ 

  At $\nu_{12}$ the pump and probe beams are resonant with the same two opposite velocity groups: $v=\pm c(\nu_2-\nu_1)/2\nu_{12}$. Atoms at one of these two $v$ will be resonant with one excited state and atoms at the opposite $v$ with the other excited state.

* **Optical pumping**: excited level can spontaneously decay to more than one lower level

### Energy levels of Rubidium

* Fine structure levels

  $^{(2S+1)}L_J$  with total orbital angular momentum $\vec L$, total electronic spin angular momentum $\vec S$, total electronic angular momentum $\vec J$ , in the L-S coupling regime $\vec J= \vec L + \vec S$.

  Rb = [Kr] $5 S^1$ and thus ground state $^2 S_{1/2}$, excited states $^2 P_{1/2}, ^2P_{3/2}$ 

* Hyperfine structure levels

  nuclear spin angular momentum $\vec I$, total angular momentum $\vec F=\vec I + \vec J$. $|J-I|\leq F \leq |J+I|$.

  2 natural isotopes of Rb: 72% $^{85}$Rb with $I=5/2$ and 28% $^{87}$Rb with $I=3/2$. For both, two hyperfine levels with in  $^2 S_{1/2}$ and $^2 P_{1/2}$, 4 hyperfine levels within $^2 P_{3/2}$.

* Allowed transitions

  $^2 S_{1/2}$ to $^2 P_{1/2}$ all ~ 795 nm, $^2 S_{1/2}$ to $^2 P_{3/2}$ all around 780 nm(here would be discussed). Dipole transitions: $\Delta F = 0, \pm 1$. -> For Rb transitions fall into two groups of 3, groups well separated, within group transitions close spaced in energy.

### Frequency modulation(FM) spectroscopy



### Sisyphus cooling

a type of [laser cooling](https://en.wikipedia.org/wiki/Laser_cooling) of atoms used to reach temperatures below the [Doppler cooling limit](https://en.wikipedia.org/wiki/Doppler_cooling_limit).

Sisyphus cooling can be achieved by shining two counter-propagating laser beams with [orthogonal](https://en.wikipedia.org/wiki/Orthogonality) [polarization](https://en.wikipedia.org/wiki/Polarization_(waves)) onto an atom sample. The two interfering  beams create a standing wave with a polarization gradient that alternates between [σ+, π and σ− polarisation](https://en.wikipedia.org/wiki/S_and_p_polarizations). Atoms moving through the potential landscape along the direction of the standing wave lose [kinetic energy](https://en.wikipedia.org/wiki/Kinetic_energy) as they move to a potential maximum, at which point [optical pumping](https://en.wikipedia.org/wiki/Optical_pumping) moves them to a lower-energy state, thus ridding them of the potential energy they carried. 

Repeated cycles of converting kinetic energy to potential energy, and subsequent loss of this potential energy via optical pumping, allow the atoms to reach temperatures orders of magnitude below those available through simple [Doppler cooling](https://en.wikipedia.org/wiki/Doppler_cooling). 

## Part I: Doppler free spectroscopy

### § Familiarization with basic monitoring and controlling units in the optics lab

* relevant infos: Doppler free spectroscopy and laser cooling.
  * Basic laser absorption spectroscopy
  2. Saturated absorption and Doppler free spectroscopy
  3. Energy levels of Rubidium
  4. Frequency modulation (FM) spectroscopy

* D2-line spectra of both Rubidium isotopes: 85, 87

  measure spectrum of cooler laser and repumper laser -> analyse best of the 2

  **TODO Evaluation:**

  * [All peaks]([https://raw.githubusercontent.com/anananlyjlyj/physics-FP-Uni-HD/master/F20%20Magneto-optical%20Trap/Part%20I/All_Peaks.bmp](https://raw.githubusercontent.com/anananlyjlyj/physics-FP-Uni-HD/master/F20 Magneto-optical Trap/Part I/All_Peaks.bmp))

  * To perform the frequency measurements you have to calibrate the horizontal axis, by converting it from time to frequency for 1 dataset and apply to the others.

  * From 2-transitions-combined datasets, by fitting each absorption profile with a Gaussian and comparing the distance between the centers of the two profiles, measure the multiplet separation

  * From single-transition datasets measure the natural **line width** of the hyperfine lines from the Lamb dips and the **temperature** of the atomic sample from the Doppler profile.

    fit each absorption profile with a Gaussian, subtract it, then fit the real absorption dips with a Lorentzian (only the ones that have a good SNR). To have a better fit, it
    is suggested to mask the areas where the Lorentzian dips are. Extract from the FWHM of the Doppler valleys the temperature of the atomic sample and compare it with the Doppler broadening expected for a thermal gas. From the Lorentzian fit extract the line width and compare it to the theoretical natural line width of the transitions

  * From these recorded Doppler free spectra you can measure the D2 line hyperfine energy level separation

    find in the derivative the six zero crossings and you have to compare their frequency separation (it's a relative frequency measurement!) with the theoretically expected  frequency separations between the hyperfine transitions

    

## Part II: Laser cooling

* relevant infos
  * Radiative optical forces
  * Optical molasses
  * Magneto-Optical Trap
  * Temperature regimes accessible in laser cooling
  * Trap loading
  * Temperature measurement via release and recapture

### 1. Beam path characterization

* For the cooling beam:
  * the power going to the spectroscopy
  * the power going to the MOT beam path
  * the power before the AOM
  * the power after the diaphragm which selects the first order of the AOM
    diffraction (if possible optimize it by slightly adjusting the AOM angle)
  * the power before the fiber
  * the power after the fiber (with repumping beam blocked)
* For the repumping beam:
  * the power going to the spectroscopy
  * the power going to the MOT beam path
  * the power before the fiber
  * the power after the fiber (with cooling beam blocked)

For each beam separately you should try to optimize the fiber coupling via a procedure called "beam walking" if the power is not above 10.5 mW for the cooler or 2 mW for the repumper.

### 2. Alignment of the MOT beams

use the first mirror to align the beam to the first viewport and the second mirror for align the beam to the center of the second viewport. 

### 3. Laser locking

Cooler laser is locked on the crossover between F = 3 → F = 2 and F = 3 → F = 4 levels, while the Repumper on the F = 2 → F = 3 line

### 4. Magnetic coils

choose one direction and increase the current slowly up to a value of 6 A.

### 5. Achievement of the MOT

see a MOT with the IR finger camera on the black and white TV screen

## Part III: Optimization of fluorescence signal & Measurement of loading characteristics of the MOT at different detunings and magnetic field gradients

### 1. Improvement of the MOT and of the fluorescence signal

adjust the photo diode to the fluorescence light emitted by the MOT by slightly improving the alignment of the mirror. 

play a little bit with the current of the z-Compensation coils, until you'll find the position which allows you to trap the biggest cloud with the strongest fluorescence.  Then try to adjust the power balance between the x-y-z MOT beams until you reach the highest fluorescence signal. Estimate
the average laser intensity in each of the six laser beams, it should be close to 3 mW.

Why should the detuning of the laser be at a fixed value for this procedure?

### 2. Acquisition of the loading curve at different detunings and magnetic field gradients

measure the loading curve for different configurations: vary the detuning from 14 MHz to the
resonance in steps of 2 MHz with respect to the F = 3 → F = 4 transition and at each detuning vary the gradient by changing the current through the quadrupole coils between 4.5A and 6A in steps of 0.5A.

Where do you see the best loading rate?

[Data](https://github.com/anananlyjlyj/physics-FP-Uni-HD/tree/master/F20 Magneto-optical Trap/Part II)

### 3. Evaluation

[Eva](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/F20 Magneto-optical Trap/Part II.ipynb)

**TODO Discussion:**

* Are the loss coefficients constant? What would it mean if they were dependent on the atom number? What is the behaviour in detuning?
* Plots interpretation

## Part IV: Release and recapture measurements

to estimate the temperature of the MOT

Choose the detuning and the magnetic field gradient that gave you the best loading rate

* 5 traces at such short duration that you don't see a change in the atom number
* 5 at such durations that you loose all the atoms
* 20 traces at durations in between to sample properly the expansion behavior

[Data](https://github.com/anananlyjlyj/physics-FP-Uni-HD/tree/master/F20 Magneto-optical Trap/Part III)

[Evaluation](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/F20%20Magneto-optical%20Trap/Part%20III.ipynb)

**TODO Discussion:**

* Is the calculated temperature compatible with the one that you expected to achieve?
* Plots interpretation



