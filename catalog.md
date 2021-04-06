# AWS Data Catalog

AWS Glue itself provides a database which can store data's temporarily.
We can load data into catalog with Glue Crawlers or ETL Jobs.
> glueContext.create_dynamic_from has three methods:
> from_catalog, from_jdbc_conf, from_options.
## Read Data
We just need to specify only catalog database and catalog table name under this condition.

`
 glueContext.create_dynamic_frame.from_catalog(
    database = "database-name", 
    table_name = "table-name", 
    redshift_tmp_dir = args["TempDir"], 
    additional_options = {"aws_iam_role": "arn:aws:iam::account-id:role/role-name"}) 
  `
  
 
  
 ## Write Data
 
 Similiar to read, we only need to specify catalog database and catalog table for writing.
 
`
 glueContext.write_dynamic_frame.from_catalog(
    database = "database-name", 
    table_name = "table-name", 
    redshift_tmp_dir = args["TempDir"], 
    additional_options = {"aws_iam_role": "arn:aws:iam::account-id:role/role-name"}) 
  `

