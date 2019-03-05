# F20 Magneto-optical trap

- [F20 instruction](https://www.physi.uni-heidelberg.de/Einrichtungen/FP/anleitungen/F20.pdf)
- Literature:
- [Protocol]
- Data and evaluation as below

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
Integrate over all velocities in weak laser field($P_0-P_1=1​$):
$$
\kappa=\kappa_0e^{-(\nu-\nu_0)^2/2\sigma_\nu^2},\kappa_0=h\nu n_0 \alpha_0 \sqrt\frac{m}{2\pi k_B T}\frac{c}{\nu_0}\frac{\pi \Gamma}{2},\sigma_{\nu}=\nu_0 \sqrt\frac{k_B T}{mc^2}
$$
Populations with spontaneous emission rate $\gamma$, absorption rate $\alpha​$:
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

  *  $\nu=\nu_0,v_{probe}=v_{pump}=0$ hole burning for v near 0. -> absorption coefficient vs. the laser frequency offset from resonance: Doppler-broadened profile with **Lamb dip** at $\nu=\nu_0​$ (increasing intensity leads to power broadening of the Lamb dip)

### Multilevel effects

* **Crossover resonance**: additional narrow absorption dips arising because several upper or lower levels are close enough in energy that their Doppler-broadened profiles overlap. 

  $V$-system and $\Lambda$-system: here V-system

  Without pump beam: net absorption = Gaussian($\nu_1​$) + Gaussian($\nu_2​$). If separation small compared to the Doppler width -> single broadened absorption profile

  With pump beam: dip at $\nu_1,\nu_2$ and at crossover frequency $\nu_{12}=(\nu_1+\nu_2)/2$ 

  At $\nu_{12}$ the pump and probe beams are resonant with the same two opposite velocity groups: $v=\pm c(\nu_2-\nu_1)/2\nu_{12}$. Atoms at one of these two $v$ will be resonant with one excited state and atoms at the opposite $v$ with the other excited state.

* **Optical pumping**: excited level can spontaneously decay to more than one lower level

### Energy levels of Rubidium

* Fine structure levels

  $^{(2S+1)}L_J$  with total orbital angular momentum $\vec L$, total electronic spin angular momentum $\vec S$, total electronic angular momentum $\vec J$ , in the L-S coupling regime $\vec J= \vec L + \vec S$.

  Rb = [Kr] $5 S^1​$ and thus ground state $^2 S_{1/2}​$, excited states $^2 P_{1/2}, ^2P_{3/2}​$ 

* Hyperfine structure levels

  nuclear spin angular momentum $\vec I$, total angular momentum $\vec F=\vec I + \vec J$. $|J-I|\leq F \leq |J+I|$.

  2 natural isotopes of Rb: 72% $^{85}$Rb with $I=5/2$ and 28% $^{87}$Rb with $I=3/2$. For both, two hyperfine levels with in  $^2 S_{1/2}$ and $^2 P_{1/2}$, 4 hyperfine levels within $^2 P_{3/2}$.

* Allowed transitions

  $^2 S_{1/2}$ to $^2 P_{1/2}$ all ~ 795 nm, $^2 S_{1/2}$ to $^2 P_{3/2}$ all around 780 nm(here would be discussed). Dipole transitions: $\Delta F = 0, \pm 1$. -> For Rb transitions fall into two groups of 3, groups well separated, within group transitions close spaced in energy.

### Frequency modulation(FM) spectroscopy



## Part I: Doppler free spectroscopy

### § Familiarization with basic monitoring and controlling units in the optics lab

* D2-line spectra of both Rubidium isotopes: 85, 87
* Spectrum of cooler laser, repumper laser



## Part II: Laser cooling

### 1. Beam path characterization

### 2. Alignment of the MOT beams

### 3. Laser locking

### 4. Magnetic coils

### 5. Achievement of the MOT

## Part III: Optimization of fluorescence signal & Measurement of loading characteristics of the MOT at different detunings and magnetic field gradients

### 1. Improvement of the MOT and of the fluorescence signal

### 2. Acquisition of the loading curve at different detunings and magnetic field gradients

## Part IV: Release and recapture measurements

