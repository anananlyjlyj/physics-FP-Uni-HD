# F30 Stellar CCD Photometry

- [F30 instruction](http://www.kip.uni-heidelberg.de/fp-computer/fp75/fp30.pdf)

- Literature: 

  [STSci](http://www.stsci.edu/)

  [Qucam](http://www.qucam.com/ccd.html)

  [presentation](http://www2.mpia.de/AO/INSTRUMENTS/FPRAKT/All_about_CCDs_by_Simon_Tulloch.pdf)

- [Protocol]

  [Ezpadova](https://github.com/mfouesneau/ezpadova)

- Evaluation:

  use package [Astropy](http://www.astropy.org/)

## Part A: 

### 

## Part B: Star Clusters data analysis

### Zeropoint calibration

V: 25.15702

I: 25.14337

### PSF photometry with STARFINDER

#### Determination of Noise

I: Mode = -0.000303037, StdDev = 0.00967375

V: Mode = -0.000221867, StdDev = 0.0119044

### Astrometry and Photometry

Detection threshold, Correlation threshold

V: Correlation threshold = 0.4, found stars = 53900/2 = 26950

V: Correlation threshold = 0.3, found stars = 54608/2 = 27304 (with arithmetic error: floating underflow, floating overflow, floating illegal operand )

I: Correlation threshold = 0.4, found stars = 49770

combine stars = 23690



## Reference list

### Color Magnitude Diagram

https://arxiv.org/pdf/0704.2942.pdf

https://acszeropoints.stsci.edu/

http://www.stsci.edu/cgi-bin/get-visit-status?id=10248&markupFormat=html&observatory=HST

http://www.stsci.edu/hst/acs/analysis/zeropoints

[stellar isochrones and their derivatives](http://stev.oapd.inaf.it/cgi-bin/cmd)

### CCD files analysis

[python ccdproc example reduction](https://nbviewer.jupyter.org/gist/mwcraig/06060d789cc298bbb08e)



