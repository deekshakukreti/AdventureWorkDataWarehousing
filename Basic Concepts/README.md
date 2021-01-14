# Basic Concepts of DataWarehousing

A datawarehouse is subject-oriented, integrated, non-volatile and time-variant collection of data. Data is fed from multiple sources which 
makes an important feature of integration in datawarehousing. It is non-volatile because of its data loading procedure which does not change 
the data and load a snapshot of the source data.

Data Partitioning helps to maintain the data in datawarehouse. If the data is not partitioned, then it fails to perform some tasks like :

1. Restructuring
2. Indexing
3. Recovery
4. Monitoring


Hence, data partitioning can be divided into :
1. Date
2. Line of Business
3. Geography
4. Organisational Unit
 

Data models are applicable to both existing systems and data warehouses. The data models are best build iteratively i.e. first part of the datawarehouse is build,
and then the second and so forth. The following are the reasons why iterative development is important :
1. The end user is unable to articulate many requirements until the first iteration is done.
2. Management will not make commitments until atleast few actual results are tangible.
3. Visible results must be seen quickly.


### Normalisation and Denormalisation in Datawarehousing

Data is normalised so that each occurrence of a sequence of data resides in a different physical location. Retrieving each occurrence, n, n+1, n+2,....
requires a physical I/O to get the data. If the data were placed in a single row in an array, then a single I/O would suffice to retrieve it.

Creating an array of data is important when :
1. The data is accessed in sequence.
2. Has stable number of occurrence.
3. Where it is created or updated in a statistically well behaved sequence.

Another important physical design relevant to data warehouse environment is delibrate introduction of the redundant data. For example, introducing a field in 
each table of database where it is most likely to be accessed in the base parts table. By doing so the access of the data is more efficient, and the update is 
not optimal. 








