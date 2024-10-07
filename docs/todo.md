## 2022
- <small>[Lei, Nov 11, 2022]</small> The total GPU memory usage is only optimized for KerPolyOrder = 2 & BGPolyOrder = 2, I will extend the optimization to other cases ASAP! In fact, I believe there is ample space for reducing the total GPU usage and I will explore it. **[FINISHED]**

- <small>[Lei, Nov 11, 2022]</small> I will allows users to disable the hough detection for preprocessing when there are too few sources in the field in the next version sfft v1.3.5. 

- <small>[Lei, Nov 9, 2022]</small> Add a verbose argument for sfft so that users can get more clean printed messages. **[FINISHED]**

- <small>[Lei, Nov 9, 2022]</small> Test if we can use sep to replace SExtractor in preprocessing to make sfft more Pythonic.  

- <small>[Lei, July 6, 2022]</small> Incorporate the separate functions for spline form sfft into the unified sfft functions. Note that only Numpy backend is currently available and the spline form is very memory-consuming. **[FINISHED]**

- <small>[Lei, May 24, 2022]</small> Write a detailed documentation for sfft! **[FINISHED]**

- <small>[Lei, May 24, 2022]</small> We notice that SExtractor may have been called to perform astrometric calibration before image subtraction. It is definitely not wise to run SExtractor again in sfft, I need to develop a module which allows users to feed SExtractor products as inputs of sfft, which will significantly reduce the preprocessing time in sfft. 

- <small>[Lei, May 24, 2022]</small> The multiprocessing mode is expected to accomondate multiple GPU devices, however, the function has not tested on such a multi-GPUs platform. **[FINISHED]**

- <small>[Lei, May 20, 2022]</small> Add a function for optimizing sfft on a given computing platform with multiple CPU threading and one/multiple GPU card(s). This would be very useful to reduce the overall time cost when users have a large set of image-pairs to be processed simultaneously. **[FINISHED]**
