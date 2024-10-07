# Tutorials

## Quick Start

We have provided several examples in the test directory of our GitHub repository to help you quickly get acquainted with the main functions of our software.

[Example for Sparse Field Flavor SFFT]: https://github.com/thomasvrussell/sfft/tree/master/test/subtract_test_sparse_flavor

### Sparse Field Flavor SFFT

The sparse field flavor is the most common mode. It works well when isolated sources are dominated/sufficient in the field. Get started with [Example for Sparse Field Flavor SFFT]. 

In this example, we use the module ``sfft.EasySparsePacket`` to perform image subtraction for CTIO-4m DECam observations. For more details on module usage, refer to ``help(sfft.EasySparsePacket)``.

### Crowded Field Flavor SFFT

[Example for Crowded Field Flavor SFFT]: https://github.com/thomasvrussell/sfft/tree/master/test/subtract_test_crowded_flavor
The crowded field flavor is designed for extreme cases where sources are typically highly blended in the field. Get started with [Example for Crowded Field Flavor SFFT]. 

In this example, we use the module ``sfft.EasyCrowdedPacket`` to perform image subtraction for ZTF M31 observations. For more details on module usage, refer to ``help(sfft.EasyCrowdedPacket)``.

!!! Remarks

    - The two flavors SFFT actually follow the same routine for image subtraction and differ only in ways of masking the data for kernel determination.

    - Proper image-masking is required by SFFT to identify the pixels that cannot be correctly modeled (hereafter, distraction pixels), e.g., saturated sources, casual cosmic rays and moving objects, bad CCD pixels, optical ghosts, and even the variable objects and transients themselves. The pre-subtraction processing for image-masking is referred to as **preprocessing** in sfft.

    - Our software provides a generic and robust function to perform **preprocessing** of the data, which has been extensively tested with data from various transient surveys. When you run Crowded-flavor sfft and Sparse-flavor sfft, sfft actually performs the generic **preprocessing** for image-masking and do the sfft subtraction subsequently. 

!!! Details

    More specificially, the built-in **preprocessing** in sfft consists of two steps: (I) identify the distraction pixels in the input image-pair; (II) create the masked version of the input image-pair via replacing the identified distraction pixels by proper flux values. 
    
    In Sparse-flavor sfft, we designed a source-selection based on SExtractor catalogs and identify the unselected regions as distraction pixels. Given that the input images are required to be sky-subtracted in Sparse-flavor sfft, we simply replace the distraction pixels by zeros; 
    
    In Crowded-flavor sfft, we only identify the pixels contaminated by saturated sources as distraction pixels using SExtractor, and then replace the distraction pixels by local background flux. 

### Preparations before SFFT

[Example for SFFT Preparation]: https://github.com/thomasvrussell/sfft/tree/master/test/subtract_test_sparse_flavor/prepare_data_example
[Example for Sky Subtraction]: https://github.com/thomasvrussell/sfft/blob/master/test/subtract_test_sparse_flavor/prepare_data_example/SubtractSky.py
[Example for Image Alignment]: https://github.com/thomasvrussell/sfft/blob/master/test/subtract_test_sparse_flavor/prepare_data_example/AlignImage.py

Sky subtraction is required for the Sparse Field Flavor of SFFT, while image alignment is necessary for both flavors of SFFT. SFFT provides convenient modules to assist users in performing both sky subtraction and image alignment, see [Example for SFFT preparation].

- Use SExtractor to subtract the sky background, see [Example for Sky Subtraction] using module ``sfft.utils.SExSkySubtract``. 

- Use SWarp to align reference image and science image, see [Example for Image Alignment] using module ``sfft.utils.pyAstroMatic.PYSWarp``. 

## Customized usage

[Example for Customized SFFT]: https://github.com/thomasvrussell/sfft/tree/master/test/subtract_test_customized
The customized sfft is designed to allow users to feed their own image-masking to replace the generic **preprocessing** in sfft. Get started with [Example for Customized SFFT]. 

In this example, we use the module ``sfft.CustomizedPacket`` to perform image subtraction for ZTF-M31 observations with given image mask. For more details on module usage, refer to ``help(sfft.CustomizedPacket)``.

!!! Tip
    The module focuses exclusively on the subtraction process, giving users a sense of the lightning-fast speed of SFFT subtraction on GPU devices!

!!! Tip
    If you are using GPU backends and processing a queue of observations, the first iteration of SFFT subtraction may be slow due to CuPy compilation. However, the runtime stabilizes after the initial run. As observed in the previous test, the GPU warm-up phase can be quite slow. Fortunately, this issue can be easily mitigated by running a trivial subtraction (even on simple images) beforehand, allowing the pipeline to warm up and be ready for subsequent observations.

!!! Remarks

    The built-in **preprocessing** in SFFT, based on SExtractor, is designed to provide a generic yet conservative approach that can adapt to a wide variety of imaging data. However, in contrast to the high speed of the image subtraction, the computing performance of the built-in **preprocessing** is considerably less efficient, taking roughly 10 times longer. For specific time-domain programs, we believe there is significant potential for optimizing the computing overhead associated with **preprocessing**. Below are two suggestions that may help users incorporate SFFT more efficiently into their pipeline:

    - For Sparse-flavor SFFT, the built-in **preprocessing** performs source selection based on SExtractor catalogs and then creates masked images for subsequent subtraction. To optimize the overall computational cost of the pipeline, users can leverage the SExtractor products generated in earlier stage (e.g., astrometric calibration) for source selection in SFFT. This approach is much faster than running SExtractor again, as it avoids repeated photometry and significantly reduces computing time.

    - For Crowded-flavor SFFT, the built-in **preprocessing** only masks saturation-contaminated pixels using SExtractor. However, when data quality masks are available for the observed imaging data in a survey program, users can identify invalid pixels using those masks and replace them with the local background. This allows the built-in **preprocessing** to be entirely skipped, streamlining the workflow.

We encourage users to design dedicated image-masking strategies for their survey programs to unleash the great power of sfft subtraction!
