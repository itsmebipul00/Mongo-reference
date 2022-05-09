# Mongo-reference

db -> collection -> document

db.users.insetOne({name: "Bipul"})

db.users.find().sort({name: -1}).limit(2)

db.users.find().sort({age: -1, name: -1}).limit(3) //sort by age in rev order(99->0) if same age then sort by name in rev order

like where in sql
db.users.find({age: 21}) //unlike js find it returns all users whose age is 26

like select in sql
db.users.find({name: "Bipul"}, {name: 1, age: 1, _id: 0})

db.users.find({name: "Bipul"}, {age: 0})

mongoose -> Schema, query, model
we can add methods, validations, queries , virtuals and middlewares to the schema

userSchema.methods.sayHi = function(){
 clg (`HI ${this.name}`)
} //used on instances


userSchema.methods.findByName = function(){
 return this.find({name: new RegExp(name, 'i')})
} //used on models


userSchema.methods.byName = function(){
 return this.where({name: new RegExp(name, 'i')})
} // chained on methods in models


userSchema.virtual("namedEmail").get(function(){
 return `${this.name}`
} )// only in code not saved in db


middleware 

userschema.pre('save', function(next){
  this.updatedAt = Date.now()
  next()
})

//cant use this, as it passes the doc that is saved
userSchema.post('save', function(doc, next){
  doc.sayHi()
next()
})


https://github.com/akashshyamdev/mongoose-query-methods-cheatsheet

https://drive.google.com/file/d/1ZEcnJi6oglVQ5qkVnumYdPXvyVHBk7Ck/view?usp=sharing

https://mongoosejs.com/docs/queries.html
