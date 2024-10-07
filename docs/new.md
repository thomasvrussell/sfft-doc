## 2024
- <small>[Lei, Jan 9, 2024]</small> New release ``sfft v1.4.2+`` that can support Python 3.10! 

## 2023
- <small>[Lei, Dec 4, 2023]</small> New tutorial jupyter notebooks are available now, find them in test directories! 

## 2022
- <small>[Lei, Nov 9, 2022]</small> A warning for users: As scikit-image has changed something in its function of hough detection since version 0.19.0, I recently found that the source selection in sfft will be affected by this upgrade. For the time being I would recommend users to install ``0.16.2 <= scikit-image <= 0.18.3``. I may add a constrain on scikit-image version in sfft 1.3.5. 

- <small>[Lei, Oct 25, 2022]</small> A warning message about the usage of ``sfft.MultiEasySparsePacket`` and ``sfft.MultiEasyCrowdedPacket`` is added in the related test scripts. 

- <small>[Lei, Aug 19, 2022]</small> The preprocessing in sparse-flavor-sfft is refined using an additional rejection of mild varaibles since version 1.3.0. 

- <small>[Lei, May 24, 2022]</small> The sfft is now optimized for multiple tasks since version 1.1.0. 

- <small>[Lei, May 24, 2022]</small> A few argument-names have been changed since version ``sfft v1.1.0``, please see the test scripts. 

- <small>[Lei, May 24, 2022]</small> Locking file is removed since ``sfft v1.1.0``, as I found it unreliable in our tests, i.e., -GLockFile is removed. 

- <small>[Lei, May 24, 2022]</small> The trial subtraction for refinement is removed since ``sfft v1.1.0``. However, I add a post-subtraction check to search anomalies on the difference image using the same logic. One can feed the coordinates of the anomalies to sfft again as Prior-Banned sources to refine the subtraction (see ``-XY_PriorBan`` in ``sfft.MultiEasySparsePacket``). 