---
title: GDAL crashes python
date: 2015-10-13 09:16:00
categories:
- Programming

tags:
- python



---

### GDAL crashes Python
```
>>> from osgeo import gdal
>>> dataset = gdal.Open('C:\\RandomData.img')
>>> band = dataset.GetRasterBand(1)
>>> del dataset           # This will cause the Python garbage collector to deallocate dataset
>>> band.GetChecksum()    # This will now crash Python because the band's dataset is gone
< Python crashes >
```

```
>>> from osgeo import gdal
>>> print gdal.Open('C:\\RandomData.img').GetRasterBand(1).Checksum()
< Python crashes >
```
In the above example, the dataset is no longer needed after the call to GetRasterBand so Python deallocated it before calling Checksum.  
The GDAL and OGR objects are implemented in C++ and the relationships between them are maintained in C++ using pointers.When you delete the dataset instance in Python it causes the C++ object behind it to be deallocated. But the C++ object behind the band instance does not know that this happened, so it contains a pointer to the C++ dataset object that no longer exists. When the band tries to access the non-existing object, the process crashes.

The problem is not restricted to the GDAL band and dataset objects. It happens in other areas where objects have relationships with each other. Unfortunately there is no complete list, so you have to watch for it yourself. One other known place involves the OGR GetGeometryRef() function:
```
>>> feat = lyr.GetNextFeature()
>>> geom = feat.GetGeometryRef()     # geom contains a reference into the C++ geometry object maintained by the C++ feature object
>>> del feat                         # This deallocates the C++ feature object, and its C++ geometry
>>> print(geom.ExportToWkt())        # Crash here. The C++ geometry no longer exists
< Python crashes >
```
The functions that end in "Ref" obtain references to internal objects, rather than making new copies.The advantage of the "Ref" and "Directly" functions is they provide faster performance because a duplicate object does not need to be created. The disadvantage is that you have to watch out for this problem.  


Python crashes in GDAL functions when you upgrade or downgrade numpy.If you obtain a precompiled version of GDAL's Python bindings,be sure you look up what version of numpy was used to compile them, and install that version of numpy on your machine.


