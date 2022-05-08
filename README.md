# Mongo-reference

db -> collection -> document

db.users.insetOne({name: "Bipul"})

db.users.find().sort({name: -1}).limit(2)

db.users.find().sort({age: -1, name: -1}).limit(3) //sort by age in rev order(99->0) if same age then sort by name in rev order

like where in sql
db.users.find({age: 21}) //unlike js find it returns all users whose age is 26

db.users.find({name: "Bipul"}, {name: 1, age: 1, _id: 0})

db.users.find({name: "Bipul"}, {age: 0})
