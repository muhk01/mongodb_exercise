# INSERTING DATA IN MONGODB

Through mongosh create new db as 'excercise'
'''
use excercise
'''

## INSERTING DATA IN MONGODB (insertone)
Inserting single record in collection in mongoDB collection is same as table in RDBMS, 

```
exercise> db.employees.insertOne({
...   name: "John Doe",
...   age: 30,
...   occupation: "Engineer"
... })
{
  acknowledged: true,
  insertedId: ObjectId("645d262b481da6ba377c466d")
}
```

## INSERTING DATA IN MONGODB (insertMany)

Inserting multiple record using insertMany. in mongoDB the collection could having different structure unlike RDBMS which has schema noSQL is Schemaless
```
db.employees.insertMany([
...   {
...     name: "John Doe",
...     age: 35,
...     email: "john.doe@example.com"
...   },
...   {
...     name: "Jane Smith",
...     age: 30,
...     address: {
...       street: "123 Main St",
...       city: "New York",
...       state: "NY",
...       zipcode: "10001"
...     }
...   },
...   {
...     username: "bob_johnson",
...     password: "password123",
...     name: {
...       first: "Bob",
...       last: "Johnson"
...     },
...     email: "bob.johnson@example.com",
...     phone: "555-555-5555"
...   }
... ])
{
  acknowledged: true,
  insertedIds: {
    '0': ObjectId("645d26df481da6ba377c466f"),
    '1': ObjectId("645d26df481da6ba377c4670"),
    '2': ObjectId("645d26df481da6ba377c4671")
  }
}
```
