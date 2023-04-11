# Processing Image Data
## Before starting this tutorial make sure you have geometry.nxs and follow the preliminary steps.
### Preliminary 
To process data in mdx2, the data has to be sliced as mdx2 cannot process 360 degrees in one go. Choose an image range that is suitable for you. 
```
dials.slice_sequence refined.expt "image_range=X Y"
```
- where X is your lower limit frame and Y is your upper limit frame. This can be any range that is suitable for your data set. 
- If your dataset is 360 degrees, subsets of 50 degrees work well, e.g.:
```
dials.slice_sequence refined.expt "image_range=100 600"
```
- this will output refined_100_600.expt

### Processing in mdx2
1. In an IDE or in python on the terminal:
```
from nexusformat.nexus import nxload
```
2. Imp
