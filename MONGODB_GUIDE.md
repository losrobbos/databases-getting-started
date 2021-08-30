# MongoDB

Following find helpful instructions for getting started with MongoDB.

## Database Setup / Installation

### MongoDB in the Cloud with ATLAS

We wanna create a MongoDB Database in the Cloud.

Go to the MongoDB Atlas Page:
https://www.mongodb.com/cloud/atlas

- Signup for free
  - Fill out register form with a reachable email (you need to verify your account)

- Create a Cluster (will take some minutes to complete)

- Setup a user
  - necessary for remote connection
  - please use for the same "string" for username and password 
      -> e.g. username: user123 and password: user123
      -> makes it much easier to test

- Setup Network Access > IP Whitelist > Access from everywhere

<!--
- Connect to your Atlas DB using Compass 
  - Go to tab "Connect"
  - Grab the connection string specific for Compass
  - Launch Compass and paste the string into the connection field 
  - Create a collection and fill in a document
  - Check in Atlas if you can see the created data (tab "Collections")
-->

Video Guide for the steps above (optional): https://www.youtube.com/watch?v=KKyag6t98g8



### MongoDB local installation

#### Linux / Ubuntu

Check first if mongo db is already installed

`mongod --version`

If not - we can now start the installation.

Please do NOT right away do the following: `sudo apt install mongodb`. This will maybe install an quite outdated version of MongoDB of the official Ubuntu package repository.

First let's check which MongoDB version is available for us:

`sudo apt policy mongodb`

This should give some output like this:

```
mongodb:
  Installed: (none)
  Candidate: 1:3.6.3-0ubuntu1.1
  ...
```

In case you got a version 3.6 or above as your "Candidate 1:" that should be fine with our lectures. You can now do `sudo apt install mongodb`

In case you got a version LESS THAN 3.6 listed here, it is highly recommended installing a MongoDB version from the official repository (see below). This way it will be assured that you can use all the code  we are going to show in the lectures.

##### Install Official MongoDB version

Follow the official guide to install the current stable version:

https://docs.mongodb.com/manual/tutorial/install-mongodb-on-ubuntu/#install-mongodb-community-edition

In Step 2 ("Create a list file") you do not need to create this file in your file explorer. Just execute the command given at the end of the section (the one starting with 'echo "deb [...'). Click the "Copy" button to grab that line and paste it into a terminal with CTRL+SHIFT+V. And then hit enter.

Afterwards try to startup the MongoDB service with the provided instructions.

Once you can successfully run the command "mongo" in the terminal and it runs without error, you have done it!

After you run "mongo" you will be in the so called "Mongo Shell". Here you can execute commands against the database. To quit simply type "exit" and hitting Enter or just type CTRL+C.


##### Troubleshooting

You just installed MongoDB, but running "mongo" to test the connection gives you an error? 

First check if MongoDB is correctly installed:

`mongod --version`

If that is the case: Check if the mongod service is running:

`sudo systemctl status mongod.service`

Is it not running?

Startup the Mongo Service:

`sudo systemctl start mongod.service`

And also activate it to run on boot:

`sudo systemctl enable mongod.service`

Check the status again:

`sudo systemctl status mongod.service`

If the Mongo service fails to startup (you get "inactive"), likely something during installation went wrong. Then follow below...

First check if you have actually the community version installed:

`sudo apt-cache policy mongodb-org-server | head -n3`

If the command above gives you nothing or "(none)" as value for installed, you likely have not performed all steps in the official installation guide of MongoDB (see link above) correctly, because you do not have the official version installed. Please get in touch & we check individually.

If the command above tells you, MongoDB is installed locally (and the version is above 4.0), the installation has worked, but probably write permissions on the MongoDB directory are not set correctly.

Please check where MongoDB stores its data:

`grep dbPath /etc/mongod.conf`

(normally this should give you the path /var/lib/mongodb

Now check the permissions of the parent folder:

`ls -l /var/lib | grep mongo`

That should give you something like the following:

`drwxr-xr-x  4 mongodb       mongodb       4096 Mar  9 10:02 mongodb`

If the owner of that folder is NOT the user mongodb, but root, please make mongodb the owner:

`sudo chown -R mongodb:mongodb /var/lib/mongodb`

Afterwards try to startp the service once more: 

##### Setting up an Admin user

In case you wanna protect your local MongoDB with an administrator password, you can lookup the Access Control Guide:

https://docs.mongodb.com/manual/tutorial/enable-authentication/


### Windows

https://docs.mongodb.com/manual/tutorial/install-mongodb-on-windows/


### MacOS

https://docs.mongodb.com/manual/tutorial/install-mongodb-on-os-x/#install-mongodb-community-edition



## Connect to database

We have two options to access & work with data in a database: 

- Connecting with an UI tool
- Connecting from code

### Database UI tool(s)

MongoDB Compass - An UI for managing data in a mongo database:

Installation: https://docs.mongodb.com/compass/master/install/

### Connecting from JavaScript

Mongoose Library: https://mongoosejs.com/docs/

JavaScript snippet for setting up a connection:

```
  mongoose.connect(...yourConnString..., {
    useNewUrlParser: true,
    useUnifiedTopology: true
  })
  .then(() => console.log("DB Connection successful!"))
  .catch((err) => console.log("[ERROR] DB Connection failed!", err))
```


## Terminology

- Document: A resource stored in the DB, e.g. a "user". Documents are very similar to JavaScript objects.
- Field: An attribute of a document, e.g. the "name" of a user
- Collection: An "array" of documents of the same type. E.g. the "users" collection containing all users of our database
- ObjectID: The unique ID format / datatype MongoDB uses to identify each record / document in the database. An ObjectID is unique in the WHOLE database, not just in a collection.
- Model: A "data manager" for one resource. E.g. a User model manages users in the database. So you can use a model to perform creation, filtering, updating & deleting of user data. You can think about the model as a "super-charged" array, that - instead of providing "normal" array methods for data querying & manipulating - offers special array methods to query & manipulate data directly in a database! Every model has a schema attached to it. So the model will validate the rules in the schema for all operations to decide if the operation is permitted or not.
- Schema: Set of rules any valid document in a collection must fulfill. the schema defines which fields required, what datatypes the fields must be, etc. For example a "email" field of the user should be a string, is required, same for the password field. But the field "username" is optional.

## Schema Field Datatypes

Find following a list of all datatypes a field in MongoDB can have:

https://www.tutorialspoint.com/mongodb/mongodb_datatype.htm

<!-- https://3.bp.blogspot.com/-AJekhXzsT7g/W_F-KYEfZEI/AAAAAAAAB1M/
62-rfvLLJyQZC_a8QwR7FK9jE1C9ffgZACLcBGAs/s1600/image1.png -->


## Online Query Training tool

MongoDB playground: https://mongoplayground.net/

Here you can safely try out common DB CRUD operations without having to deal with the hassle of installing an own Mongo database.


### Command Cheatsheet

Find following some cheat sheets for common DB operations (for usage in Online training tool or in the terminal):

MongoDB Cheatsheet:
https://github.com/azat-co/cheatsheets/blob/master/mongodb-mongoose/readme.md

See section "MongoDB console". Do NOT click the PDF - that's a paid version :) 



