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

The mapping of data from the local operational systems to the data structure of the global data warehouse. It will be different for each local data warehouse.

A variation of the local and global data warehouse structure that has been discussed is to allow a global data warehouse “staging” area to be kept at the local level. Each local area stages global warehouse data before passing the data to the central location. For example, say that in France are two data warehouses—one a local data warehouse used for French decisions. In this data warehouse, all transactions are stored in the French franc. In addition, there is a “staging area” in France, where transactions are stored in U.S. dollars. The French are free to use either their own local data warehouse or the staging area for decisions.


### OLAP (Multidimensional DBMS)

Also called as data marts, allows the organisation to have flexible access to data, to slice and dice the data any number of ways, and to dynamically explore relationships between summary and detailed data. Multidimansioal DBMS offer both flexibiltiy and control to the end user. Data flows from datawarehouse to multidimensional database and periodically refreshed. 


### External Data And The datawarehouse

The data that comes internally from the corporation and has already been shaped into a regularly occuring format. External data and usually enters the corporation in an unpredictable format.

When external data is not entered into the data warehouse :

1. The original source of the data is an external file like excel, which analyst have to enter the data manually rather then from the source system.
2. It becomes hard to recall the data.


### A Migration Plan

The beginning of migration plan is the corporate data model which represents the needs of the corporation. The corporate data model, needs to identify, at minimum :

1. Major subjects  of the corporation
2. Definition of the major subjects of the corporation
3. Relationships between the major subjects
4. Groupings and keys that more fully represent the major subjects, including the following :
	a. Attributes of the major subjects
	b. Keys of the major subjects
	c. Repeating groups of keys and attributes
	d. Connectors between major subject areas
	e. Subtyping relationships

As a rule, the corporate data model identifies corporate information at a high level. From the corporate data model, a lower-level model is built. The lower-level model identifies details
that have been glossed over by the corporate data model. This mid-level model is built from the subject areas that have been identified in the corporate data model, one subject area at a time.

Reasons for excluding derived data and DSS data from the corporate data model and the mid-level model include the following :

1. Derived data and DSS data change frequently.
2. These forms of data are created from atomic data.
3. They frequently are deleted altogether.
4. There are many variations in the creation of derived data and DSS data.

After this, the next activity is defining the system of record. It is the identification of the 'best' data the corporation has. In other words, the architect
starts with the data model and asks what data is in hand that fullfills the data requirement identified in the data model. 

Once, the system of records is defined then the technological challenges are identified that could be faced while brining the data in datawarehouse. Few technological challenges are:
1. A change in DBMS : The system of record in one DBMS, and the datawarehouse is in another DBMS.
2. A change in operating systems : The system of record is in one operating system, and the datawarehouse is in another system.
3. The need to merge data from different DBMS and operating system : System-of-record data must be pulled from multiple DBMSs and multiple operating systems and must be merged in a meaningful way. 
4. A change in basic data format : Data in one environment is stored in ASCII, data in the data warehouse is stored in EBCDIC.

Other related issues are , huge volume of data to be migrated in datawarehouse. The cleansing of data is also important challenge faced during migration if data.

After all the analysis of technological challenges, the next step is to design data warehouse. If data modelling is done properly, then design is very simple.

Few elements that change data model to datawarehouse are :

1. An element of time needs to be added to the key structure if one is not already present.
2. All operational data needs to be eliminated.
3. Referential integrity relationships need to be turned into artifacts.
4. Derived data that is frequently needed is added to the design.

The data needs to be altered when appropriate :

1. Adding arrays of data
2. Adding data redundantly
3. Further seperating data under right conditions
4. Merging tables when appropraite


#### Stability Analysis Of Data

In stability analysis, data whose content has tendancy to change is isolated to data whose content is stable. For example, bank account balance changes frequently in a day, but the customer address changes very slowly.Because of the difference in stability of bank account balance and customer address, 
these elements of data need to be seperated into different physical constructs.


After the data warehouse design is complete, it is important to design and build interfaces between the system of records and datawarehouse. ETL softwares are used to build and maintain interfaces.
If you wait for existing systems to be cleaned up, you will never build a data warehouse. The issues and activities of the existing systems’ operational environment must be independent of the issues and activities of the data warehouse environment. One train of thought says, “Don’t build the data
warehouse until the operational environment is cleaned up.”

The analysts communicates with the datawarehouse team to make the adjustments in datawarehouse that is communicated as a requirement.The data architect may add
data, delete data, alter data, and so forth based on the recommendations of the end user who has touched the data warehouse.


#### Strategic Considerations
















