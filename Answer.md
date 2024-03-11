1. Explain the relationship between the "Product" and "Product_Category" entities from the above diagram.
Ans: Product Entity: This entity represents individual products. Each product has attributes such as product name, price,category_id,inventory_id etc.
     Product_Category Entity: This entity represents categories or groups to which products belong. Each category has attributes such as category ID,name, description, etc.

     Now, in terms of their relationship:

   The "Product_Category" table serves as a reference for  "Product" table links individual products to their respective categories through the use of foreign key relationships.
     
2. How could you ensure that each product in the "Product" table has a valid category assigned to it?
   Ans: To ensure that each product in the "Product" table has a valid category assigned to it, you can implement the following measures:

       Foreign Key Constraint: Define a foreign key constraint on the "category_id" column in the "Product" table, referencing the "id" column in the "Product_Category" table.
       This constraint ensures referential integrity, meaning that every value in the "category_id" column of the "Product" table must match a valid "id" value
       in the "Product_Category" table.

                  E.g        ALTER TABLE Product
                             ADD CONSTRAINT fk_product_category
                             FOREIGN KEY (category_id)
                             REFERENCES Product_Category(id);
   
        Database Triggers: Implement database triggers to enforce data integrity rules. For example, you can create a trigger that fires before inserting or updating a row
        in the "Product" table. This trigger can check whether the provided "category_id" value exists in the "Product_Category" table. If not, it can raise an error or
         take appropriate action to prevent the operation from completing.

        Application-Level Validation: Implement validation logic in your application code to ensure that each product added or updated includes a valid category ID.
         Before inserting or updating a product record in the database, the application can query the "Product_Category" table to verify the existence of the
         specified category ID. If the category ID is invalid, the application can reject the operation and provide feedback to the user.

   
