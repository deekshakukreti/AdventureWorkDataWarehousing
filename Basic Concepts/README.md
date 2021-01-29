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

Also, when their is wide disparity in the probability of access the data, then it is benefitial to seperate the data. Also, the introduction of derived data into 
physical database design can reduce the amount of I/O needed. For example, storing the calculated fields or storing names in differebnt languages as used in AdventureWork
database.

Another technique is by creating creative index when operational data is tranfered to datawarehouse. The creative index does a profile on item that is of interest
to end users for example latest shipmest, largest purchases or inactive users. Also, referential tables are used in maintaining datawarehouses.A database design a reference 
table is a table into which an enumerated set of possible values of a certain field data type is divested.



### Interfaces to many technologies

Datawarehouse has the ability to both receive data and pass data from the wide variety of technologies. Data passes into the data warehouse from the operational environment and
the ODS, and from the data warehouse into data marts, DSS applications, exploration and data mining warehouses, and alternate storage. The data passed to and from
are in batch mode. The interface to different technologies require several consideration:
1. Does data pass from one DBMS to another easily.
2. Does it pass from one operating system to another easily.
3. Does it change its basic format in passage (ASCII etc.)
4. Can passage in multidimensional process be done easily.
5. Is the context of data lost in translation as data is moved to other environments.


### MetaData Management

Metadata is important because of the fundamental differences in development lifecycle of the datawarehouse. The datawarehouse follows iteartive development lifecycle. The user of the datawarehouse must have accurate and up-to date access to metadata.

Typically, technical metadata is described in the following :

1. Data warehouse table structure
2. Data warehouse table attribution
3. Data warehouse source data
4. Mapping from the system of record to the datawarehouse
5. Data model specification
6. Exttact logging
7. Common routines for access of data

Their are two types of Meta data. The business data which is of use and value to business person. The next is the technical metadata which is of use and value to the technicians.  


### Distributed Datawarehouse

#### Types of Distributed warehouse

1. Business is distributed geographically among different product lines. In this case we have local and global data warehouse. The local datawarehouse is used for data processing at local site whereas in global datawarehouse is part of the business that is integrated accross the business.

2. The data warehouse environment will hold a lot of data, and the volume of data will be distributed over multiple processors. Logically there is a single data warehouse, but physically there are many data warehouses that are all tightly related but reside on separate processors. This configuration can be called the technologically distributed data warehouse.

3. The lack of coordination of the growth of the different data warehouses is a result of political and organizational differences. This case can be called the independently evolving distributed data warehouse.











