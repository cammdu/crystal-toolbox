# Viewing the Geometry of your Experiment in NeXpy
## Adapted from the mdx2 tutorials of the erice 2022 data reduction workshop (link to page)
### To run this tutorial, make sure you have produced 'refined.expt' from the How_to_DIALS.md tutorial. 

- mdx2 is a powerful tool used to process x-ray diffraction data and is used in parallel with DIALS.
- NeXpy is the graphical user interface of mdx2 and allows the user to view geometry factors such as solid angle as well as generated reciprocal space plots etc.
Run the following in your terminal in the directory where you want your output files located:

To open NeXpy, run:
```
nexpy
```
This should open an app. 

Import the following dependencies:
```
import numpy as np

import matplotlib.pyplot as plt

import pandas as pd

from mdx2.utils import loadobj #important for loading nexus format files
```

To convert the geometry from DIALS to mdx2, refined.expt should be imported and converted to nexus format:
```
mdx2.import_geometry refined.expt
```
- this will output a geometry.nxs file. 
To view the contents of this file, mdx2 has a quick view option of the tree structure (see h5_to_nexus tutorial)
```
mdx2.tree geometry.nxs
```
- this will show a list of information in your terminal, including symmetry information and metadata. 
- this is a good point to check whether the assigned symmetry and Laue/ Space group is what you expect.

There are two ways to view geometry.nxs:
In NeXpy:
- Click **open** and then choose geometry.nxs. 
- open entry
- open corrections
- double click the plot you would like to see

In Python:
```
corrections = loadobj('geometry.nxs','corrections')
ax = plt.imshow(corrections.CHOOSE_YOUR_PLOT,extent=[0,1,1,0])
```
- where the extent is the orientation of your image
- where CHOOSE_YOUR_PLOT can be efficiency, solid angle or any other plot
- try to get familiar with the different geometry plots and see if they properly represent your data. 
 
#### Troubleshoot note:
Check if your efficiency is >0. If this is not true, then set your efficiency to the correct value in **import_geometry.py**. The value should be between 0 and 1, where 1 is a very high efficiency for a detector and 0 is low. 
