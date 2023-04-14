# Integration 
## make sure you have followed peaks.md before starting. 
###### Adapted from [Erice-2022](https://github.com/ando-lab/erice-2022-data-reduction/blob/main/4_mdx2_integration.ipynb)

1. Firstly, you need to decide how to split up reciprocal space into voxels. 
- note that voxels are just 3 dimensional pixels. 
- Similarly to count thresholds and sigma cutoffs, voxels are very specific to your dataset. 
- you can divide in any subsections, but be aware that as you separate into more voxels, the processing time will increase and it will take up considerably more memory. 
```
mdx2.integrate geometry.nxs data.nxs --mask mask.nxs --subdivide X X X
```
- where X is a subsection, 1 is the default (very manageable for a computer and fairly fast running time), and 10 is a very refined option but will take much longer. 

2. To produce an hkl table after integration:
- this step is not necessary but highly recommended to view if your exposure times are non-zero. If they are zero, then you will encounter a divide by zero error when correcting the integration as the intensity is calculated by using the count rate. 
The table can be produced as follows:
- import the necessary packages:
```
# for loading mdx2 objects in python
from mdx2.utils import loadobj

# for calculations and tables
import numpy as np
import pandas as pd
```
- make your table:
```
# make a table variable using loadobj
table = loadobj('integrated.nxs','hkl_table')

# convert to pandas dataframe
df = tab.to_frame().set_index(['h','k','l'])

# show the first couple rows
df.head()
```
- check that the column labelled **seconds** has non zero values. It is okay if the starting entry is 0. 

## Corrections
- the mdx2 correct function is able to correct for many attributes including polarisation abd efficiency. It can be used as follows:
```
mdx2.correct geometry.nxs integrated.nxs
```
- similarly to above, you should output a table demonstrating the intensities present in your data to check that they are not infinite or NaN. 
```
# make a table mdx2 object
table2 = loadobj('corrected.nxs','hkl_table')

# convert to pandas DataFrame
df = tab.to_frame().set_index(['h','k','l','op','n']).sort_index()

# show the first few rows
df.head()
```
- this table will also include other columns, including the intensity error, scattering vector magnitude (s), reciprocal space volume (rs_volume) and the index of symmetry operator (op). 
- [Erice-2022](https://github.com/ando-lab/erice-2022-data-reduction/blob/main/4_mdx2_integration.ipynb) demonstrates additional correction histograms and plots. 
