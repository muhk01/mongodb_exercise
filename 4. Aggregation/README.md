# Simple Aggregation

Create new Collections

```
exercise> db.employees_dept.insertMany([{
...   "_id": 1,
...   "name": {
...     "first": "John",
...     "last": "Doe"
...   },
...   "age": 25,
...   "salary": 50000,
...   "department": "Sales",
...   "address": {
...     "street": "123 Main St",
...     "city": "New York",
...     "state": "NY",
...     "zip": "10001"
...   }
... },
... {
...   "_id": 2,
...   "name": "Jane Smith",
...   "age": 30,
...   "salary": 75000,
...   "department": "Marketing",
...   "address": {
...     "street": "456 Broadway",
...     "city": "Boston",
...     "state": "MA",
...     "zip": "02108"
...   }
... },
... {
...   "_id": 3,
...   "name": {
...     "first": "Bob",
...     "last": "Johnson"
...   },
...   "age": 35,
...   "salary": 60000,
...   "department": "Sales",
...   "address": "789 Market St, San Francisco, CA 94103"
... }])
```

Find Average Salary in Department and order Descending

***Aggregate** and use ***$group*** used to group data in some categorical columns, then ***$sort*** in descending order.

```
db.employees_dept.aggregate([
	{$group: 
		{_id: "$department", 
		averageSalary: {$avg: "$salary"}} },
	{$sort: {averageSalary: -1}}
])
[
  { _id: 'Marketing', averageSalary: 75000 },
  { _id: 'Sales', averageSalary: 55000 }
]
```


