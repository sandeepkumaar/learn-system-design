## Partition - Clustering Columns - Unique key(primary)

In Cassandra, Primary Key which is a combination of 
- Partition key (required)
- Clustering key (optional)
- Unique key  (required)

The above keys are very important while creating a table. because cassandra uses this information to effectively query our data.

> Note: Cassandra for performance reasons dont allow queries which does not leverage the above keys. In those cases, you need to 
> drop and recreate the collection/ALTER? or handle it at the client side
> This also makes Cassandra special, because we cannot do anything thats affecting performance, making the developers have the 
> entire idea on how data should be organised rather than leaving it for later.


Query: 
```
CREATE TABLE
state, 
city,
name
PRIMARY KEY ((state), city, name);
```

### PRIMARY KEY ((state), city, name);
- state -> partition key
- city, name -> clustering columns (sorted)
all together state + city + name -> should form a primary/unique key (otherwise cassandra will overwrite the records)


Partition key is used to partition the data into different nodes. It should logically represent a group of data.
Cassandra makes Partition key mandatory - so it knows which node to reach for the given query. 
For the same reason, cassandra forces us to use the **`partitionkey` in every query !** to prevent lookup on other nodes.
This will raise many questions like flexibility - we will look at the work arounds/design models suggested by cassandra.

Clustering Column/key: 
Clustering columns or keys are basically used for order the data by that key. This is useful for cassandra to leverage
Binary search algo - to find the data quickly. 
To ensure this, Cassandra expects us to provide our query in the **same order as the clustering key order defined**



### Query rules: 
- Each query should have **partition key**
- Clustering columns follows after partitionkey, order of clustering column in the query shouldn't change
- Operations like `=`, `<>` are allowed within the partition. not outside the partition
- Equality comparisons must come before inequality comparisions

