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
## databases
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

![_config.yml]({{ site.baseurl }}/images/pgdeletedb.png)

>^this command will drop the myotherdata database

## tables
The first thing we can do with out newly created database is stick a table in there

![_config.yml]({{ site.baseurl }}/images/pgmaketable.png)

>^this makes a table called myinfo in the database mydata


Up to this point we have been working with the defult account on the postgresql server, this account is refered to as the admin account and it is the general concesus that best practice is to only use the admin account for executive decision making and creating other accounts. In the next section we will be discussing how to create these new accounts and how to control what they do and dont have access to.
