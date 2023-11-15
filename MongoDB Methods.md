### MongoDB Insert() Method – db.Collection.insert()

> the insert() method inserts a document or documents into the collection. It takes two parameters, the first parameter is the document or array of the document that we want to insert and the remaining are optional.

*  Syntax
```
db.Collection_name.insert(<document or [document1, document2,…]>, { writeConcern: <document>, ordered: <boolean>})
```
* Example for inserting document
```
db.basicdata.insert({Name: "abc", num: 836})
```
* Example to Insert multiple documents in the collection
```
db.basicdata.insert([{Name: "jcg", num: 550}, {Name: "ydk", num: 430}, {Name: "ksw", num: 499}])
```
### MongoDB insertOne() Method – db.Collection.insertOne()

> insertOne() method inserts a document into the collection. This method inserts only one document at a time. 

* Syntax 
```
db.Collection_name.insertOne(<document>,{writeConcern: <document>})
```
* To Insert a single document
```
db.basicdata.insertOne({Name: "nci", num: 937})
```
* Insert a single document with _id field
```
db.basicdata.insertOne({_id: "basic573", Name: "nci", num: 937})
```
### MongoDB insertMany() Method – db.Collection.insertMany()

> The insertMany() method inserts one or more documents in the collection. It takes array of documents to insert in the collection. 
* Syntax 
```
db.Collection_name.insertMany([<document 1>, <document 2>, …],{
writeConcern: <document>, ordered: <boolean>})
```
* To Insert the array of documents
```
db.basicdata.insertMany([{name:"ihd",num:873},
                       {name:"fgr",num:249},
                       {name:"etg",num:233}])
```
* Insert unordered documents by setting the value of ordered option to false
```
db.student.insertMany([{_id:"basic947",name:"nxj",num:287}, 
                       {_id:"basic845", name:"nfu", age:253}], 
                       {ordered: false})
```
### MongoDB – Bulk.insert() Method
> The Bulk.insert() method is used to perform insert operations in bulk. Or in other words, the Bulk.insert() method is used to insert multiple documents in one go. To use Bulk.insert() method the collection in which data has to be inserted must already exist. 
* Syntax 
```
Bulk.insert(<document>);
```
* Unordered Insertion of documents
```
var bulk = db.students.initializeUnorderedBulkOp();
bulk.insert( { first_name: "Sachin", last_name: "Tendulkar" } );
bulk.insert( { first_name: "Virender", last_name: "Sehwag" } );
bulk.insert( { first_name: "Shikhar", last_name: "Dhawan" } );
bulk.insert( { first_name: "Mohammed", last_name: "Shami" } );
bulk.insert( { first_name: "Shreyas", last_name: "Iyer" } );
bulk.execute();
```
* Ordered Insertion of documents
```
var bulk = db.students.initializeOrderedBulkOp();
bulk.insert( { first_name: "Robin", last_name: "Marvin" } );
bulk.insert( { first_name: "John", last_name: "Hudson" } );
bulk.insert( { first_name: "Nancy", last_name: "Drew" } );
bulk.insert( { first_name: "Tom", last_name: "Wheeler" } );
bulk.insert( { first_name: "Anna", last_name: "Ryder" } );
bulk.execute();
```
### MongoDB – db.collection.bulkWrite() Method
> MongoDB is a versatile documentum based NoSQL database and has the ability to perform DB write operations efficiently by means of its bulkWrite() method. That means multiple documents can be inserted/updated/deleted in one shot.
* Syntax 
```
db.collection.bulkWrite([ <opr1>, <opr2>, …,<oprn> ], {writeConcern : <your document and this is optional>, ordered : <true/false, defaults to true and this is optional>})
```
* Unordered Bulkwrite
```
try {
  db.students.bulkWrite([
     {insertOne:{"document":{studentId:5, studentName:"Virat", studentAge:34}}},
     { updateOne : {
        "filter" : { "studentId" : 2 }, 
        "update" : { $set : { "studentName" : "Dev" } }
     } },
     { deleteMany : { "filter" : { "studentAge" : 20} } }, 
     { replaceOne : {
        "filter" : { "studentId" : 3 },
        "replacement" : { "studentId" : 30, "studentName" : "Anderson" }
     } }  
  ],{ ordered : false });
} catch (e) {
  print(e);
}
```
* Ordered BulkWrite
```
try {
  db.students.bulkWrite([
     {insertOne:{"document":{studentId:5, studentName:"Virat", studentAge:24}}},
     { updateOne : {
        "filter" : { "studentId" : 2 }, 
        "update" : { $set : { "studentName" : "Shreyas" } }
     } },
     { deleteMany : { "filter" : { "studentAge" : 20} } }, 
     { replaceOne : {
        "filter" : { "studentId" : 3 },
        "replacement" : { "studentId" : 40, "studentName" : "Rahul" }
     } }  
  ],{ ordered : true });
} catch (e) {
  print(e);
}
```
### MongoDB – Update() Method
> The update() method updates the values in the existing document in the collections of MongoDB. When you update your document the value of the _id field remains unchanged. By default, the db.collection.update() method updates a single document. Include the option multi: true to update all documents that match the given query. This method can be used for a single updating of documents as well as multi documents.

