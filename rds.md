## AWS RDS Connections
AWS Glue can connect to the following data stores through a JDBC connection:

- PostgreSQL
- MySQL
- Aurora
- Oracle 
- Microsoft SQL Server


## READ

We use  'create_dynamic_frame_from_options' for reading data from rds, which is same as redshift. The main difference to notice is, we are providing db driver name.

`glueContext.create_dynamic_frame_from_options('postgresql', { 'url': "db url", 'dbtable': "table name", 'user':"db user name", 'password': "db password"})`

### Options

| Key | Description|
|:----|:----------|
| url | It should include driver, db type, url, port ,db name.|
| dbtable | DB Table name, which is mandatory.|
| user | DB Username.|
| password | DB Password.|
| redshiftTmpDir | Temporary location in s3 bucket.|
| aws_iam_role | Not Mandatory as we provide it while creating jobs.|

## Write

Similarly, we use 'write_dynamic_frame' class to write data to rds.
 
`glueContext.write_dynamic_frame_from_options(frame=df,connection_type='postgresql',connection_options={ 'url': "db url", 'dbtable': "table name", 'user': "db user name", 'password': 'bCF5d0H8QCutVH80CuJo','postactions':"db password"})`

### Options

| Key | Description|
|:----|:----------|
| url | It should include driver, db type, url, port ,db name.|
| dbtable | Redshift Table name, which is mandatory.|
| user | DB Username.|
| password | DB Password.|
| redshiftTmpDir | Temporary location in s3 bucket.|
| aws_iam_role | Not Mandatory as we provide it while creating jobs.|
