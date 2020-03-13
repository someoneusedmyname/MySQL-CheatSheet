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
CREATE USER 'someuser'@'localhost' IDENTIFIED BY 'somepassword';
```
