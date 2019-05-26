# F13 Muon Lifetime

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

  pulse heights ~1V

* effect of using a terminating resistor of 50 \Ohm compared to internal termination of oscilloscope (1 M\Ohm) -> Figure 1.1, 1.2

* Questions:
  *  How are photons detected in a photomultiplier? -> Photoelectric effect & amplification by multiple anodes
  * How are the photons generated in the scintillator? -> certain transparent materials emit photons when charged particle passing through (Ionisation)
  *  How much energy deposit relativistic particles such as muons from cosmic radiation in a scintillator? ~eV, energy difference between the valence band and conduction band
  * Which impact has the terminator on the waveform? -> see above
  * How do pulses from photomultiplier tubes look like? -> Figure side
  * What determines the height of these pulses? -> ionisation of the charged particle

**now use FP13neu.vi, Threshold.vi**  see signals passing through the discriminators

* Questions:

  * What is the functionality of the discriminators?  -> produce pre-set signal when p.m. signal exceeds threshold
  * Which impact does changing the thresholds have? -> protocol, how many events would be registered

* Compare signal of one photomultiplier before/after the discriminator 

  * observation, explanation -> protocol, possible delay (possible integration activated after whole signal)

* average pulse width ($\Delta t$) after discriminator: 110 ns

  dimensions of detector: 32.5 cm * 82 cm * 9 cm

  **TODO:**
  
  => solid angle $\Omega = \int_{-82/2}^{82/2}{\int_{-32.5/2}^{32.5/2} {\frac{4.5 dx dy}{\sqrt{x^2 + y^2 + 4.5^2}^3}}} = 5.11946 $ sr
  
  => the absolute rates of cosmic particles expected in the detector: $r = \Omega * 0.325 * 0.82 = 95.5  $ 1/s

### 2. Determination of optimal operating settings

* dark-pulse rates: 

**now use Einzelraten.vi, Diskriminatoren.vi**

* **use Effizienz-Rate.vi** measure efficiency of each layer -> see table on protocol

  **TODO:**

* rate of random coincidence $R_{12}=R_1 R_2 \Delta t$  (formula is only valid if the rate of real coincidences is much smaller than the rate of a single layer)

## Part B: Measurements and Analysis

### 3. Data acquisition and on-line verification of data

**use Lebensdauer.vi**

### 4. Filtering and checking the recorded data

