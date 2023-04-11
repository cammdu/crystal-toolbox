# Viewing the Geometry of your Experiment in NeXpy
## Adapted from the mdx2 tutorials of the erice 2022 data reduction workshop
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
To view the contents of this file, mdx2 has a quick view option. 
