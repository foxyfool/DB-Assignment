# DB-Assignment

Table 1 
Product : 
id(int)
name(varchar)
desc(text)
SKU(varchar)
category_id(int)
inventory_id(int)
price(decimal)
discount_id(int)
created_at(timestamp) - the date and the time the product was created 
modified_at(timestamp) - the date and the time the product was last modified 
deleted_at(timestamp) - the date and the time the product was deleted

Table 2 
Product Category : 
id(int) - unique identifier for product category 
name(varchar) - the name of the product category 
desc(text) - A description of the product category 
created_at(timestamp) - the date and the time the product category was created 
modified_at(timestamp) - the date and the time the product category was last modified 
deleted_at(timestamp) - the date and the time the product category was deleted

Q1.>> The relationship between Product & Product Category entities from the above table or the given diagram can be explained as the category_id field in the product table is a foreign key that references the id(int) in the product category table(2) which creates an one to many relationship between the product categories and the product table which concludes that a product category can have many products but a product can only belong to one category.

Q2.>> To ensure that each product in the Product(Table1) has a valid category assigned to it we will need to check the DB constraints first :
1. The category_id coloumn in the Product (Table1) as a foreign key referencing the id coloumn of the Product Category Table which forces the referencial integrity and prevents insertion of a product with a category_id that does not exist in your list of valid categories.
2. We can also make the category_id coloumn in the Product (Table1) as NOT_NULL 
Apart from this we can also do a form validation (gathering the required inputs when the user inserts data into the table and matching it with the data type like int varchar etc...) OR

Backend validation like : 
const Product = require('./loaction')
const ProductCategory = require("./loacation")
async function CreateProduct (req,res) {
const validCategory = req.body.category_id;
const isValidCategory = await.ProductCategory.exists({_id: category_id})
if(!isValidCategory){
return res.status(400).json({error: "Invalid Category id"})
}
}


--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------




