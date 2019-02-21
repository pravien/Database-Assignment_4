# Database-Assignment_4
## Exercise 1 - user privileges
### **SQL Queries**
```sql
DROP USER IF EXISTS InventoryUser;
DROP USER IF EXISTS BookkeepingUser;
DROP USER IF EXISTS HRUser;
DROP USER IF EXISTS SalesUser;
DROP USER IF EXISTS ITUser;

CREATE USER 'InventoryUser'@'localhost' IDENTIFIED BY "1234";
CREATE USER 'BookkeepingUser'@'localhost' IDENTIFIED BY "1234";
CREATE USER 'HRUser'@'localhost' IDENTIFIED BY "1234";
CREATE USER 'SalesUser'@'localhost' IDENTIFIED BY "1234";
CREATE USER 'ITUser'@'localhost' IDENTIFIED BY "1234";

GRANT SELECT, INSERT, UPDATE, DELETE ON classicmodels.products TO InventoryUser@localhost;
GRANT SELECT, INSERT, UPDATE, DELETE ON classicmodels.productlines TO InventoryUser@localhost;
GRANT SELECT ON classicmodels.orders TO BookkeepingUser@localhost;
GRANT SELECT, INSERT, UPDATE, DELETE ON classicmodels.employees TO HRUser@localhost;
GRANT SELECT, INSERT, UPDATE, DELETE ON classicmodels.offices TO HRUser@localhost;
GRANT INSERT ON classicmodels.orders TO SalesUser@localhost;
GRANT SELECT, INSERT, UPDATE, DELETE, GRANT OPTION ON classicmodels.* TO ITUser@localhost;

FLUSH privileges;
```
---
* *InventoryUser* – This user needs to be able to *maintain* the two tables **products** and **productlines**, and we determined the CRUD rights would be sufficient
* *BookkeepingUser* – The Bookkeeping user needs to *make sure that orders are paid*, which can be accomplished by simple SELECT rights.
* *HRUser* – The Human Resources user *take care of* **employees** and their **offices**, so CRUD rights are enough to fulfill this requirement.
* *SalesUser* – This user *creates orders* for the customers, which most likely only involves inserting new orders into the **orders** table.
* *ITUser* – The role of the IT User is to *maintain the database*, so CRUD rights and the ability to grant permissions seem enough.

## Exercise 2 - logging
### SQL Queries
```sql
INSERT INTO classicmodels.employees VALUES (13370, "Knudsen", "Knud", "x1337", "email@email.email", 1, 1002, "Administrator of Sales");
INSERT INTO classicmodels.employees VALUES (13360, "Børgesen", "Børge", "x1336", "email@email2.email", 1, 1002, "Sales Assistant");
INSERT INTO classicmodels.products VALUES ("1337", "l33t", "Trains", "100:1", "Min Lin Diecast", "herp", 3, 70034234.60, 1000);
INSERT INTO classicmodels.orders VALUES (1337, "2003-01-10", "2003-01-17", "2003-01-15", "Shipped", null, 128)
