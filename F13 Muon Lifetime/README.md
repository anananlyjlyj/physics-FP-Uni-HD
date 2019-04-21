# F75 Muon Lifetime

- [F13 instruction](https://www.physi.uni-heidelberg.de/Einrichtungen/FP/anleitungen/F13.pdf)

  [homepage](http://www.physi.uni-heidelberg.de/~bachmann/Lehre/F13.php)

  For data analysis we use a C++ toolkit [ROOT](https://root.cern.ch/) with pre-equipped [programs](https://gitlab.cern.ch/HD-FP13/Students).

- [Protocol]

- Evaluation:

## Goals

- **determine the lifetime of muons** (will be measured with an accuracy of about 5%)

  Literature value: $\tau = 2196.9803(22)$ ns 

- **observe the muon spin precession in a magnetic field**

- **extract the weak interaction Fermi coupling constant  from your measurements**

  $G_F^2 = \frac{192 \cdot \pi^3 \cdot \hbar}{\tau_0\cdot (m_\mu \cdot c^2)^5}$

- **measure the Larmor frequency of the muon, to determine the magnetic moment of the muon**

-  **interpret results in the context of parity violation in the decay of the muon.**

## Part A: Preparation

### 1. Verification of the hardware

* output pulses of the photomultiplier with oscilloscope -> see protocol
* effect of using a terminating resistor of 50 \Ohm compared to internal termination of oscilloscope (1 M\Ohm)
* Questions:
  *  How are photons detected in a photomultiplier? -> Photoelectric effect
  * How are the photons generated in the scintillator?
  * How much energy deposit relativistic particles such as muons from
    cosmic radiation in a scintillator?
  * Which impact has the terminator on the waveform?
  * How do pulses from photomultiplier tubes look like?
  * What determines the height of these pulses?

**now use FP13neu.vi, Threshold.vi**

* Questions:

  * What is the functionality of the discriminators?
  * Which impact has changing the thresholds?

* Compare signal of one photomultiplier before/after the discriminator 

  * observation, explanation

* average pulse width ($\Delta t$) after discriminator: 

  dimensions of detector: 

  => the absolute rates of cosmic particles expected in the detector: 

### 2. Determination of optimal operating settings

* dark-pulse rates: 

**now use Einzelraten.vi, Diskriminatoren.vi**

* **use Effizienz-Rate.vi** measure efficiency of each layer -> see table
* rate of random coincidence $R_{12}=R_1 R_2 \Delta t$  (formula is only valid if the rate of real coincidences is much smaller than the rate of a single layer)

## Part B: Measurements and Analysis

### 3. Data acquisition and on-line verification of data

**use Lebensdauer.vi**

### 4. Filtering and checking the recorded data

* bit patterns correspond to the four categories, e.g. layer 123456

  * upwards decays: e.g. on layer 4: 111100 -> 000100
  * downwards decays: e.g. on layer 4: 11100 -> 000100
  * after-pulses: e.g. on layer 4: 111110 -> 000110
  * all remaining event

* a function for downwards decays and a more general function for the after-pulses

  * downwards decay

    ```c++
    int fp13Analysis::findDecayDownward(int timeBin)
    {
    	if ((nLayers - 1) == lastMuonLayer)
    		return -1;
    	
    	if ((1 << (lastMuonLayer + 1)) & detectorHitMask[timeBin]){
    		return lastMuonLayer;
    	}
    	
    	return -1;
    }
    ```

  * more general function for the after-pulses

    ```c++
    int fp13Analysis::findAfterpulsesImproved(int timeBin, int startLayer)
    {
        
        if (-1 == startLayer)
            // startLayer = nLayers;
            startLayer = lastMuonLayer;
    
        for (int iLayers = startLayer-1; iLayers >=0; iLayers--){
            if((1 << iLayers) & detectorHitMask[timeBin]){
                return iLayers;
            }
        }
    
    	return -1;
    }
    ```

### 5. Determination of the lifetime of the muon and evaluations of systematic errors

**now use [Lebensdauer.C](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/F13%20Muon%20Lifetime/Lebensdauer.C)** 

- Questions for histograms:

  - Where can you ﬁnd similarities in the decays in diﬀerent layers?
  - Are there histograms particularly diﬀerent from other histograms?
  - How do the after-pulses aﬀect the spectra? What are the consequences for your next step?

  - Correction for after-pulses: see [table](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/F13%20Muon%20Lifetime/Scaling.ods)

  - Why is the speciﬁc ineﬃciency factor necessary when calculating the number of start patterns for after-pulses in downward decays? Remember that after-pulses occur only if the scintillator was passed by a muon previously. 

  - After subtracting the after-pulses using our scaling factors. How does the appearance of the spectra change? ->  the records for decays with long times are approximately zero.

  - Plot both the scaled and the unscaled histogram in order to understand the contribution and intensity of the after-pulses. [FitObenUntenMitScaling](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/F13%20Muon%20Lifetime/FitObenUntenMitScaling.pdf), [LebensDauerFitMitScaling](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/F13%20Muon%20Lifetime/LebensDauerFitMitScaling.pdf), [FitObenUntenOhneScaling](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/F13%20Muon%20Lifetime/FitObenUntenOhneScaling.pdf), [LebensDauerFitOhneScaling](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/F13%20Muon%20Lifetime/LebensDauerFitOhneScaling.pdf).

    Decide which spectra and layers to use for the rest of the analysis in order to ﬁt the lifetime.

- Fit using function $N(t)=N(\mu)e^{-t/\tau_0}+N_{BG}$ , set initial value and range of fit parameters 

  ```c++
  // par[0] background level
  // par[1] number of muons
  // par[2] muon lifetime
  par[1] * Exp(-x[0] / par[2])) + par[0]
  ```

  - What appears to be useful?
  - At what time the capture of negative muons gives no contribution to the spectrum anymore?
  - What does this tell you for your ﬁt?

  Fit the lifetime after the correction for the after-pulses (layer 2): [FitFuncF](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/F13%20Muon%20Lifetime/FitFuncF.pdf) for fit parameters(),  [FitFuncF2](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/F13%20Muon%20Lifetime/FitFuncF2.pdf) (), [FitFuncF3](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/F13%20Muon%20Lifetime/FitFuncF3.pdf) ()

**now use [Einfangzeiten.C](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/F13%20Muon%20Lifetime/Einfangzeiten.C)** fit using function $N(t)=N(\mu_+)e^{-t/\tau_0}(\frac{1}{f}e^{-t/\tau_c}+1)+N_{BG}$  where $f = \frac{N(\mu_+)}{N(\mu_-)}$ Since the measured decay spectra include both contributions from the decay of free muons and muons which were captured by atoms. In addition to the lifetime of the muons, you can also measure from the same data also the much shorter lifetime of the negative muons, being captured by the nuclei of the aluminium or copper, the so called capturing time. This is about 880 ns for aluminium.

??[Einfangszeiten.eps](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/F13%20Muon%20Lifetime/Einfangzeit.eps)

* Check the results of the ﬁt and in particular compare the results for the decays upwards and downwards. Discuss which of the parameters should be similar for both decay spectra and in which parameters it is possible to have diﬀerences. Does the result match your expectations?

* Determination of the systematic errors of the lifetime

  * influence of the fit range

  * Inaccuracy of the correction for the after-pulses (vary the correction factors for the after-pulses )

  * Inﬂuence of the ratio f ($\pm 1 \sigma, \pm 2 \sigma$)

    In the relevant experiments for this energy range, the ratio was determined to be $f \approx 1.275 \pm0.05$. One can specify this measured value for the ratio when making the ﬁt

  [Fit parameters](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/F13%20Muon%20Lifetime/Lebensdauer.ods), plot results(closest lifetime fit: 13): Zerfall "1Both, ... [13Both](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/F13%20Muon%20Lifetime/13Both.pdf)" Lebensdauer "1All, ... [13All](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/F13%20Muon%20Lifetime/13All.pdf)". (NOTE: 13th fit of capturing time is ok, oben: $976.4 \pm 123.9$ ns, unten: $1070 \pm 183.5$, together: $976.7 \pm 103.9$ ns)

  

  TODO: how to estimate the bias arising from the ﬁt ranges and combine all diﬀerent systematic uncertainties

### 6. Polarization measurement

The magnetic field $B = I \cdot 2.0 \cdot 10^{-4}$. For a storm $20$ A, the magnetic field $B = 4$ mT.

Why are the muons polarised?

To determine the polarisation you have to compare the measurement with and without the magnetic ﬁeld (including the scaling factor correction). 

**now use Asymmetrie.C** 

* The asymmetry function $\frac{Z^{without}(t) - Z^{with}(t)\cdot s}{Z^{without}(t) + Z^{with}(t) \cdot s} = \frac{P\cdot A}{2} \cos{(\omega_{Larmor} t + \phi)} + c$ . Now one must consider that the duration of the measurements with and without the magnetic ﬁeld is diﬀerent and therefore the number of entries in the histograms are diﬀerent. To do so, one has to scale in the subtraction or addition the number of entries in the histogram with the magnetic ﬁeld by using the scaling-factor $s = \frac{Z_0^{without}}{Z_0^{with}}$ (derived from the integrals of the respective (with and without B) histograms listed there.)  Note that the asymmetry functions for the decays
  upwards and downwards decays are determined separately, and hence also the scaling factor for both asymmetry functions has to be determined separately.

  Scaling factor for correction see table before.

* Now look at the data from each layer. Do they diﬀer from those without a magnetic ﬁeld? Choose again the best data set. Compare again the results for the decays downwards and upwards. Which of them seems to have less systematic problems? Try also to vary the initial values of the parameters until the ﬁt function describes well the data. Test also how much the ﬁt result depends on the ﬁt range. 

* Questions:

  * What values do you expect for the parameters? (Concerning $\Phi$: think about with which polarisation the muons are created and with which polarisation they reach the Earth’s surface).
  * Are the expected values close to those calculated by the program? 
  * Which parameter shows the parity violation in the weak interaction?
  * Calculate the magnetic moment of the muon from the measured Larmor frequency.
  * Discuss the results critically. In particular, think about whether your measurements show signiﬁcant polarisation of the cosmic muons. How
    can you show this quantitatively?

**now use AccumulatedAsymmetrie.C** to measure the polarisation with an increased data set (with a
higher statistics, combine our dataset with [those of other groups())





## TODO: script Chapter 3 & 4