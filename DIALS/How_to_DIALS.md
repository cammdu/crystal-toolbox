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
