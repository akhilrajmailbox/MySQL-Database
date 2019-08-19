# databases


## MySQL Migration Scripts

[backup script](https://raw.githubusercontent.com/akhilrajmailbox/MySQL-Database/master/scripts/Bakup_MySQL.sh)

[import script](https://raw.githubusercontent.com/akhilrajmailbox/MySQL-Database/master/scripts/Import_MySQL.sh)


## basic queries

to find sock::

```
netstat -ln | grep -o -m 1 -E '\S*mysqld?\.sock'
```
Example :

```
$ netstat -ln | grep -o -m 1 -E '\S*mysqld?\.sock'
/var/run/mysqld/mysqld.sock
```


[link 1](https://www.digitalocean.com/community/tutorials/how-to-create-a-new-user-and-grant-permissions-in-mysql)

[link 2](http://www.wikihow.com/Create-a-Database-in-MySQL)


### making a new user within the MySQL shell :

```
CREATE USER 'newuser'@'localhost' IDENTIFIED BY 'password';
```

### give all grand to root user from remote system :

```
GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' IDENTIFIED BY 'root-passwd' WITH GRANT OPTION;
FLUSH PRIVILEGES;
```

### provide the user with access to the information they will need :

```
GRANT ALL PRIVILEGES ON * . * TO 'newuser'@'localhost';
```

### updating :

```
UPDATE mysql.user SET Host='%' WHERE Host='localhost' AND User='root';
```

### change the root password :

```
mysqladmin -u root password newpasswd -poldpasswd
```

### reload all the privileges :

```
FLUSH PRIVILEGES;
```

### User query :

```
select User,Host from mysql.user;
```

### dumping :

```
mysqldump -u root redmine_default > redmine_default.sql -p
```

### exporting to database from name.sql file :

```
mysql -h host -u user -p -D redmine_default < redmine_default.sql
```

### to see the  database, tables or column :

```
mysqlshow -h host -u user -ppassword database tablename column
```

### to see the grants for a user :

```
show grants for username;
```

### revoke permission :

```
revoke usage on database.* from 'user'@'%';
```

### giving readonly permission for a user to database :

```
grant LOCK TABLES,select on database.* to 'user'@'%';
```

