# Processing Image Data
## Before starting this tutorial make sure you have geometry.nxs
### Preliminary 
To process data in mdx2, the data can be sliced to increase processing speed. If you aim to process the 360 degrees, skip this step.  Choose an image range that is suitable for you (has to fit properly into your dataset). 
```
dials.slice_sequence refined.expt "image_range=X Y"
```
- where X is your lower limit frame and Y is your upper limit frame. This can be any range that is suitable for your data set. 
- If your dataset is 360 degrees, subsets of 50 degrees work well, e.g.:
```
dials.slice_sequence refined.expt "image_range=100 600"
```
- this will output refined_100_600.expt and save it in the previously designated directory. 

### Processing in mdx2
1. In an IDE or in python on the terminal:
```
from nexusformat.nexus import nxload
```
2. Proceed with importing your data:
```
mdx2.import_data refined.expt --chunks X Y Z
```
- where X,Y and Z are parameters for the chunks in which you read data. Smaller chunks are great as they increase processing efficiency. 
- this will output data.nxs

3. To visualise your data, open data.nxs in NeXpy by running
```
nexpy
```
in your terminal. 
- In NeXpy find: **open --> data.nxs**
- please note that data.nxs is a very large file (>3gb). Therefore it is recommended that inspecting data.nxs is only done on a device with adequate space.

4. It is possible to inspect whether there is any diffuse scattering available in your data using **data.nxs** 
- You can use matplotlib to plot a strong peak (not a hot pixel).  
// tutorial not finished yet
