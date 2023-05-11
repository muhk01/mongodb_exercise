
# Re arrange Column of Unstructured Data

Insert new collections

```
 db.employee_details.insertMany([{
...   "_id": ObjectId("60a9b8028a4d460001ab1c1c"),
...   "name": "Alice",
...   "age": 28,
...   "location": {
...     "city": "New York",
...     "state": "NY"
...   },
...   "job": {
...     "title": "Software Engineer",
...     "company": "ABC Inc."
...   }
... },
... {
...   "_id": ObjectId("60a9b8168a4d460001ab1c1d"),
...   "firstName": "Bob",
...   "lastName": "Smith",
...   "email": "bob.smith@example.com",
...   "address": {
...     "street": "123 Main St",
...     "city": "Los Angeles",
...     "state": "CA",
...     "zip": "90001"
...   },
...   "phoneNumbers": [
...     {
...       "type": "home",
...       "number": "555-1234"
...     },
...     {
...       "type": "work",
...       "number": "555-5678"
...     }
...   ]
... }])
{
  acknowledged: true,
  insertedIds: {
    '0': ObjectId("60a9b8028a4d460001ab1c1c"),
    '1': ObjectId("60a9b8168a4d460001ab1c1d")
  }
}
```
Using ***$project*** to re arrange column for each data since it is unstructured.

```
db.employee_details.aggregate([
  {
    $project: {
      _id: 0,
      name: { $ifNull: [ "$name", { $concat: [ "$firstName", " ", "$lastName" ] } ] },
      age: { $ifNull: [ "$age", null ] },
      city: { $ifNull: [ "$location.city", "$address.city" ] },
      state: { $ifNull: [ "$location.state", "$address.state" ] },
      jobTitle: { $ifNull: [ "$job.title", null ] },
      company: { $ifNull: [ "$job.company", null ] },
      firstName: { $ifNull: [ "$firstName", null ] },
      lastName: { $ifNull: [ "$lastName", null ] },
      email: { $ifNull: [ "$email", null ] },
      street: { $ifNull: [ "$address.street", null ] },
      zip: { $ifNull: [ "$address.zip", null ] },
      homePhone: { $ifNull: [ { $arrayElemAt: [ "$phoneNumbers.number", 0 ] }, null ] },
      workPhone: { $ifNull: [ { $arrayElemAt: [ "$phoneNumbers.number", 1 ] }, null ] }
    }
  }
])
```

and will return this following result
```
[
  {
    name: 'Alice',
    age: 28,
    city: 'New York',
    state: 'NY',
    jobTitle: 'Software Engineer',
    company: 'ABC Inc.',
    firstName: null,
    lastName: null,
    email: null,
    street: null,
    zip: null,
    homePhone: null,
    workPhone: null
  },
  {
    name: 'Bob Smith',
    age: null,
    city: 'Los Angeles',
    state: 'CA',
    jobTitle: null,
    company: null,
    firstName: 'Bob',
    lastName: 'Smith',
    email: 'bob.smith@example.com',
    street: '123 Main St',
    zip: '90001',
    homePhone: '555-1234',
    workPhone: '555-5678'
  }
]
```
the output is hardcoded to return the first two records for each column based on their corresponding column name. This is just one way to structure the output, 
and the actual implementation may vary depending on the specific requirements of the project. However, the basic idea is to use the ***$project*** aggregation stage to reshape the data into the desired structure.
