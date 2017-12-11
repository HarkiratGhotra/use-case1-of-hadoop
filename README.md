# use-case1-of-hadoop

## I have made use_case of Hadoop for Online Store

#Description 
* In Online store, user comes, log in and buy products

* Here we have use case to show the most loyal user and the category which user buys more, so company can show them more discount on most buying product for specific user

* First - we get source files from remote server, there are three files related to Online Store, which contains product info, user info and user activity *

* Source files are Product_info, User_info, User_activity
* Then next step is transfering the source files to Landing Zone.
* We can use unix script inorder to transfer all three files to HDFS location, in this case landing zone is HDFS, where we are getting the source files.
* Inside Unix Script, we can write sqoop commands to import file into HDFS location
* We can use dctp for copying files from one cluster to another cluster
* After recieving files in HDFS location, create Temporary table in HIVE.

```
Create temp_product_info table (Columns)
Row format delimited
fields terminated by ','
stored as parquet;
```
```
Create temp_user_info table (Columns)
Row format delimited
fields terminated by ','
stored as parquet;
```
```
Create temp_user_activity table (Columns)
Row format delimited
fields terminated by ','
stored as parquet;
```
* Load the data into temp table
* Once temp tables have been created, then start creating internal tables in hive using partitioned by date, because of incremental load, as we want to analyse the data let's say 1st of every month.
* While inserting data into hive table use Joining between two tables to get the required output
* Insert the data into these hive table from temp Table partiton (date)
* DO data cleansing, make sure if we have NULL value in these table, we can use
Look ups to enrich the data

* Then use sqoop to export data from HIVE to MYSQL database, you can export complete table from HIVE to MYSQL.
* Once data is transfered, the use SQL query to find out maximum number of product purchased by user.
* Use of MicroStrategy Tool can be used to generate the report based on facts and attributes. We can generates quaderly or yearly data 