* bit patterns correspond to the four categories, e.g. layer 012345

  * upwards decays: e.g. on layer 3: 111100 -> 000100
  * downwards decays: e.g. on layer 3: 111100 -> 000010
  * after-pulses: e.g. on layer 2 and 1: 111100 -> e.g. 001000, 010000
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
    
    // Call the method:
    where = -1;
    // Fuelle die Histogramme, solange wir Nachpulse finden
    while (-1 != (where = findAfterpulsesImproved(
    				iTimeBin, where))) {
    	// Nachpuls gefunden - Flags setzen
    	eventFlags = static_cast<EventFlags>(
            eventFlags | FlagAfterpulseImproved);
    	// Detektorlage des Nachpulses
    	h2->Fill(where);
    	// Histogramm der Verzoegerungszeit fuer die
    	// getroffene Detektorlage
    	h22[where]->Fill(delay);
    ```

### 5. Final analysis: Determination of the lifetime of the muon and evaluations of systematic errors

* After-pulses scaling calculation -> see [table](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/F13%20Muon%20Lifetime/Scaling.ods)

  e.g. $s_2 = \frac{N2_{stop}}{N3_{stop} + N4_{stop} + N5_{stop}}$  after pulses on 2 layer, muon stops on 3/4/5 layer

* correct 2. layer upward decay [figure](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/F13%20Muon%20Lifetime/CorrectionMuonDecayUpwardsLayer2.pdf)

* Fitting for different time range (ns) for 2. layer -> just try it out

  * [[2000, 30000]](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/F13%20Muon%20Lifetime/FitFuncF.pdf)
  * [[1000, 30000]](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/F13%20Muon%20Lifetime/FitFuncF2.pdf)
  * [[500, 30000]](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/F13%20Muon%20Lifetime/FitFuncF3.pdf)

#### Determining the lifetime

**now use [Lebensdauer.C](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/F13%20Muon%20Lifetime/Lebensdauer.C)** 

- Questions for histograms:

  - Where can you ﬁnd similarities in the decays in diﬀerent layers? -> 
  - Are there histograms particularly diﬀerent from other histograms? -> 
  - How do the after-pulses aﬀect the spectra? What are the consequences for your next step? -> increases offsets, the offsets are "removed" after we subtract after-pulses from other spectra

  - **TODO**: Why is the speciﬁc ineﬃciency factor necessary when calculating the number of start patterns for after-pulses in downward decays? Remember that after-pulses occur only if the scintillator was passed by a muon previously. -> 

  - After subtracting the after-pulses using our scaling factors. How does the appearance of the spectra change? ->  the records for decays with long times are approximately zero, whereas without scaling factors the background remains ~10. 

  - Plot both the scaled and the unscaled histogram in order to understand the contribution and intensity of the after-pulses. 

    Decide which spectra and layers to use for the rest of the analysis in order to ﬁt the lifetime.

- Fit using function $N(t)=N(\mu)e^{-t/\tau_0}+N_{BG}$ , set initial value and range of fit parameters 

   [FitObenUntenMitScaling](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/F13%20Muon%20Lifetime/FitObenUntenMitScaling.pdf): $\tau_0^{oben} = 2184 \pm 39, N_{BG} =9\pm 1$, $\tau_0^{unten}=1879\pm34, N_{BG}=57.3 \pm 0.8 $ 
  
   [LebensDauerFitMitScaling](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/F13%20Muon%20Lifetime/LebensDauerFitMitScaling.pdf), $\tau_0=2092\pm29, N_{BG}=67 \pm 1 $ 
  
  **Literature value: $\tau = 2196.9803(22)$ ns **
  
[FitObenUntenOhneScaling](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/F13%20Muon%20Lifetime/FitObenUntenOhneScaling.pdf):  $\tau_0^{oben} = 2348 \pm 12, N_{BG} =84\pm 1$, $\tau_0^{unten}=1959\pm27, N_{BG}=62.8 \pm 0.8 $ 
  
   [LebensDauerFitOhneScaling](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/F13%20Muon%20Lifetime/LebensDauerFitOhneScaling.pdf) $\tau_0=2267\pm11, N_{BG}=153 \pm 1 $ 
  
```c++
  // par[0] background level: (1.1 +- 0.8)
  // par[1] number of muons: (1.44 +- 0.12)e3
  // par[2] muon lifetime: (2.23 +- 0.10)
  par[1] * Exp(-x[0] / par[2])) + par[0]
  ```
  
  - What appears to be useful? 
  - At what time the capture of negative muons gives no contribution to the spectrum anymore? 
  - What does this tell you for your ﬁt?
  

#### Advanced method for lifetime determination

**now use [Einfangzeiten.C](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/F13%20Muon%20Lifetime/Einfangzeiten.C)** fit using function $N(t)=N(\mu_+)e^{-t/\tau_0}(\frac{1}{f}e^{-t/\tau_c}+1)+N_{BG}$  where $f = \frac{N(\mu_+)}{N(\mu_-)}$ Since the measured decay spectra include both contributions from the decay of free muons and muons which were captured by atoms. In addition to the lifetime of the muons, you can also measure from the same data also the much shorter lifetime of the negative muons, being captured by the nuclei of the aluminium or copper, the so called *capturing time*. This is about 880 ns for aluminium.

* Check the results of the ﬁt and in particular compare the results for the decays upwards and downwards. Discuss which of the parameters should be similar for both decay spectra and in which parameters it is possible to have diﬀerences. Does the result match your expectations?

  -> 

* Determination of the systematic errors of the lifetime

  * influence of the fit range

  * Inaccuracy of the correction for the after-pulses (vary the correction factors for the after-pulses )

  * Inﬂuence of the ratio f ($\pm 1 \sigma, \pm 2 \sigma$)

    In the relevant experiments for this energy range, the ratio was determined to be $f \approx 1.275 \pm0.05$. One can specify this measured value for the ratio when making the ﬁt

  [Fit parameters](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/F13%20Muon%20Lifetime/Lebensdauer.ods), plot results(closest lifetime fit: 13): Zerfall "1Both, ... [13Both](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/F13%20Muon%20Lifetime/13Both.pdf)" Lebensdauer "1All, ... [13All](https://github.com/anananlyjlyj/physics-FP-Uni-HD/blob/master/F13%20Muon%20Lifetime/13All.pdf)". (NOTE: 13th fit of capturing time is ok, $\tau_c^{oben}=976.4 \pm 123.9$ ns, $\tau_c^{unten}=1070 \pm 183.5$, together: $976.7 \pm 103.9$ ns. 

  13th fit: $\tau_0^{oben} = 2218 \pm 47$, $\tau_0^{unten} = 2106 \pm 41$, $\tau_0^{both}= 2176 \pm 36, N_{BG} = 65 \pm 1$ 

  **Literature value: $\tau = 2196.9803(22)$ ns **)
  
  Best fit probability: 2 & 4 with free $f < 1$
  
  Best $\tau_c$ -> 4
  
  TODO: how to estimate the bias arising from the ﬁt ranges and combine all diﬀerent systematic uncertainties

### 6. Polarization measurement

Why are the muons polarised?

To determine the polarisation you have to compare the measurement with and without the magnetic ﬁeld (including the scaling factor correction). 

**now use Asymmetrie.C** 

* The asymmetry function $\frac{Z^{without}(t) - Z^{with}(t)\cdot s}{Z^{without}(t) + Z^{with}(t) \cdot s} = \frac{P\cdot A}{2} \cos{(\omega_{Larmor} t + \phi)} + c$ . Now one must consider that the duration of the measurements with and without the magnetic ﬁeld is diﬀerent and therefore the number of entries in the histograms are diﬀerent. To do so, one has to scale in the subtraction or addition the number of entries in the histogram with the magnetic ﬁeld by using the scaling-factor $s = \frac{Z_0^{without}}{Z_0^{with}}$ (derived from the integrals of the respective (with and without B) histograms listed there.)  Note that the asymmetry functions for the decays
  upwards and downwards decays are determined separately, and hence also the scaling factor for both asymmetry functions has to be determined separately.

  Scaling factor for correction see table before.

* Now look at the data from each layer. Do they diﬀer from those without a magnetic ﬁeld? Choose again the best data set. Compare again the results for the decays downwards and upwards. Which of them seems to have less systematic problems? Try also to vary the initial values of the parameters until the ﬁt function describes well the data. Test also how much the ﬁt result depends on the ﬁt range. 

* Fit function 

  `par[0] + par[1]/2.0 * TMath::Cos(x[0] * par[2] + par[3])`

  Questions:

  * What values do you expect for the parameters? 

    *  $par[1] = P\cdot A \in [0.076, 0.124]$ for pions as primary particles polarisation $P = 0.33$, for kaons $P=0.54$. 
    * The magnetic field $B = I \cdot 2.0 \cdot 10^{-4}$. For a current $20$ A, the magnetic field $B = 4$ mT. Larmor frequency $par[2]=\omega_L = \frac{eB}{m_{\mu} 10^9} =0.0003402(1/ns)$ where from the calculator $m_{\mu} \approx 1.8833\cdot10^{-28}$ kg. At the end of our measurement we have current $19.4$ A, the magnetic field $B = 3.88$ mT.  $par[2]=\omega_L =0.0003300(1/ns)$ 
    * par[3], par[0] are not further discussed for the fit

  * Are the expected values close to those calculated by the program? -> **TODO**

  * Which parameter shows the parity violation in the weak interaction? -> $par[1]=P\cdot A$

  * Calculate the magnetic moment of the muon from the measured Larmor frequency. -> $\mu^{Bohr}_{\mu} = \frac{\omega_L \hbar}{gB} $ where $g=−2.0023318418(13)$(Wiki) is gyromagnetic factor.

  * Discuss the results critically. In particular, think about whether your measurements show signiﬁcant polarisation of the cosmic muons. How can you show this quantitatively?
    
    -> **TODO**

**TODO: now use AccumulatedAsymmetrie.C** to measure the polarisation with an increased data set (with a
higher statistics, combine our dataset with those of other groups)



Discussion points:

- Done: Gelegentlich laufen Fitparameter an die Grenze des erlaubten Bereichs 
(bspw. der Parameter für den Untergrund ist eine runde Zahl und hat eine 
sehr kleine Unsicherheit). Das verzerrt auch die anderen Ergebnisse aus 
dem Fit. Wenn das passiert, sollte man die erlaubten Bereiche für die 
Parameter im Fitskript so anpassen, dass ihre Intervallgrenze mehrere 
Standardabweichungen vom besten Wert für den Parameter entfernt ist, und 
den Fit wiederholen.
- **TODO:** checkt am besten noch mal, ob ihr sowohl bei der verbesserten 
Lebensdauermessung als auch bei der **Polarisationsmessung** den 
systematischen Fehler bestimmt, der sich durch die Wahl der Fitrange 
ergibt. Dafür kann man bspw die obere und untere Fitgrenze separat um 
+-20 % (oder eben so viel variation wie noch zu einem akzeptablen wert 
für die fit-wahrscheinlichkeit führt) variieren und bestimmen, wie stark 
sich die interessanten Parameter (Lebensdauer, P*A, Frequenz) dadurch 
ändern.
- checkt auch, ob die fits bei zerfällen nach oben durchgehend 
schlechter sind als bei denen nach unten. Das deutet dann auf eine 
nicht-optimale nachpulskorrektur hin. Es kann dann sinnvoll sein, nur 
die Ergebnisse aus Zerfällen nach unten zu betrachten für ein gutes Ergebnis
- TODO: (Concerning $\Phi$: think about with which polarisation the muons are created and with which polarisation they reach the Earth’s surface).



## 7. Leftover

* number of expected muon decays in the time range > 10 $\mu$ s: ~$e^{-5}\approx1\%$, thus for periods over the time scale a lot of background is observed, it can be a typical characteristic time
* Fermi coupling constant: $G_F^2 = \frac{192 \cdot \pi^3 \cdot \hbar}{\tau_0\cdot (m_\mu \cdot c^2)^5} = 2.08\cdot 10^{29} \frac{1}{J^4}$ for $\tau=2176$ ns. $G_F^2 =2.06\cdot 10^{29} J^{-4}$ for literature value.
* From the spin of the muon you can determine the magnetic moment precession. What is the original spin-direction with respect to the moving direction of the muons?
* Determine the polarisation of cosmic muons. Which conclusions can be drawn about the genesis of cosmic muons?