### Introduction :

A startup company called Sparkify provides music streaming to the users through the application. The songs details and the user activity data from the application are currently available and stored in the format of JSON.The sparkify has grown their user base and song database and it's difficult to process this much data through JSON files.

Instead of storing the generated data from the user into the JSON files, I would recommend a cloud database which is widely used for modeling techniques and it helps in the fast retrieval of data and store large amount of data. This can be made even more efficient with the approach of the STAR schema creating in Redshift Cluster.

Created a STAR schema, optimized for song play analysis.

`Fact Table: songplays: attributes referencing to the dimension tables.`

`Dimension Tables: users, songs, artists and time table.`

### DWH configurations:

- Create an IAM Role that makes Redshift able to access S3 bucket (ReadOnly)

- Create a RedShift Cluster and get the DWH_ENDPOIN(Host address) and DWH_ROLE_ARN and fill the config file.

### Description :

**sql_queries.py** : 
Contains all SQL queries of the project.

**create_tables.py**: 
Run this file only after writing queries in the sql_queries.py file. This has two functions:
```
drop_tables: This function is used to drop the tables. 
create_tables: This function is used to create tables.
```

**etl.py:**
Check the table schemas in your redshift database.
```
load_staging_tables: This function is used to load the data from S3 to Redshift staging tables. 
insert_tables: This functionis used to insert data into fact and dimemsion tables from staging tables.
```

#### Order of execution :

- create_tables.py
```$ python create_tables.py```

- etl.py
```$ python etl.py```
