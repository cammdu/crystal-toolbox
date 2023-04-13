# How to use DIALS 
## Before continuing with this tutorial, make sure DIALS is properly installed (into a python 3.10 environment).
- [DIALS](https://dials.github.io/index.html) (Diffraction Integration for Advanced Light Sources) is diffraction software developed to analyse x-ray diffraction data. DIALS is a very useful tool run via the command line and is heavily documented. 
- DIALS comes with its own GUI which is installed intrinsically when DIALS is installed. 
- If possible, run this operation in the same directory as the images, if not possible, add the path. 
- To check whether DIALS is properly installed run:
```
dials.version
```
This should print the current version. 

1. Import the folder containing the cbf images (in pre_processed) using:
```
dials.import_xds 'xds_folder_name'
```
- This should output xds_models.expt

2. To have a look at the unprocessed data:
```
dials.show xds_models.expt
dials.image_viewer xds_models.expt 
```
3. If you are interested to see how the data looks in reciprocal space without processing, you can use:
```
dials.reciprocal_space_viewer xds_models.expt
```
4. For peak detection, either before or after making a mask, use:
```
dials.find_spots xds_models.expt 
```
which will output the strong reflections (strong.refl)
5. To assign a Miller index to every found spot, use the index function:
```
dials.index xds_models.expt strong.refl 
```
- this will output a table providing unit cell parameters, show the percentage of indexed peaks and other useful information. 
- To be rigorous, make sure that the output here provides similar parameters to xds. 
- output files are: indexed.expt and indexed.refl 

6. If needed, DIALS has a refine function which can improve spot predictions, and can be ran as:
```
dials.refine indexed.expt indexed.refl 
```
7. An excellent feature of DIALS is the report html it can produce. This report contains many charts and summarises information from the previous steps.
dials.report refined.expt refined.refl

Note that DIALS can perform many more tasks and is not restricted to these commands. 
