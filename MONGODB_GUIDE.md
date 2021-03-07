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

- Connect to your Atlas DB using Compass 
  - Go to tab "Connect"
  - Grab the connection string specific for Compass
  - Launch Compass and paste the string into the connection field 
  - Create a collection and fill in a document
  - Check in Atlas if you can see the created data (tab "Collections")

- Video Guide (optional): https://www.youtube.com/watch?v=KKyag6t98g8


### MongoDB local installation

#### Linux / Ubuntu

Check first if mongo db is already installed

`mongod --version`

If not - we can now start the installation:

Please do NOT do the following: `sudo apt install mongodb`. This will install an likely quite outdated version of MongoDB in the official Ubuntu package repository.

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

Enable the Mongo Service if not active:

`sudo systemctl enable mongod.service`

Check the status again:

`sudo systemctl status mongod.service`

If the Mongo service fails to startup, likely something during installation went wrong. 

First check if you have actually the community version installed:

`sudo apt-cache policy mongodb-org-server | head -n3`

If the command above gives you no output, you likely have not performed all steps in the official installation guide of MongoDB (see link above) correctly, because you do not have the official version installed. Please get in touch & we need to check individually.

##### Setting up an Admin user

In case you wanna protect your local MongoDB with an administrator password, you can lookup the Access Control Guide:

https://docs.mongodb.com/manual/tutorial/enable-authentication/


### Windows

https://docs.mongodb.com/manual/tutorial/install-mongodb-on-windows/


### MacOS

https://docs.mongodb.com/manual/tutorial/install-mongodb-on-os-x/#install-mongodb-community-edition



## Connect to database

We have two options to work the data in a database: 

- Connecting with an UI tool
- Connecting from code

### Database UI tool(s)

MongoDB Compass - An UI for managing data in a mongo database:

Installation: https://docs.mongodb.com/compass/master/install/

### Connecting from JavaScript

Mongoose Library: https://mongoosejs.com/docs/


## Terminology

- Document: A resource stored in the DB, e.g. a "user"
- Field: An attribute of a document, e.g. the "name" of a user
- Collection: An "array" of documents. E.g. the "users" collection containing all users of our database
- ObjectID: The unique ID format / datatype MongoDB uses to identify each record / document in the database. An ObjectID is unique in the WHOLE database, not just in a collection.

## Field Datatypes

https://3.bp.blogspot.com/-AJekhXzsT7g/W_F-KYEfZEI/AAAAAAAAB1M/62-rfvLLJyQZC_a8QwR7FK9jE1C9ffgZACLcBGAs/s1600/image1.png



## Online Query Training tool

MongoDB playground: https://mongoplayground.net/

Here you can safely try out common DB operations without having to deal with the hassle of installing an own Mongo database.


### Command Cheatsheet

Find following some cheat sheets for common DB operations (for usage in Online training tool or in the terminal):

MongoDB Cheatsheet:
https://github.com/azat-co/cheatsheets/blob/master/mongodb-mongoose/readme.md

See section "MongoDB console". Do NOT click the PDF - that's a paid version :) 



