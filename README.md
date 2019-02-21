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
