# Data Frame Basic Operations

##### 1) Convert Dynamic Frame to Data Frame

`DF = DYF.toDF()`
___
##### 2) Convert Data Frame to Dynamic Frame

`DYF = DynamicFrame.fromDF(DF, glueContext, 'DF')`
___
##### 3) Alias Data Frame

`DF.alias('aliasName')`
___
##### 4) Run SQL Query in Glue

`spark = glueContext.spark_session`

`usersDF.MasterDF.createOrReplaceTempView("users")`

`outputDF = spark.sql("Select * from users")`
___
##### 5) Select particular fields from data frame.

`requiredFields = ['name','age']`

`NewDF = DF.select(*requiredFields)`
___
##### 6) Collect data frame as an array

`requiredFields = ['name','age']`

`NewDF = DF.select(*requiredFields).collect()`

___
##### 7) Filter data based on condition from data frame.

`NewDF = DF.filter(col('name') == 'Aditya').select(['age'])`
___
