# AdventureWorkDataWarehousing 2019

The project is developed in SQL Server 2019 and Visual Studio 2017. The database files attached in SQL server management studio is AdventureWorks2019.bak file extracted from MSDN.

## Project Objective

Since this is a first time load, bringing all data from source to destination hence Full Load loading is performed. This type of loading can also be done when the entire destination table or database needs to be refreshed. The project uses Microsoft Adventurework database 2019 to develop AdventureWork datawarehouse. The project consist of following sections :

1. Developed ETL solution which uses various different data sources like CSV, Excel and SQL using SSIS.
2. Design Enterprise Business Matrix for Adevnturework Database.
3. Designed star schema dimensional model by loading facts and dimensions.
4. Implement Error handelling and Logging of ETL solutions.


## Task 1 : Populate DataWarehouse Master Tables

#### Table 1 :  dbo.DimCurrency

The AdventureWork2019 database table [Sales].[Currency] has data to be populated in dbo.DimCurrency. Inorder to try different datasources, the [Sales].[Currency]  data is populated in CSV file and uploaded in OLEDB destination table dbo.DimCurrency of AdventureWorksDW. The reference package name is DimCurrency.

#### Table 2 :  dbo.DimSalesTerritory

The SQL server database table used in to populate dbo.DimSalesTerritory is [Sales].[SalesTerritory] from AdventureWork2019 database. The package DimSalesTerritory uses data flowtask in SSIS components to perform ETL process for this table. OLEDB source and Destination extract and load data to different databases in SQL server.

#### Table 3 :  dbo.DimGeography

Instead of writing join query in query analyser, Merge Join component is used to with AdventureWork2019 database tables. The multiple tables used in ETL are CountryRegion, Address, StateProvince and DimSalesTerritory. Merge join will give error if data is not sorted, hence it is important to put SOrtComponent before Merge Join in SSIS.
 
#### Table 4 : dbo.DimDepartmentGroup

The data is populated from [HumanResources].[Department]. Distinct GroupName gives all the reference data for DimDepartmentGroup.

#### Table 5 : dbo.DimCustomer

The data is populated from various Adventurework Database tables and views. Merge Join component and Derived component are majorly used to design the loading of dbo.DimCustomer. 

#### Table 6 : dbo.DimPromotion

This table is populated from Sales.SpecialOffer which has only 16 records in the AdventureWork Database table. The destination has few derived columns and also consist of only 16 records in the dbo.DimPromotion.

#### Table 7 : dbo.DimProductSubCategory

The dimansional table is derived from ProductionSubCategory table. The package development consist of OLEDB source and destination components alongwith derived column component. Only 37 records were reproduced in this table.


#### Table 8 : dbo.DimProductCategory



## Task 2 : Enterprise Business Matrix


## Theory

Another type of load is Incremental loads. This type of load occurs when full load has taken place and only subsequent amount of data changes needs to be loaded from source to destination. For sensitive data, this load can occur every five minute, depending on the infrastructure capacity. Slowly Changing Dimension (SCD) is a term used to identify which dimension tables you track historical changes. You may need to keep track of this so that if you were to run a report today and you want the report to be consistent to when you ran it one year ago before a customer’s address changed, the report would show you the same results.

##### SCD Type 0
Fixed, absolutely no updates or changes allowed

##### SCD Type 1 
Replaces/updates changes to record

##### SCD Type 2
Keeps historical record by inserting a new record and expiring the old record


#### Variables and Parameters

Parameter values cannot be changed when the package is running (at runtime). Parameter values are fixed for the duration of the package execution. Alternatively, variables values can be changed at any time. Variables are also used to assign values dynamically at runtime.


#### Package vs. project parameters

Package deployment : The package deployment model means nothing is shared and that everything is maintained separately within each individual SSIS package—variables, connection manager, etc.

Project deployment : The project deployment model enables you to deploy your SSIS project as a single unit with shared resources, including parameters, and packages. It is deployed to either file, or to the SSISDB database catalog within SQL Server.
 
#### Transaction

To be deemed successful, transaction should be completed fully. If any step fails, the transactio is considered to be unsuccessful. This helps maintaing the integrity of data. The scope of the transaction is at different levels in SSIS and they are package level, individual control flow container or task level. Any tasks inside of the container will also be a part of the transaction as long as each individual task has the TransactionOption property set to Supported, which is the default. If there are some tasks that you do not want to rollback within a container, in case of failure, set the TransactionOption to NotSupported.


#### Checkpoint

If a package fails at a certain point, it can be configured to restart from the point of failure, or from an earlier step at the next attempt to run the package. This configuration process is called checkpoints.

#### Containers and Parameters

SSIS has three types of containers.

Sequence Container Grouping and organizing tasks.

For Loop Container Iterating tasks multiple times.

Foreach Loop Container Iterating through each object or file.
 
Each question mark (?) represents a different variable 


#### Data Profiling, Parallelism, Transactions, logging, and security

Data Profiler is used to evaluate the source data. It checks the content, structure and quality of data. It cannot identify bad data, but just the metrics. This includes the frequency of the values, the datatypes, NULLs, and length of data in the columns. You can setup a Data Profiler Task in Control flow.

Parallelism is simply running multiple SSIS tasks concurrently (together in parallel). So when you have multiple tables to be loaded that don’t depend on each other for their data (Customers, Products, Cities), they can be loaded at the same time, instead of loading Products, then loading Cities, and finally Customers. It is very important to monitor parallelisation as sometime it can run slower impacting the purpose.


