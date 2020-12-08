# AdventureWorkDataWarehousing 2019

## AdventureWork Database version 

The project is developed in SQL Server 2019 and Visual Studio 2017. The datbase files attached in SQL server management studio is AdventureWorks2019.bak file.

## Project Objective

Since this is a first time load, bringing all data from source to destination hence Full Load loading is performed. This type of loading can also be done when the entire destination table or database needs to be refreshed. The project uses Microsoft Adventurework database 2019 to develop AdventureWork datawarehouse. The project consist of following sections :

1. Developed ETL solution which uses various different data sources like CSV, Excel and SQL using SSIS.
2. Design Enterprise Business Matrix for Adevnturework Database.
3. Designed star schema dimensional model by loading facts and dimesnions.
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



Another type of load is Incremental loads. This type of load occurs when full load has taken place and only subsequent amount of data changes needs to be loaded from source to destination. For sensitive data, this load can occur every five minute, depending on the infrastructure capacity. Slowly Changing Dimension (SCD) is a term used to identify which dimension tables you track historical changes. You may need to keep track of this so that if you were to run a report today and you want the report to be consistent to when you ran it one year ago before a customer’s address changed, the report would show you the same results.

##### SCD Type 0
Fixed, absolutely no updates or changes allowed

##### SCD Type 1 
Replaces/updates changes to record

##### SCD Type 2
Keeps historical record by inserting a new record and expiring the old record


