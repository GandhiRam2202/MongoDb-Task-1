# MongoDB Day 1
## 1.Find all the information about each products

### Ans : db.products.find();

### Output : 

{
  _id: ObjectId('65e37384a9e2145934538821'),
  id: '1',
  product_name: 'Intelligent Fresh Chips',
  product_price: 655,
  product_material: 'Concrete',
  product_color: 'mint green'
}
{
  _id: ObjectId('65e37384a9e2145934538822'),
  id: '2',
  product_name: 'Practical Fresh Sausages',
  product_price: 911,
  product_material: 'Cotton',
  product_color: 'indigo'
}
{
  _id: ObjectId('65e37384a9e2145934538823'),
  id: '3',
  product_name: 'Refined Steel Car',
  product_price: 690,
  product_material: 'Rubber',
  product_color: 'gold'
}
{....................}
{....................}
{
  _id: ObjectId('65e37384a9e2145934538839'),
  id: '25',
  product_name: 'Licensed Steel Car',
  product_price: 20,
  product_material: 'Cotton',
  product_color: 'indigo'
}

...... 25 Products


## 2.Find the product price which are between 400 to 800

### Ans : db.products.find({'product_price': {$gte: 400, $lte: 800}});

### Output:

{
  _id: ObjectId('65e37384a9e2145934538821'),
  id: '1',
  product_name: 'Intelligent Fresh Chips',
  product_price: 655,
  product_material: 'Concrete',
  product_color: 'mint green'
}
{
  _id: ObjectId('65e37384a9e2145934538823'),
  id: '3',
  product_name: 'Refined Steel Car',
  product_price: 690,
  product_material: 'Rubber',
  product_color: 'gold'
}
{
  _id: ObjectId('65e37384a9e2145934538824'),
  id: '4',
  product_name: 'Gorgeous Plastic Pants',
  product_price: 492,
  product_material: 'Soft',
  product_color: 'plum'
}
{
  _id: ObjectId('65e37384a9e2145934538826'),
  id: '6',
  product_name: 'Awesome Wooden Towels',
  product_price: 474,
  product_material: 'Plastic',
  product_color: 'orange'
}
{
  _id: ObjectId('65e37384a9e2145934538827'),
  id: '7',
  product_name: 'Practical Soft Shoes',
  product_price: 500,
  product_material: 'Rubber',
  product_color: 'pink'
}

## 3.Find the product price which are not between 400 to 600

### Ans : db.products.find({$or: [{ 'product_price': { $lt: 400 } },{ 'product_price': { $gt: 600 } }]});

### Output:

{
  _id: ObjectId('65e37384a9e2145934538821'),
  id: '1',
  product_name: 'Intelligent Fresh Chips',
  product_price: 655,
  product_material: 'Concrete',
  product_color: 'mint green'
}
{
  _id: ObjectId('65e37384a9e2145934538822'),
  id: '2',
  product_name: 'Practical Fresh Sausages',
  product_price: 911,
  product_material: 'Cotton',
  product_color: 'indigo'
}
{
  _id: ObjectId('65e37384a9e2145934538823'),
  id: '3',
  product_name: 'Refined Steel Car',
  product_price: 690,
  product_material: 'Rubber',
  product_color: 'gold'
}
{---------}
{---------}
{---------}
{
  _id: ObjectId('65e37384a9e2145934538838'),
  id: '24',
  product_name: 'Tasty Rubber Cheese',
  product_price: 47,
  product_material: 'Frozen',
  product_color: 'orchid'
}
{
  _id: ObjectId('65e37384a9e2145934538838'),
  id: '24',
  product_name: 'Tasty Rubber Cheese',
  product_price: 47,
  product_material: 'Frozen',
  product_color: 'orchid'
}
............. 22 Products


## 4.List the four product which are greater than 500 in price 

### Ans : db.products.find({'product_price':{$gt:500}}).limit(4);

### Output:

{
  _id: ObjectId('65e37384a9e2145934538821'),
  id: '1',
  product_name: 'Intelligent Fresh Chips',
  product_price: 655,
  product_material: 'Concrete',
  product_color: 'mint green'
}
{
  _id: ObjectId('65e37384a9e2145934538822'),
  id: '2',
  product_name: 'Practical Fresh Sausages',
  product_price: 911,
  product_material: 'Cotton',
  product_color: 'indigo'
}
{
  _id: ObjectId('65e37384a9e2145934538823'),
  id: '3',
  product_name: 'Refined Steel Car',
  product_price: 690,
  product_material: 'Rubber',
  product_color: 'gold'
}


## 5.Find the product name and product material of each products

### Ans : db.products.find({}, {'_id':0, 'product_name': 1, 'product_material': 1 });

### Output:

{
  product_name: 'Intelligent Fresh Chips',
  product_material: 'Concrete'
}
{
  product_name: 'Practical Fresh Sausages',
  product_material: 'Cotton'
}
{
  product_name: 'Refined Steel Car',
  product_material: 'Rubber'
}
{
  product_name: 'Gorgeous Plastic Pants',
  product_material: 'Soft'
}
{
  product_name: 'Sleek Cotton Chair',
  product_material: 'Fresh'
}
{--------}
{--------}
{--------}
{--------}
{
  product_name: 'Handcrafted Wooden Bacon',
  product_material: 'Concrete'
}

............25 Products


## 6.Find the product with a row id of 10

### Ans : db.products.find().skip(9).limit(1);

### Output:

{
  _id: ObjectId('65e37384a9e214593453882a'),
  id: '10',
  product_name: 'Generic Wooden Pizza',
  product_price: 84,
  product_material: 'Frozen',
  product_color: 'indigo'
}

7.Find only the product name and product material

Ans : db.products.find({}, {'_id':0, 'product_name': 1, 'product_material': 1 });

Output:

{
  product_name: 'Intelligent Fresh Chips',
  product_material: 'Concrete'
}
{
  product_name: 'Practical Fresh Sausages',
  product_material: 'Cotton'
}
{
  product_name: 'Refined Steel Car',
  product_material: 'Rubber'
}
{
  product_name: 'Gorgeous Plastic Pants',
  product_material: 'Soft'
}
{
  product_name: 'Sleek Cotton Chair',
  product_material: 'Fresh'
}
{--------}
{--------}
{--------}
{--------}
{
  product_name: 'Handcrafted Wooden Bacon',
  product_material: 'Concrete'
}

............25 Products


## 8.Find all products which contain the value of soft in product material 

### Ans : db.products.find({ 'product_material': 'Soft' });

### Output:

{
  _id: ObjectId('65e37384a9e2145934538824'),
  id: '4',
  product_name: 'Gorgeous Plastic Pants',
  product_price: 492,
  product_material: 'Soft',
  product_color: 'plum'
}
{
  _id: ObjectId('65e37384a9e2145934538829'),
  id: '9',
  product_name: 'Awesome Wooden Ball',
  product_price: 28,
  product_material: 'Soft',
  product_color: 'azure'
}
{
  _id: ObjectId('65e37384a9e214593453882b'),
  id: '11',
  product_name: 'Unbranded Wooden Cheese',
  product_price: 26,
  product_material: 'Soft',
  product_color: 'black'
}
{
  _id: ObjectId('65e37384a9e2145934538833'),
  id: '19',
  product_name: 'Intelligent Cotton Chips',
  product_price: 46,
  product_material: 'Soft',
  product_color: 'azure'
}


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
