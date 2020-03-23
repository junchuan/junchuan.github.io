---
title: Geomesa Converter
date: 2018-05-23 11:29:00
categories:
- Big Data

tags:
- big geospatial data
- spatiotemporal database
- hdfs
- geomesa


---

## Geomesa Converters
A *converter* defines the mapping between source data (CSV, JSON, XML, etc) and a *SimpleFeatureType*.  
The *converter* accepts as input source files, and outputs GeoTools SimpleFeatures, which can then be written to GeoMesa. Each *converter* corresponds to a single *SimpleFeatureType*.  

Converters are generally defined with a *type* and a *fields array*. Optionally, they may define an *id-field*, *user-data* and *configuration* options. 
- The *type* element specifies the type of the converter, for example `delimited-text` or `json`. 
- The *fields array* defines the attributes created by the converter. The `transform` of a field can be used to reference other fields or modify the raw value extracted from the source data. The `transform` element supports referencing each field in the record by its column number using `$`.  See a list of available [transform functions](https://www.geomesa.org/documentation/user/convert/function_overview.html#converter-functions).
- The *id-field* element will set the feature ID for the SimpleFeature. 