* Syntax 
```
db.COLLECTION_NAME.update({SELECTION_CRITERIA}, {$set:{UPDATED_DATA}}, {
     upsert: <boolean>,
     multi: <boolean>,
     writeConcern: <document>,
     collation: <document>,
     arrayFilters: [ <filterdocument1>, ... ],
     hint:  <document|string>        
   })
```
* Examples to update 
```
db.student.update({name:"shami"},{$set:{age:36}}
```
```
db.student.update({name:"siraj"},{$set:{name:"striker"}})
```
### MongoDB updateOne() Method – db.Collection.updateOne()
> In MongoDB, updateOne() method updates a first matched document within the collection based on the given query. When you update your document the value of the _id field remains unchanged. This method updates one document at a time and can also add new fields in the given document. It takes three parameters, the first one is the selection criteria to update the document, the second one is the new data to be updated, and the remaining are optional.
* Syntax 
```
db.Collection_name.updateOne(

{Selection_Criteria}, {$set:{Update_data}}, {

    upsert: <boolean>,

    writeConcern: <document>,

    collation: <document>,

    arrayFilters: [<filterdocument1>, … ],

    hint: <document|string>        

})
```
* Example to Update
```
db.student.updateOne({name: "samson"}, {$set:{age:25}})
```
```
db.student.updateOne({name:"samson"},{$set:{name:"sanju samson"}})
```
* Insert a new field in the document using the updateOne method
```
db.student.updateOne({name: "tahir"}, {$set:{age: 37}})
```
### MongoDB updateMany() Method – db.Collection.updateMany()
> The updateMany() method updates all the documents in MongoDB collections that match the given query. When you update your document, the value of the _id field remains unchanged. This method can also add new fields in the document. Specify an empty document({}) in the selection criteria to update all collection documents.
* Syntax 
```
db.Collection_name.updateMany({Selection_Criteria},{$set:{Update_Data}}, 

{
    upsert: <boolean>,

    multi: <boolean>,

    writeConcern: <document>,

    collation: <document>,

    arrayFilters: [<filterdocument1>, … ],

    hint: <document|string>        

})
```
* Example
```
db.student.updateMany({age:36},{$set:{rank:4}})
```
### MongoDB – db.collection.Find() Method
> In MongoDB, find() method is used to select documents in a collection and return a cursor to the selected documents. Cursor means a pointer that points to a document, when we use find() method it returns a pointer on the selected documents and returns one by one.
* Syntax 
```
db.Collection_name.find(selection_criteria, projection,options)
```
* Find all the documents present in the collection
```
db.basicdata.find()
```
* Find all the document that matches the given filter query(i.e., age:18)
```
db.student.find({age:18})
```
* Find the embedded document that matches the given filter query
```
db.student.find({score:{math: 230, science: 234}})
```
### MongoDB – FindAndModify() Method
> The findAndModify() method modifies and return a single document that matches the given criteria. By default, this method returns a pre-modification document. To return the document with the modifications made on the update, use the new option and set its value to true. It takes a document as a parameter.

