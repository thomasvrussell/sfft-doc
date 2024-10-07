# Q & A

## Which image is convolved?

!!! Answer
    There is a universal argument named ``-ForceConv`` to control the direction of image subtraction, which works on all image subtraction modules in sfft.

    - ``-ForceConv = AUTO`` means sfft will determine the direction of image subtraction automatically according to the estimated FWHM of reference image and science image. The image which has smaller FWHM will be convolved in the image subtraction to avoid deconvolution. After comparing the FWHM, ``AUTO`` actually becomes either ``REF`` or ``SCI`` (see below). 
    
        One can get to know which image is eventually convolved in image subtraction from the primary header of the output difference image (see the FITS keyword ``CONVD``). This mode does not supported in the Customized module ``sfft.CustomizedPacket``.

    - ``-ForceConv = REF`` means sfft will convolve the reference image and DIFF = SCI - Convolved_REF. As a result, the psf and flux zero-point of difference image is consistent with the unconvolved image, i.e., the science image.

    - ``-ForceConv = SCI`` means sfft will convolve the reference image and DIFF = Convolved_SCI - REF. Consequently, the psf and flux zero-point of difference image is consistent with the unconvolved image, i.e., the reference image.

    One can perform PSF / Aperture photometry on the transients on difference image as if it is an object living in the science (reference) image when ``REF`` (``SCI``) is convolved: using the same psf model / aperture and magnitude zeropoint.

    With our convention, a transient on science image is always a positive signal on difference image whatever ``-ForceConv`` is.

## Backward compatiablity?

!!! Answer
    We have tried our best to ensure the backward compatiablity, however, the rule was sometimes overrided in the development of sfft, e.g., some arguments might be deprecated in higher version of sfft. Users might get errors when they use old scripts but update sfft to a higher version. To solve the problem, I have been maintaining the test scripts on Github to make sure they can always work for the lastest version of sfft. You can also find the change log of arguments in the test scripts. 
