# AdventureWorkDataWarehousing 2019

## Project Objective

The project uses Microsoft Adventurework database 2019 to develop AdventureWork datawarehouse. The project consist of following sections :

1. Developed ETL solution which uses various different data sources like CSV, Excel and SQL using SSIS.
2. Design Enterprise Business Matrix for Adevnturework Database.
3. Designed star schema dimensional model by loading facts and dimesnions.
4. Implement Error handelling and Logging of ETL solutions.


## Task 1 : Populate Master Tables

#### Table 1 :  dbo.DimCurrency

The AdventureWork2019 database table [Sales].[Currency] has data to be populated in dbo.DimCurrency. Inorder to try different datasources, the [Sales].[Currency]  data is populated in CSV file and uploaded in OLEDB destination table dbo.DimCurrency of AdventureWorksDW. The reference package name is DimCUrrency.




