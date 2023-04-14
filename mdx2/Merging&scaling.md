# Merging and Scaling Your Dataset to Create the 3D Reconstruction
## Merging
- merging is significant to group the number of repeating observations with the same Laue group 
- to start merging use the merge function:
```
mdx2.merge corrected.nxs --outfile merged_not_scaled.nxs
```
- this will output a table, to inspect this:
```
mdx2.map geometry.nxs merged_not_scaled.nxs --limits hx hy kx ky lx ly --outfile slice_not_scaled.nxs
```
- herein you should input whichever slice you want. It is conventional to start with a slice where l=0 like so:
```
mdx2.map geometry.nxs merged_not_scaled.nxs --limits hx hy kx ky 0 0 --outfile slice_not_scaled.nxs
```
- now open **slice_not_scaled.nxs** in NeXpy to visualise it. 

## Scaling
- Mdx2 has a function called scale which runs through 5 iterations to make model to scale the data. 
- scaling is important as it essentially normalises the data. This allows your data to be compared to others. 
1. Make your model:
```
mdx2.scale corrected.nxs
```
- this will save your model to a file named **scales.nxs**
- to plot this:

```
#import packages
from mdx2.utils import loadobj

# make your object
table3 = loadobj('corrected.nxs','hkl_table')

# find the number of times every h,k,l is observed
c = tab.to_frame().groupby(['h','k','l'])['phi'].count().value_counts().sort_index()
c[c>1000].plot.bar();
```
