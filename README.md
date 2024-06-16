# mongodb_task

1.Find all the information about each products
db.collection.find({})
![alt text](image.png)

2.Find the product price which are between 400 to 800
db.collection.find({ product_price: { $gte: 400, $lte: 800 }})
![alt text](image-1.png)


3.Find the product price which are not between 400 to 600
db.collection.find({ product_price: { "$not": { $gte: 400, $lte: 800 } }})
![alt text](image-2.png)

4.List the four product which are grater than 500 in price
db.collection.find({"product_price": {"$gte": 500}}).limit(4)
![alt text](image-3.png)

5.Find the product name and product material of each products
db.collection.find({},{ product_name: 1, product_material: 1})
![alt text](image-4.png)

6.Find the product with a row id of 10
db.collection.find({id: "10"})
![alt text](image-6.png)

7.Find only the product name and product material
db.collection.find({},{ product_name: 1, product_material: 1})
![alt text](image-5.png)

8.Find all products which contain the value of soft in product material
db.collection.find({product_material: { "$eq": "Soft" }})
![alt text](image-7.png)

9.Find products which contain product color indigo and product price 492.00
db.collection.find({ "$or": [{product_color: "indigo" },{product_price: 492.00 }]})
![alt text](image-8.png)

10.Delete the products which product price value are same
db.collection.aggregate([ { "$group": { "_id": { product_price: "$product_price" }, total: { $sum: 1 } } }, { $match: { total: { $gt: 1 } } } ]).map(val=> db.collection.deleteMany({"product_price": val._id.product_price}))
![alt text](image-9.png)