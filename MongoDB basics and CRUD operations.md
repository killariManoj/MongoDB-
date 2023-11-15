* MongoDB Overview
```
MongoDB is a cross-platform, document oriented database that provides, high performance, high availability, and easy scalability. MongoDB works on concept of collection and document.
```
* Database
```
Database is a physical container for collections. Each database gets its own set of files on the file system. A single MongoDB server typically has multiple databases.
```
* Collection
```
Collection is a group of MongoDB documents. It is the equivalent of an RDBMS table. A collection exists within a single database. Collections do not enforce a schema. Documents within a collection can have different fields. Typically, all documents in a collection are of similar or related purpose.
```
* Document
```
A document is a set of key-value pairs. Documents have dynamic schema. Dynamic schema means that documents in the same collection do not need to have the same set of fields or structure, and common fields in a collection's documents may hold different types of data.
```
* _id
```
_id is a 12 bytes hexadecimal number which assures the uniqueness of every document. You can provide _id while inserting the document. If you don’t provide then MongoDB provides a unique id for every document. These 12 bytes first 4 bytes for the current timestamp, next 3 bytes for machine id, next 2 bytes for process id of MongoDB server and remaining 3 bytes are simple incremental VALUE.
```

### MongoDB - Create Database

* To create database
```
use DATABASE_NAME
```
> Your created database (DATABASE_NAME) is not present in list. To display database, you need to insert at least one document into it.
* To switch databases
```
use DATABASE_NAME
```
* To check your currently selected database
```
db
```
* To check databases list
```
show dbs
```
> In MongoDB default database is test. If you didn't create any database, then collections will be stored in test database.

### MongoDB - Drop Database

* Drop Database
```
db.dropDatabase()
```
> This will delete the selected database. If you have not selected any database, then it will delete default 'test' database.

### MongoDB - Create Collection

* To create collection
```
db.createCollection(name, options)
```
> In the command, name is name of collection to be created. Options is a document and is used to specify configuration of collection.
* To check the created collection
```
show collections
```
> In MongoDB, you don't need to create collection. MongoDB creates collection automatically, when you insert some document.

### MongoDB - Drop Collection

* To Drop collection
```
db.COLLECTION_NAME.drop()
```
### MongoDB - Datatypes

* String − This is the most commonly used datatype to store the data. String in MongoDB must be UTF-8 valid.

* Integer − This type is used to store a numerical value. Integer can be 32 bit or 64 bit depending upon your server.

* Boolean − This type is used to store a boolean (true/ false) value.

* Double − This type is used to store floating point values.

* Min/ Max keys − This type is used to compare a value against the lowest and highest BSON elements.

* Arrays − This type is used to store arrays or list or multiple values into one key.

* Timestamp − ctimestamp. This can be handy for recording when a document has been modified or added.

* Object − This datatype is used for embedded documents.

* Null − This type is used to store a Null value.

* Symbol − This datatype is used identically to a string; however, it's generally reserved for languages that use a specific symbol type.

* Date − This datatype is used to store the current date or time in UNIX time format. You can specify your own date time by creating object of Date and passing day, month, year into it.

* Object ID − This datatype is used to store the document’s ID.

* Binary data − This datatype is used to store binary data.

* Code − This datatype is used to store JavaScript code into the document.

* Regular expression − This datatype is used to store regular expression.

### MongoDB - Insert Document

* To insert data into MongoDB collection
```
db.COLLECTION_NAME.insert(document)
```
* To insert only one document into a collection
```
db.COLLECTION_NAME.insertOne(document)
```
* To insert multiple documents into a collection
```
db.COLLECTION_NAME.insertMany(document)
```

### MongoDB - Query Document

* To display all the documents in a non-structured way
```
db.COLLECTION_NAME.find()
```
* To display the results in a formatted way
```
db.COLLECTION_NAME.find().pretty()
```
* To query documents based on the AND condition
```
db.mycol.find({ $and: [ {<key1>:<value1>}, { <key2>:<value2>} ] })
```
* To query documents based on the OR condition
```
db.mycol.find(
   {
      $or: [
         {key1: value1}, {key2:value2}
      ]
   }
).pretty()
```
* To query documents based on the NOT condition
```
db.COLLECTION_NAME.find(
	{
		$not: [
			{key1: value1}, {key2:value2}
		]
	}
)
```
* To query documents based on the NOT condition
```
db.COLLECTION_NAME.find(
	{
		$NOT: [
			{key1: value1}, {key2:value2}
		]
	}
).pretty()
```

### MongoDB - Update Document

* To update the values in the existing document
```
db.COLLECTION_NAME.update(SELECTION_CRITERIA, UPDATED_DATA)
```
* To update multiple documents, you need to set a parameter 'multi' to true.
```
db.COLLECTION_NAME.update(SELECTION_CRITERIA, UPDATED_DATA, {multi:true})
```
* The `save()` method replaces the existing document with the new document passed in the save() method
```
db.COLLECTION_NAME.save({_id:ObjectId(),NEW_DATA})
```
* The `findOneAndUpdate()` method updates the values in the existing document.
```
db.COLLECTION_NAME.findOneAndUpdate(SELECTIOIN_CRITERIA, UPDATED_DATA)
```
* This `updateOne()` method updates a single document which matches the given filter.
```
db.COLLECTION_NAME.updateOne(<filter>, <update>)
```
* The `updateMany()` method updates all the documents that matches the given filter.
```
db.COLLECTION_NAME.update(<filter>, <update>)
```

### MongoDB - Delete Document

* MongoDB's remove() method is used to remove a document from the collection. remove() method accepts two parameters. One is deletion criteria and second is justOne flag.
```
> deletion criteria − (Optional) deletion criteria according to documents will be removed.

> justOne − (Optional) if set to true or 1, then remove only one document.
```
* Basic syntax of remove() method
```
db.COLLECTION_NAME.remove(DELLETION_CRITTERIA)
```
* If there are multiple records and you want to delete only the first record, then set justOne parameter in remove() method.
```
db.COLLECTION_NAME.remove(DELETION_CRITERIA,1)
```
* If you don't specify deletion criteria, then MongoDB will delete whole documents from the collection.
```
b.COLLECTION_NAME.remove({})
```
