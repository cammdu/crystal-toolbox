# meerkat 
- meerkat performs reciprocal space reconstruction based on the orientation matrix provided by xds. 
- meerkat requires XPARM.XDS from xds as well as the cbf image dataset. 
1. In a new python file, import reconstruct_data:
```
from meerkat import reconstruct data
```
3. The reconstruction can be ran by using the script bellow, written by Arkadiy Simonov (slightly adapted):
```
#reconstruct dataset
reconstruct_data(filename_template='../frames/file_name_%05i.cbf',
        first_image=1,
        last_image=XXXX,
        reconstruct_in_orthonormal_basis=False,
        maxind=[4,5,16], #the reconstruction will be made for h=-4...4, k=-5...5, l=-16...16
        number_of_pixels=[801, 801, 801], #The resulting size of the array. Controls the step size
        polarization_factor=0.5,
        path_to_XPARM='/home/arkadiy/work/data/PdCPTN01002/xds',
        output_filename='reconstruction.h5',
        all_in_memory=True, #change to false if memory does not allow
        size_of_cache=100,
        override=True)
```
- where XXXX is the last image number (usually 3600 if 360 degrees were measured)
