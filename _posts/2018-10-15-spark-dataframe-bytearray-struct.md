---
title: Decode bytearray column in Spark dataframe into StructType
date: 2018-10-15 11:29:00
categories:
- notes

tags:
- tweet data
- apache spark
- apache parquet

---

## TL;DR
This post shows you how to transform ByteType column in Spark dataframe into complex StructType. 

## Problem
After running some preprocessing on streamed tweets, I stored the proprocessed results into apache parquet format. Then, somehow, parquet file automatically stores string column into bytearray. Well, it is pretty easy to cast byte array into string using `astype` function. However, it becomes tricky for colume with structured information,e.g., the bounding_box column, which contains a json string like this:
```
{
  "bounding_box": {
    u"coordinates": [
      [
        [
          -74.026675,
          40.683935
        ],
        [
          -74.026675,
          40.877483
        ],
        [
          -73.910408,
          40.877483
        ],
        [
          -73.910408,
          40.3935
        ]
      ]
    ],
    u"type": "Polygon"
  }
}
```
The ideal scenario would be that `spark.read.parquet` function can automatically recognize the structure of information in the json string. Obviously, not so fast!

## Solution
The extra `u` have to removed from the decoded result first: 
```
temp_sdf=temp_sdf.withColumn('bbox_str',temp_sdf.bounding_box.astype('string'))
temp_sdf=temp_sdf.withColumn('coords',func.regexp_replace('bbox_str','u',""))
```
Then, we have to specify the struct type manually in order to let the reader recognize the information in the json string:
```
schema = StructType([
    StructField("type", StringType(), True),
    StructField("coordinates", ArrayType(ArrayType(ArrayType(FloatType()))),
                True),
])
temp_sdf=temp_sdf.withColumn('bbox',func.from_json('coords',schema)) 

```  
Check out the [jupyter notebook] (http://nbviewer.jupyter.org/github/junchuan/ResearchProject/blob/gh-pages/jupyter_notebook/ParquetFileBinary_Note.ipynb)for this post.

