[SFFT Github Issues]: https://github.com/thomasvrussell/sfft/issues
!!! Tip
    Please report bugs on Github: [SFFT Github Issues]

## Installation issues
!!! Issue
    If your Python environment already has some version of ``llvmlite`` (a package required by NumPy backend) before installing sfft. Sometimes the ``setup.py`` in sfft cannot properly update llvmlite to the desired version, then you may get errors related to ``Numba`` or ``llvmlite``. You can manually install llvmlite by:
    ```
    pip install llvmlite==0.36.0 --ignore-installed
    ```
