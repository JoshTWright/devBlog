---
layout: post
title: PostgreSQL Commands
---

Learn to use postgres basics to get you up and running.



In this post we will be going over some basic postgres knowledge and commands that will show you how to get a simple database set up and will show you which commands will be helpful to you when first starting out.I will be using the Cloud9 ide or C9 for short, i have a tutorial on how to setup a basic C9 workspace if that is of interest to you.

## setting up

Starting out we will want to navigate to our terminal on C9 and enter the following command.

![_config.yml]({{ site.baseurl }}/images/pgstart.png)

>^This will start our postgresql server

Now we should login so that we can make changes to the server

![_config.yml]({{ site.baseurl }}/images/pgflogin.png)

>^This will log us in to our server with the defult password

We must create a new password so we can create a more secure way to connect to our server. The following command may help with that.

![_config.yml]({{ site.baseurl }}/images/pgpasschange.png)

>^The defult password to our server has been changed

Now to demonstrate the new password working and a slightly different login procedure type the following command in to quit your session with the postgres server.

![_config.yml]({{ site.baseurl }}/images/pglogout.png)

>^This will log us out of the session

Now we can login to our server using a similar command from the first time, take note of the small changes made.

![_config.yml]({{ site.baseurl }}/images/pgnlogin.png)

>^ sudo sudo -U postgres psql  ------> psql -U postgres -h localhost

## Databases

Now we have the basic server setup done we can move on to creating databases.

![_config.yml]({{ site.baseurl }}/images/pgmakedb.png)

>^this makes a database called mydata

We can create multiple databases

![_config.yml]({{ site.baseurl }}/images/pgmakedb2.png)

>^this makes a database called myotherdata

We can switch between databases if needed

![_config.yml]({{ site.baseurl }}/images/pgchangedb.png)

>^this command will change the current database we reside in to mydata

We can also delete databases, this is refered to as 'dropping a database'
please note that you cannot drop a database if you are currently inside of it, 
you can tell which database you are in by looking to the left of the # sign on the terminal.

![_config.yml]({{ site.baseurl }}/images/pgdeletedb.png)

>^this command will drop the myotherdata database

There are little commands that will also help you in your endevors with postgresql databases.
One of those is the describe command, it will show all tables in a database, there are two versions which i will show below.

![_config.yml]({{ site.baseurl }}/images/pgpdescribedb.png)

>^this command describe the database

![_config.yml]({{ site.baseurl }}/images/pgdescribemoredb.png)

>^this command describe the database in more detail

Databases and thier tables can have multiple accounts tied to them within the postgresql server, 
each account can have a different set of permissions. 

![_config.yml]({{ site.baseurl }}/images/pgpermdb.png)

>^this command will show all permissions for tables in a given database. In this example there are two accounts postgres and newuser, both have all permissions active on the two listed tables in our mydata database.

## Tables
The first thing we can do with out newly created database is stick a table in there

![_config.yml]({{ site.baseurl }}/images/pgmaketable.png)

>^this makes a table called myinfo in the database mydata

We can drop tables just like we can drop databases.

![_config.yml]({{ site.baseurl }}/images/pgdroptable.png)

>^this makes a table called myinfo in the database mydata

## Roles (Accounts)

Up to this point we have been working with the defult account on the postgresql server, this account is refered to as the admin account and it is the general concesus that best practice is to only use the admin account for executive decision making and creating other accounts. In the next section we will be discussing how to create these new accounts and how to control what they do and dont have access to.

We are given the postgres defult admin account when we start our server for the first time, but we want to make more accounts to use for accessing our data so we can create a secure hierarchy of privilege.

![_config.yml]({{ site.baseurl }}/images/pgcreaterole.png)

>^this creates a user also known as a 'role' with the ability to login

Once we create the role using our admin account we can then begin giving the role permissions pertaining to specific tables.

![_config.yml]({{ site.baseurl }}/images/pggrantselect.png)

>^Gives newuser role the permission to Select from the myinfo and myinfo_id_seq tables 

![_config.yml]({{ site.baseurl }}/images/pggrantupdate.png)

>^Gives newuser role the permission to Insert into the myinfo table and update the id of the myinfo_id_seq table 

Okay so you have given a user permission to do something and now you have changed your mind, thankfully for you there is a revoke command built right in.

![_config.yml]({{ site.baseurl }}/images/pgrevoke.png)

>^The revoke command will remove the permission specified from the table specified

There are many options when it comes to which permissions postgresql supports.

### ist of possible privileges
Select
Insert
Update
Delete
Truncate
References
Connect
Create
Trigger
Temp
Temporary
Usage
Ececute
All Privileges


