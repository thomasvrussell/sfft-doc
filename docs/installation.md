# Installation

<!-- ### with pip <small>recommended</small> { #with-pip data-toc-label="with pip" } -->
## SFFT Installation
[PyPI]: https://pypi.org/project/sfft/
To install the latest stable version of sfft from [PyPI]: <small>[recommended]</small>
=== "Latest"

    ``` sh
    pip install sfft
    ```

[GitHub]: https://github.com/thomasvrussell/sfft
One can also install sfft from [GitHub]:
```
git clone https://github.com/thomasvrussell/sfft.git
```
```
python setup.py install
```
Both will automatically install compatible versions of python dependencies.

!!! tip

    PyPI/GitHub installation does not include the setup of GPU backend.

## Enable GPU backend

[CuPy]: https://cupy.dev
SFFT method supports both CPU backend and GPU backend. To enable the GPU backend, users need to further install [CuPy] according to their CUDA version. Note this backend requires GPU device(s) with double-precision support.

- CUDA 12: e.g., enable the CuPy backend for CUDA 12.0 via
```
pip install cupy-cuda12x
```

- CUDA 11: e.g., enable the CuPy backend for CUDA 11.5 via
```
pip install cupy-cuda115
```

- CUDA 10: e.g., enable the CuPy backend for CUDA 10.1 via
```
pip install cupy-cuda101
```

!!! Remarks

    There was a PyCUDA backend in sfft but now deprecated since v1.4.0. For sfft < v1.4.0, PyCUDA backend was preserved as it consumes less GPU memory. However, the CuPy backend is now better implemented for GPU memory allocation, making the PyCUDA backend no longer useful.

## AstrOmatic Dependencies

You need further to install additional AstrOmatic software for sfft.
[SExtractor]: https://github.com/astromatic/sextractor
[SWarp]: https://github.com/astromatic/swarp
[AstrOmatic]: https://www.astromatic.net/software

- [SExtractor]: SExtractor from [AstrOmatic] is required for SFFT preprocessing, as it allows SFFT to determine an appropriate pixel mask for the input image pair before performing image subtraction. This step is critical for achieving more accurate parameter solutions.
```
conda install -c conda-forge astromatic-source-extractor
```

    !!! tip

        We have wrapped SExtractor into a Python module, ``sfft.utils.pyAstroMatic.PYSEx``, enabling users to trigger SExtractor directly within Python. Use ``help(sfft.utils.pyAstroMatic.PYSEx)`` for more details.

- [SWarp] (optional): SWarp from [AstrOmatic] is not required for sfft subtraction itself. However, it is normally useful to align the input image-pair before image subtraction by SWarp.
```
conda install -c conda-forge astromatic-swarp
```

    !!! tip

        We have additionally wrapped SWarp into a Python module ``sfft.utils.pyAstroMatic.PYSWarp`` so that you can align images in a more Pythonic way. Use ``help(sfft.utils.pyAstroMatic.PYSWarp)`` for more details.
