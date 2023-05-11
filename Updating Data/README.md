# Updating Data within the Database

using ***$set*** to update data.

```
db.employees.update({"name":"John Doe"},{$set:{"name":"Jessica"}})
DeprecationWarning: Collection.update() is deprecated. Use updateOne, updateMany, or bulkWrite.
{
  acknowledged: true,
  insertedId: null,
  matchedCount: 1,
  modifiedCount: 1,
  upsertedCount: 0
}
```

check the collections data

```
exercise> db.employees.find()
[
  {
    _id: ObjectId("645d26aa481da6ba377c466e"),
    name: 'Jessica',
    age: 30,
    occupation: 'Engineer'
  },
  {
    _id: ObjectId("645d26df481da6ba377c466f"),
    name: 'John Doe',
    age: 35,
    email: 'john.doe@example.com'
  },
  {
    _id: ObjectId("645d26df481da6ba377c4670"),
    name: 'Jane Smith',
    age: 30,
    address: {
      street: '123 Main St',
      city: 'New York',
      state: 'NY',
      zipcode: '10001'
    }
  },
  {
    _id: ObjectId("645d26df481da6ba377c4671"),
    username: 'bob_johnson',
    password: 'password123',
    name: { first: 'Bob', last: 'Johnson' },
    email: 'bob.johnson@example.com',
    phone: '555-555-5555'
  }
]
```
