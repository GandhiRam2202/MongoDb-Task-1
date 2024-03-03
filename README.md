# MongoDB Day 1
## 1.Find all the information about each products

### Ans : db.products.find();

## 2.Find the product price which are between 400 to 800

### Ans : db.products.find({'product_price': {$gte: 400, $lte: 800}});

## 3.Find the product price which are not between 400 to 600

### Ans : db.products.find({$or: [{ 'product_price': { $lt: 400 } },{ 'product_price': { $gt: 600 } }]});

## 4.List the four product which are greater than 500 in price 

### Ans : db.products.find({'product_price':{$gt:500}}).limit(4);

## 5.Find the product name and product material of each products

### Ans : db.products.find({}, {'_id':0, 'product_name': 1, 'product_material': 1 });

## 6.Find the product with a row id of 10

### Ans : db.products.find().skip(9).limit(1);

## 7.Find only the product name and product material

### Ans : db.products.find({}, {'_id':0, 'product_name': 1, 'product_material': 1 });

## 8.Find all products which contain the value of soft in product material 

### Ans : db.products.find({ 'product_material': 'Soft' });

## 9.Find products which contain product color indigo  and product price 492.00

### Ans : db.products.find({ 'product_color': 'indigo' , 'product_price': 492.00 });

## 10.Delete the products which product price value are same

### Ans :  
let Prices = db.products.distinct("product_price");

Prices.forEach(price => {

    let product = db.products.find({ product_price: price }).sort({ _id: 1 }).skip(1); 
    
    product.forEach(doc => {
    
        db.products.deleteOne({ _id: doc._id });
        
    });
    
});

