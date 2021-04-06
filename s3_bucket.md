## AWS S3 Bucket Connections

> AWS Glue supports JSON, CSV, Parquet, ORC, Avro, and Grok for read and write to S3.

Read Data
-
In AWS Glue, we can read files from S3 buckets.

`
dyf = glueContext.create_dynamic_frame.from_options("s3", {'paths': ["s3://s3path/"], 'recurse':True, 'groupFiles': 'inPartition', 'groupSize': '1048576'}, format="json")
`

Here, the data have been fetched from s3 bucket folder

`df = dyf.toDF()`

Converted Dynamic Frame to Pyspark Dataframe.

`df.show()`

| **User** | **Age** |
|:----:|:---:|
| Tim | 20 |
| Tom | 22 |
| Tiny | 25 |

### Options

| Key | Description|
|:----|:----------|
| Path | S3 location.|
| groupFiles | To group files .|
| groupSize | Define grouping size (in bytes).|
| recurse | To recursively read all files in subdirectory (boolean).|

## Write Data

We can directly convert **data frame** directly to csv and save in s3 bucket.

`df.repartition(1).write.option('header', 'true').csv('s3://s3path/')`

Or, we can convert **dynamic frame** to csv and save in s3 bucket.

`glueContext.write_dynamic_frame.from_options(frame = dyf,
           connection_type = "s3",
           connection_options = {"path": "s3://s3path/"},
           format = "csv")`



