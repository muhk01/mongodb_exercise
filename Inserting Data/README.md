# INSERTING DATA IN MONGODB

## INSERTING DATA IN MONGODB (insertone)

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
