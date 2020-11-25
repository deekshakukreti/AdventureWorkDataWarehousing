# AdventureWorkDataWarehousing 2019

## Project Objective

The project uses Microsoft Adventurework database 2019 to develop AdventureWork datawarehouse. The project consist of following sections :

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



