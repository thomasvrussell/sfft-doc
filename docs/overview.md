## About SFFT

[SFFT Speed]: assets/images/sfft_subtract_speed.png
[SFFT Characteristics]: assets/images/sfft_features.png

[DESIRT]: https://ui.adsabs.harvard.edu/abs/2022TNSAN.107....1P/abstract
[AR 5965]: https://www.stsci.edu/jwst/science-execution/program-information?id=5965>
[Roman Supernova PIT]: https://github.com/Roman-Supernova-PIT

Saccadic Fast Fourier Transform (SFFT) is an algorithm for astronomical image subtraction in Fourier space (Hu et al., 2022). SFFT brings about a remarkable improvement of computational performance of <span style="color: #EE3277;">**an order of magnitude**</span> compared to other published image subtraction codes.

[![SFFT Speed]][SFFT Speed]

SFFT method is the transient detection engine for several ongoing time-domain programs, including the [DESIRT] survey based on DECam & DESI, the DECam GW-MMADS Survey for GW Follow-ups and the JWST Cycle 3 Archival program [AR 5965]. SFFT is also the core engine for the differential photometry pipeline of the [Roman Supernova PIT].

## SFFT vs. Others

To get a clear picture of our method, we summarize a variety of features from different perspectives for SFFT and other existing image subtraction methods:

[![SFFT Characteristics]][SFFT Characteristics]

!!! Remarks

    The table above only reflects the status of the SFFT method at the time of its initial publication in 2022. In Hu et al. (2024), we introduced **kernel regularization** into SFFT and implemented it in our software. 
    
    Additionally, to leverage the advantages of the ZOGY approach, we extended the SFFT method to be **fully compatible with ZOGY's** statistically closed-form framework. This hybrid method retains the general workflow of ZOGY while incorporating image-matching refinements using the SFFT code. This adaptation makes SFFT an optimal subtraction engine for space telescopes, such as JWST/NIRCam and Roman.

## Publications using SFFT

See ADS Library: https://ui.adsabs.harvard.edu/public-libraries/lc4tiTR_T--92f9k0YrRQg