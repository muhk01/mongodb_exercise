# Basic Simple Query

## Searching one data and one parameters (findOne)

Searching employees named "John Doe"
```
exercise> db.employees.findOne({"name":"John Doe"})
{
  _id: ObjectId("645d26df481da6ba377c466f"),
  name: 'John Doe',
  age: 35,
  email: 'john.doe@example.com'
}
```
## Searching one data and multiple parameters (findOne)

Searching employees named "John Doe" and age is equal to 30

```
exercise> db.employees.findOne({ $and: [ { age: { $eq: 35 } }, { name: "John Doe" }] })
[
  {
    _id: ObjectId("645d26df481da6ba377c466f"),
    name: 'John Doe',
    age: 35,
    email: 'john.doe@example.com'
  }
]
```
## Searching multiple data and multiple parameters (find)

Searching employees aged >= 20 and aged <= 40

```
db.employees.find({ $and: [ { age: { $gte: 20 } }, { age: {$lte: 40 } }] })
[
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
  }
]
```

# List Comparison Operator in MongoDB

```
comparison operators in NoSQL (specifically in MongoDB):

$eq: This operator stands for "equals" and is used to compare if the specified value is equal to the value in a document field.
Example: db.collection.find({ age: { $eq: 25 } })

$ne: This operator stands for "not equals" and is used to compare if the specified value is not equal to the value in a document field.
Example: db.collection.find({ age: { $ne: 25 } })

$gt: This operator stands for "greater than" and is used to compare if the value in a document field is greater than the specified value.
Example: db.collection.find({ age: { $gt: 25 } })

$lt: This operator stands for "less than" and is used to compare if the value in a document field is less than the specified value.
Example: db.collection.find({ age: { $lt: 25 } })

$in: This operator is used to select documents where the value of a field matches any of the specified values.
Example: db.collection.find({ age: { $in: [25, 30, 35] } })

$nin: This operator is used to select documents where the value of a field does not match any of the specified values.
```

