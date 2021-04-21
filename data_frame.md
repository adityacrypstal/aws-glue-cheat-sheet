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

##### 8) Get Particular Cell in data frame

`NewDF = DF.filter(col('name') == 'Aditya')`

With AND Operator

`NewDF = DF.filter((col('name') == 'Aditya') & (col('age') == 23))`
 
With OR Operator

`NewDF = DF.filter((col('name') == 'Aditya') | (col('age') == 23))`

___

##### 9) Pick particular cell in data frame.

`value = DF.collect()[Row number][Column number]`

 Get first row of data frame.

`FirstRow = DF.first().collect()`

---

##### 10) Rename / Add column in data frame.

`from pyspark.sql.functions import lit, col`

 Add New Column with data from Existing Column.

`NewDF = NewDF.withColumn("newColumn",col("oldColumn"))`

 Add New Column with data from static value.

`NewDF = NewDF.withColumn("newColumn",lit("aditya))`

---

##### 11) Union Two Data Frames.

`requiredFields = ['name','age']`


`NewDF = DFA.select(*requiredFields).union(DFB.select(*requiredFields))`



---
##### 12) Rename Column in RDD



`NewDF = DFA.select(*requiredFields).withColumnRenamed("name", "first name")`



---
##### 13) Generate random id for dataset



`from pyspark.sql.functions import rand`

`NewDF = DFA.withColumn("id", rand())`



---
##### 14) Types of join in pySpark

Cross Jojn

`df1.crossJoin(df2)`


Inner Join

`df1.join(df2, on='id', how='inner')`


Left Join

`df1.join(df2, on='id', how='left')`

`df1.join(df2, on='id', how='leftouter')`

Right Join

`df1.join(df2, on='id', how='right')`

`df1.join(df2, on='id', how='rightouter')`

Full Outer Join

`df1.join(df2, on='id', how='outer')`

`df1.join(df2, on='id', how='full')`

Left Semi Join

`df1.join(df2, on='id', how='leftsemi')`

Left Anti Join

`df1.join(df2, on='id', how='leftanti')`

##### 15) Print Columns of RDD

`print(DF.columns)`

------
##### 15) Print Count of Rows

`print(DF.count())`

------
