## AWS Redshift Connections

> Read or writing in redshift requires temporary directory.(S3)

## Read Data 

`options = {  
     "url": "jdbc:redshift://host:port/redshift database name",
     "dbtable": "redshift table name",
     "user": "username",
     "password": "password",
     "redshiftTmpDir": args["TempDir"]
 }`
 
`df = glueContext.create_dynamic_frame_from_options("redshift", options)`

### Options

| Key | Description|
|:----|:----------|
| url | It should include driver, db type, url, port ,db name.|
| dbtable | Redshift Table name, which is mandatory.|
| user | Redshift Username.|
| password | Redshift Password.|
| redshiftTmpDir | Temporary location in s3 bucket.|
| aws_iam_role | Not Mandatory as we provide it while creating jobs.|


## Write Data

`options = {
     "dbtable": "redshift table name",
     "database": "redshift database name",
     "aws_iam_role": "arn:aws:iam::account id:role/role name"
     "preactions":"DROP TABLE master"
 }`

`glueContext.write_dynamic_frame.from_jdbc_conf(
     frame = df, 
     catalog_connection = "connection name", 
     connection_options = options, 
     redshift_tmp_dir = args["TempDir"])`
     
    
- frame: dynamic frame name.
- catalog connection: redshift connection name, if we already created one in Catalog section.
- connection_options: db connection options

You can use below method to write data, if you dont have any predefined connections in Catalog section.
`glueContext.write_dynamic_frame.from_options(frame=data,connection_type="redshift",connection_options=options)`

### Options

| Key | Description|
|:----|:----------|
| url | It should include driver, db type, url, port ,db name.|
| dbtable | Redshift Table name, which is mandatory.|
| user | Redshift Username.|
| password | Redshift Password.|
| redshiftTmpDir | Temporary location in s3 bucket.|
| aws_iam_role | Not Mandatory as we provide it while creating jobs.|


### Writing data with custom encryption key.

`glueContext.create_dynamic_frame.from_catalog(
       database = "database-name", 
       table_name = "table-name", 
       redshift_tmp_dir = args["TempDir"],
       additional_options = {"extraunloadoptions":"ENCRYPTED KMS_KEY_ID 'CMK key ID'"}, 
       transformation_ctx = "datasource0"
     )`
     
 You can pass custom encryption key as 'extraunloadoptions'.


