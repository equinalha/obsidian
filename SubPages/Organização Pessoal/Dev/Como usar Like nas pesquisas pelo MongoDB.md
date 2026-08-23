---

---
```javascript
// Like no MongoDb
const name = "John"
UserSchema.find({name: {$regex: name, $options: 'i'}}).limit(5);

// Outra opção
const mongoose = require('mongoose');
const User = mongoose.model('user');

const userRegex = new RegExp(userNameVariable, 'i')
return User.find({name: userRegex})

// Ainda outra opção
var promise = UserSchema.find({name: new RegExp(req.params.keyword, 'i') }).limit(5);

// Através do aggregate
db.dbname.aggregate([{ "$match" : {"name" : { $regex: '.*SERGE.*', $options: 'i' } }}, { $sort: { "createdTime" : -1 }} ]).pretty()

```