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
- 
