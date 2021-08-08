|  SQL | 	NoSQL |  
----------  | ------|
|  SQL databases are primarily called as Relational Databases (RDBMS);    | NoSQL database are primarily called as non-relational or distributed database.       |
|SQL databases are table based databases     |  NoSQL databases are document based   |
|  SQL databases have predefined schema  |NoSQL databases have dynamic schema for unstructured data.   |
| SQL databases are vertically scalable    |  the NoSQL databases are horizontally scalable.      |
|SQL databases uses SQL ( structured query language ) for defining and manipulating the data, which is very powerful |In NoSQL database, queries are focused on collection of documents. Sometimes it is also called as UnQL     |    


# What kind of data is a good fit for an SQL database?

the complex query intensive environmen

heavy duty transactional type applications
# Give a real world example.
On a high-level, NoSQL don’t have standard interfaces to perform complex queries, and the queries themselves in NoSQL are not as powerful as SQL query language.

# What kind of data is a good fit a NoSQL database?
hierarchical data storage 
# Give a real world example.
as it is more stable and promises the atomicity as well as integrity of the data. While you can use NoSQL for transactions purpose, it is still not comparable and sable enough in high load and for complex transactional applications.

# Which type of database is best for hierarchical data storage?

NoSQL database

# Which type of database is best for scalability?

SQL databases 

# What does SQL stand for?

SQL (pronounced "ess-que-el") stands for Structured Query Language. SQL is used to communicate with a database. According to ANSI (American National Standards Institute), it is the standard language for relational database management systems.

# What is a realational database?

A relational database is a type of database that stores and provides access to data points that are related to one another.

# What type of structure does a relational database work with?

Relational databases are based on the relational model, an intuitive, straightforward way of representing data in tables. In a relational database, each row in the table is a record with a unique ID called the key. The columns of the table hold attributes of the data, and each record usually has a value for each attribute, making it easy to establish the relationships among data points.

# What is a ‘schema’?
A schema, or scheme, is an abstract concept proposed by J. Piaget to refer to our, well, abstract concepts. Schemas (or schemata) are units of understanding that can be hierarchically categorized as well as webbed into complex relationships with one anothe

# What is a NoSQL database?


A NoSQL originally referring to non SQL or non relational is a database that provides a mechanism for storage and retrieval of data. This data is modeled in means other than the tabular relations used in relational databases

# How does it work?

NoSQL databases can store relationship data—they just store it differently than relational databases do.

# What is inside of a Mongo database?

MongoDB stores data records as documents (specifically BSON documents) which are gathered together in collections. A database stores one or more collections of documents.

# Which is more flexible - SQL or MongoDB? and why.

To begin with the comparison, MongoDB is a Non-relational Database while SQL is a Relational Database. While MongoDB supports JSON querying, a SQL Database uses SQL query processing. The basic characteristics make MongoDB a more dynamic and complex option that is fit for hierarchical data while a SQL Database remains more predefined and suited for other kinds of data storage. 

# What is the disadvantage of a NoSQL database?

NoSQL databases don’t have the reliability functions which Relational Databases have (basically don’t support ACID).

This also means that NoSQL databases offer consistency in performance and scalability.

In order to support ACID developers will have to implement their own code, making their systems more complex.

This may reduce the number of safe applications that commit transactions, for example bank systems.

NoSQL is not compatible (at all) with SQL.

Note: Some NoSQL management systems do use a Structured Query Language.

This means that you will need a manual query language, making things slower and more complex.

NoSQL are very new compared to Relational Databases, which means that are far less stable and may have a lot less functionalities.
