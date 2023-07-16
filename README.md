## Document Title: MONGODB UPDATE & FILTERIZATION

# 1. Updating documents in MongoDB:

a) `updateOne()` method:
Syntax: `db.collection_name.updateOne(filter, update, options)`

Example: Update Subham's email in the 'contacts' collection.
```javascript
db.contacts.updateOne(
  {'name': 'Subham'},
  {$set: {'email': 'subham@gmail.com'}}
);
```
This command updates the document with the field `name` equal to `'Subham'` in the `contacts` collection and sets the `email` field to `'subham@gmail.com'`.

b) `updateMany()` method:
Syntax: `db.collection_name.updateMany(filter, update, options)`

Example: Add the 'age' field to Subham's record.
```javascript
db.contacts.updateOne(
  {'name': 'Subham'},
  {$set: {'age': 22}}
);
```
This command updates the document with the field `name` equal to `'Subham'` in the `contacts` collection and adds the `age` field with a value of `22`.

Example: Remove the 'age' field from Subham's record.
```javascript
db.contacts.updateOne(
  {'name': 'Subham'},
  {$unset: {'age': ''}}
);
```
This command updates the document with the field `name` equal to `'Subham'` in the `contacts` collection and removes the `age` field from the document.

c) Deleting documents in MongoDB:

Syntax: `db.collection_name.deleteOne(filter)` and `db.collection_name.deleteMany(filter)`

Example: Delete Subham's record from the 'contacts' collection.
```javascript
db.contacts.deleteOne(
  {'name': 'Subham'}
);
```
This command deletes a single document with the field `name` equal to `'Subham'` from the `contacts` collection.

Example: Delete multiple records of Subham from the 'contacts' collection.
```javascript
db.contacts.deleteMany(
  {'name': 'Subham'}
);
```
This command deletes multiple documents with the field `name` equal to `'Subham'` from the `contacts` collection.

## 2.MongoDB Filterization Techniques:

a) Basic filtering:
Syntax: `db.collection_name.find(filter).pretty()`

Example: Display the contacts whose name is Subham.
```javascript
db.contacts.find({'name': 'Subham'}).pretty();
```
This command retrieves and displays all the documents from the `contacts` collection with the field `name` equal to `'Subham'`.

Example: Using the $eq operator to find contacts with name 'Ananya'.
```javascript
db.contacts.find({'name': {$eq: 'Ananya'}});
```
This command retrieves and displays all the documents from the `contacts` collection with the field `name` equal to `'Ananya'`.

b) Comparison operators:
- `$ne`: not equal
- `$gt`: greater than
- `$gte`: greater than or equal to
- `$lt`: lesser than
- `$lte`: lesser than or equal to

Example: Select employees with salary greater than 12k.
```javascript
db.employees.find({'sal': {$gt: 12000}});
```
This command retrieves and displays all the documents from the `employees` collection with the field `sal` greater than `12000`.

Example: Select employees with salary greater than or equal to 12k.
```javascript
db.employees.find({'sal': {$gte: 12000}});
```
This command retrieves and displays all the documents from the `employees` collection with the field `sal` greater than or equal to `12000`.

Example: Select employees with salary lesser than 12k.
```javascript
db.employees.find({'sal': {$lt: 12000}});
```
This command retrieves and displays all the documents from the `employees` collection with the field `sal` lesser than `12000`.

Example: Select employees with salary lesser than or equal to 12k.
```javascript
db.employees.find({'sal': {$lte: 12000}});
```
This command retrieves and displays all the documents from the `employees` collection with the field `sal` lesser than or equal to `12000`.

c) Range filtering:
Example: Select employees with salary between 12k to 14k using the `$and` operator.
```javascript
db.employees.find({
  $and: [
    {'sal': {$gte: 12000}},
    {'sal': {$lte: 14000}}
  ]
});
```
This command retrieves and displays all the documents from the `employees` collection with the field `sal` greater than or equal to `12000` and less than or equal to `14000`.

Example: Select employees with salary not between 12k to 14k.
```javascript
db.employees.find({
  $or: [
    {'sal': {$lt: 12000}},
    {'sal': {$gt: 14000}}
  ]
});
```
This command retrieves and displays all the documents from the `employees` collection with the field `sal` either less than `12000` or greater than `14000`.

These examples demonstrate the usage of various MongoDB commands. Remember to replace `collection_name` with the actual name of your collection, and adjust the field names and values according to your specific use case.
