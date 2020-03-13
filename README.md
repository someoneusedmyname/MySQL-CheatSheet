# MySQL-CheatSheet

## Login
```
mysql -u root -p
```
## Show Users
```
SELECT User, Host FROM mysql.user;
```
## Create User
```
CREATE USER 'username'@'localhost' IDENTIFIED BY 'yourpassword';
```
## Grant All Priveleges On All Databases
```
GRANT ALL PRIVILEGES ON * . * TO 'someuser'@'localhost';
FLUSH PRIVILEGES;
```
## Show Grants
```
SHOW GRANTS FOR 'username'@'localhost';
```
## Remove Grants
```
REVOKE ALL PRIVILEGES, GRANT OPTION FROM 'username'@'localhost';
```
## Show Tables
```
SHOW TABLES;
```
## Create Table
```
CREATE TABLE users(
id INT AUTO_INCREMENT,
   first_name VARCHAR(50),
   last_name VARCHAR(50),
   email VARCHAR(50),
   password VARCHAR(25),
   register_date DATETIME,
   PRIMARY KEY(id)
);
```
## Delete / Drop Table
```
DROP TABLE tablename;
```
## Insert Row
```
INSERT INTO users (first_name, last_name, email, password, register_date) 
values ('Jack', 'Pack', 'jetpackjack@gmail.com', 'crappypassword', now());
```
## Insert Multiple Rows
```
INSERT INTO users (first_name, last_name, email, password, register_date) 
values ('Harry', 'Sachel', 'harry_sach@hotmail.com', 'lamepassword', now()), ('Frank', 'Furter', 'winerguy@gmail.com', 'sausage', now());
```
## Where Clause
```
SELECT * FROM users WHERE first_name='Frank';
```
## Where Clause with range
```
SELECT * FROM users
WHERE id BETWEEN 10 AND 20
```
## Delete Row
```
DELETE FROM users WHERE id = 1;
```
## Update Row
```
UPDATE users SET email = 'wienerguy@gmail.com' WHERE id = 2;
```
## Add New Column
```
ALTER TABLE users ADD age VARCHAR(3);
```
## Modify Column
```
ALTER TABLE users MODIFY COLUMN age INT(3);
```
## Order By (Sort)
```
SELECT * FROM users ORDER BY last_name ASC;
SELECT * FROM users ORDER BY last_name DESC;
```
## Select Distinct Rows
```
SELECT DISTINCT last_name FROM users;
```
## Concatenate Columns
```
SELECT CONCAT(first_name, ' ', last_name) AS 'Name', dept FROM users;
```
## Like Search
```
SELECT * FROM users WHERE last_name LIKE 'f%';
SELECT * FROM users WHERE last_name LIKE 'fur%';
SELECT * FROM users WHERE last_name LIKE '%r';
SELECT * FROM users WHERE last_name LIKE '%t%';
```
## IN
```
SELECT * FROM users WHERE age IN ('65');
```
## Create
```
CREATE INDEX LIndex On users(age);
```
## Remove Index
```
DROP INDEX LIndex ON users;
```
## New Table With Foreign Key
```
CREATE TABLE posts(
id INT AUTO_INCREMENT,
   user_id INT,
   title VARCHAR(50),
   body TEXT,
   publish_date DATETIME DEFAULT CURRENT_TIMESTAMP,
   PRIMARY KEY(id),
   FOREIGN KEY (user_id) REFERENCES users(id)
);
```
## INNER JOIN
```
SELECT
  users.first_name,
  users.last_name,
  blog.title,
  blog.publish_date
FROM users
INNER JOIN blog
ON users.id = blog.user_id
ORDER BY blog.title;
```
## Join Multiple Tables
```
SELECT
comments.body,
blog.title,
users.first_name,
users.last_name
FROM comments
INNER JOIN blog on blog.id = comments.post_id
INNER JOIN users on users.id = comments.user_id
ORDER BY posts.title;
```
