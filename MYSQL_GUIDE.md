# MySQL

## Online Training tool

MySQL playground: https://extendsclass.com/mysql-online.html

Here you can safely try out common DB operations without having to deal with the hassle of installing an own SQL database.

### Command Cheatsheet

Find following some cheat sheets for common DB operations.

MySQL Cheatsheet: https://devhints.io/mysql


## Terminology
	
- Table: Collection of items of the same type / structure, e.g. "users"
- Row: Data entries stored in a table. Every rows represents one unique resource, e.g. a "user"
- Column: Individual field of a row, e.g. "name" of a user
- Primary Key: Unique ID of a row within a table

## MySQL Datatypes

http://www.mysqltutorial.org/wp-content/uploads/0211/03/MySQL-Data-Types.jpg
  

## Database Setup

### MySQL local installation

#### Linux / Ubuntu

The official setup guide of MySQL is quite hard to follow and is splitted among different sub-articles until you finally can run MySQL successfully in the terminal.

A bit easier to follow are the guides from Digital Ocean, which are often kept up to date and contain all necessary setup steps.

[Install Guide - Ubuntu 20.04](https://www.digitalocean.com/community/tutorials/how-to-install-mysql-on-ubuntu-20-04)

[Install Guide - Ubuntu 18.04](https://www.digitalocean.com/community/tutorials/how-to-install-mysql-on-ubuntu-18-04)



Official MySQL Install Guide - Linux:

https://dev.mysql.com/doc/mysql-apt-repo-quick-guide/en/#apt-repo-fresh-install
(just until section "Selecting a Major Release version")

Please state a root password from the beginning and note it!

Afterwards try to run your database with "sudo mysql -u root -p <yourRootPassword>".


#### Windows

https://dev.mysql.com/doc/refman/8.0/en/windows-installation.html

#### MacOS

https://dev.mysql.com/doc/mysql-osx-excerpt/5.7/en/osx-installation-pkg.html



## Connect to database

We have two options to work the data in a database: 

- Connecting with an UI tool
- Connecting from code

### Database UI tool

With an DB UI Tool we can manage our data without any code, with an UI. 

MySQL Workbench:
- Installation: `sudo apt install mysql-workbench`


### Connecting from JavaScript

Sequelize Library (for SQL databases):

https://sequelize.org/master/manual/getting-started.html
