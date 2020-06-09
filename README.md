  
[![Build Status](https://travis-ci.org/mjirik/vebase.svg?branch=master)](https://travis-ci.org/mjirik/vebase)
[![Coverage Status](https://coveralls.io/repos/github/mjirik/vebase/badge.svg?branch=master)](https://coveralls.io/github/mjirik/vebase?branch=master)
[![PyPI version](https://badge.fury.io/py/vebase.svg)](http://badge.fury.io/py/vebase)


vebase

Vessel Basin Segmentation


```python
import vebase.livseg

p1 = "D:/liver_datasets_outputs/wokrin/1/MASKS_DICOM/liver/"
p2 = "D:/liver_datasets_outputs/wokrin/1/MASKS_DICOM/portalvein/"
p1_i = "D:/liver_datasets_outputs/wokrin/1/MASKS_DICOM/liver/image_1"
p2_i = "D:/liver_datasets_outputs/wokrin/1/MASKS_DICOM/liver/image_2"

# load ncsry data
l_data = vebase.livseg.load_vdata(p2,p1,p1_i,p2_i)
# build volumes
organ_seg = l_data[0]
liver_seg = l_data[1]
voxelsize = l_data[2]
cr = l_data[3]
voda_ = vebase.livseg.voda_sk(organ_seg,liver_seg,voxelsize,cr)
# choose important nodes of portal vein
#hint for segmentation params.
x = seg_hinter(temp) #temp = 2 - 1.bifurcation, temp = 4  2. bifurcation, temp > 8 more than real structure... 
tree_red = vebase.livseg.tree_reduction(voda_[0],voda_[1], voda_[2],l_data[3],1) 
#tree_red[0][-1] final segment areas
3d_seg = seg_3dnp(l_data[1],tree_red[0][-1],voda_[0],voda_[2])
```
