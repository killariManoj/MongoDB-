# MongoDB 

* What is MongoDB?
```
MongoDB is a document-oriented NoSQL database system that provides high scalability, flexibility, and performance. Unlike standard relational databases, MongoDB stores data in a JSON document structure form. This makes it easy to operate with dynamic and unstructured data and MongoDB is an open-source and cross-platform database System.
```

## MongoDB – Database, Collection, and Document

* View Database:
```
show dbs
```
* Creating Database:
```
use database_name 
```
> Your created database (mydb) is not present in list. To display database, you need to insert at least one document into it.
* To check your currently selected database
```
db
```
* Collection
```
Collections are just like tables in relational databases, they also store data, but in the form of documents. A single database is allowed to store multiple collections.  
```
* Creating collection:
```
db.collection_name.insertOne({..})
```
