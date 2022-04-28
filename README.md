# MongoDB Cheat Sheet

### Create New Database
```
use <new db name>
```

### Check Current Databse
```
db
```

# CRUD - An acronym for the fundamental operations of a database: Create, Read, Update, and Delete. 

## <ins> Create Operation </ins>

### Create One Document - 
```
db.collection.insertOne(
    {
        name: "John Doe",
        age : 20,
        gender: 'M'
    }
)
```

### Create Many Document - (data should be in form of LIST)
```
db.collection.insertMany(
    [
        {
            name: "Sam",
            age : 20,
            gender: 'M'
        },
        {
            name: "John",
            age : 25,
            gender: 'M'
        },
        {
            name: "Doe",
            age : 30,
            gender: 'M'
        }
    ]
)
```

## <ins> Read Operation </ins>

### Read all Data
```
db.collection.find()
```

### Read Data with Conditions
```
db.collection.find({
    age: {$gt: 20}
})
```

### Read Data with Limit
```
db.collection.find({
    age: {$gt: 20}
}).limit(2)
```

## <ins> Update Operation </ins>

### Update One Document
```
db.collection.updateOne(
   { _id: ObjectId('<id>')},
   {
     $set: {name: 'John Wick'}
   }
)
```

### Update Many Documents
```
db.collection.updateMany(
   { age:{$gt:20}},
   {
     $set: {name: 'John Wick', age:30}
   }
)
```

### Replace Document
```
db.collection.replaceOne(
   {age:30},
   {name:'John Wick', age:50, gender:'M'}
)
```

#### Note - Since replaceOne() replaces the entire document - fields in the old document not contained in the new will be lost. With updateOne() new fields can be added without losing the fields in the old document.
<br>

## <ins> Delete Operation </ins>

### Delete One Document
```
db.collection.deleteOne(
    {_id: ObjectId("<id>") }
)
```

### Delete Many Documents
```
db.collection.deleteMany(
    {age: 50}
)
```

## Notes :

### BSON - BSON is just binary JSON (a superset of JSON with some more data types, most importantly binary byte array). It is a serialization format used in MongoDB.
<br>

### CAP Theorem
Given three properties of computing systems, consistency, availability, and partition tolerance, a distributed computing system can provide any two of these features, but never all three.
<br>

 
### SQL to MongoDB Mapping Chart
<img src="https://github.com/ksalokya/mondodb_mongoose_crud/blob/main/table.png" />

#### For more visit - https://www.mongodb.com/docs/manual/reference/sql-comparison/