* Syntax
```
db.Collection_name.findAndModify(
{
    selection_criteria:<document>,
    sort: <document>,
    remove: <boolean>,
    update: <document>,
    new: <boolean>,
    fields: <document>,
    upsert: <boolean>,
    bypassDocumentValidation: <boolean>,
    writeConcern: <document>,
    collation: <document>,
    arrayFilters: [ <filterdocument1>, ... ]
})
```
* We are increasing runs by 4 whose name is rohit
```
db.playerruns.findAndModify({query:{name:"rohit"},update:{$inc:{runs:4}}})
```
> $inc operator increases the value in the score.
* To Get a modified document
```
 db.playerruns.findAndModify({query:{name:"rohit"}, update:{$inc:{score:72}},new:true})
```
### MongoDB – FindOne() Method
> The findOne() method finds and returns one document that matches the given selection criteria. If multiple documents satisfy the given query expression, then this method will return the first document according to the natural order which reflects the order of documents on the disk. If no document matches the selection criteria, then this method will return null. It takes two parameters first one is the query criteria and the other is optional.

* Syntax 
```
db.Collection_Name.findOne(query:<document>, projection:<document>)
```
* With empty query specification it returns the first document in the collection
```
db.student.findOne()
```
* Return first document that contains the specified field
```
db.student.findOne({language:"python"})
```
* Return first document that contains language field
```
db.student.findOne({language:"c++"})
```
* Finding document using projection
```
db.student.findOne({name: "Gill"}, {_id: 0, language:1})
```
### MongoDB – findOneAndDelete() Method

> The findOneAndDelete() method deletes a single document based on the selection criteria from the collection. It deletes the first document from the collection that matches the given filter query expression. It takes five parameters the first parameter is the selection criteria and the others are optional. 

* Syntax 
```
db.Collection_name.findOneAndDelete(Selection_criteria,{projection: <document>, sort: <document>, maxTimeMS: <number>, collation: <document>})
```
* Find and Delete the first document according to the selection criteria
```
db.student.findOneAndDelete({name:"Jaishwal"})
```
* Find and Delete the document according to the selection criteria
```
db.student.findOneAndDelete({age:17},{sort:{age:-1}})
```
> we first sort the documents according to the age field in decreasing order and then delete the first document whose age is 17.

> If no document found in collection it will return null.

### MongoDB – db.collection.findOneAndReplace() Method

> The findOneAndReplace() method replaces the first matched document based on the given selection criteria. By default, this method returns the original document. To return the replacement document, set the value of the returnNewDocument option to true. It takes eight parameters, the first parameter is selection criteria and the second parameter is the replacement document. And the others are optional. Using this method you can also replace embedded documents. You can also use this method in multi-document transactions.

* Syntax 
```
db.Collection_name.findOneAndReplace(selection_criteria:<document>,
replacement: <document>,
{
    projection: <document>,

    sort: <document>,

    maxTimeMS: <number>,

    upsert: <boolean>,

    returnNewDocument: <boolean>,

    collation: <document>

  }) 
```
* Replace the first matched document whose age is 17 and returns replaced document
```
db.student.findOneAndReplace({age:17},{name:"ishan", age:17})
```
* Replace the first matched document whose age is 17 and returns a new document
```
db.student.findOneAndReplace({age:17},{name:"Sagar", age:17},{returnNewDocument:true})
```
### MongoDB – db.collection.findOneAndUpdate() Method

> The findOneAndUpdate() method updates the first matched document in the collection that matches the selection criteria. If more than one document matched the selection criteria then it updates only the first matched document. When we update the document, the value of the _id field remains unchanged. This method will return the original document but if we want to return the updated document then we have to set the value of the returnNewDocument parameter to true. It takes three parameters, the first one is the selection criteria, the second one is the new data to be updated, and the remaining are optional. Using this method you can also replace embedded documents. You can also use this method in multi-document transactions.

* Syntax 
```
db.collection.findOneAndUpdate(selection_criteria: <document>, update_data: <document>, 
{

   projection: <document>,

    sort: <document>,

    maxTimeMS: <number>,

    upsert: <boolean>,

    returnNewDocument: <boolean>,

    collation: <document>,

    arrayFilters: [ <filterdocument1>, … ]

})
```
* To update the first matched document
```
db.Matchdata.findOneAndUpdate({name:"Shami"},{$inc:{Wickets:7}})
```
* Update the value of the embedded document
```
db.Matchdata.findOneAndUpdate({name:"Virat"},{$inc:{"score.Aus":97}})
```
* Update the first matched document and return the updated document
```
db.Matchdata.findOneAndUpdate({name:"Siraj"},{$inc:{Wickets:13}},{returnNewDocument:true})
```
* 