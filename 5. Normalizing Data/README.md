# Normalize Nested JSON Data

## Insert new Collection

```
exercise> db.sales.insertMany([{
...     "store": "A",
...     "products": [
...       {
...         "name": "Product 1",
...         "price": 22.99
...       },
...       {
...         "name": "Product 2",
...         "price": 14.99
...       }
...     ]
... },
... {
...     "store": "B",
...     "products": [
...       {
...         "name": "Product 3",
...         "price": 15.99
...       },
...       {
...         "name": "Product 4",
...         "price": 7.99
...       }
...     ]
... },
... {
...     "store": "C",
...     "products": [
...       {
...         "name": "Product 5",
...         "price": 12.99
...       },
...       {
...         "name": "Product 6",
...         "price": 8.99
...       }
...     ]
... }])
{
  acknowledged: true,
  insertedIds: {
    '0': ObjectId("645d465e481da6ba377c4675"),
    '1': ObjectId("645d465e481da6ba377c4676"),
    '2': ObjectId("645d465e481da6ba377c4677")
  }
}
```

## Normalize Data

Using ***$unwind to normalize Nested JSON**
```
exercise> db.sales.aggregate([{ $unwind: "$products"}])
[
  {
    _id: ObjectId("645d465e481da6ba377c4675"),
    store: 'A',
    products: { name: 'Product 1', price: 22.99 }
  },
  {
    _id: ObjectId("645d465e481da6ba377c4675"),
    store: 'A',
    products: { name: 'Product 2', price: 14.99 }
  },
  {
    _id: ObjectId("645d465e481da6ba377c4676"),
    store: 'B',
    products: { name: 'Product 3', price: 15.99 }
  },
  {
    _id: ObjectId("645d465e481da6ba377c4676"),
    store: 'B',
    products: { name: 'Product 4', price: 7.99 }
  },
  {
    _id: ObjectId("645d465e481da6ba377c4677"),
    store: 'C',
    products: { name: 'Product 5', price: 12.99 }
  },
  {
    _id: ObjectId("645d465e481da6ba377c4677"),
    store: 'C',
    products: { name: 'Product 6', price: 8.99 }
  }
]
```

