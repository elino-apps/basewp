# Wordpress Developer base 
This is the base repo for SAM wordpress deploy.
All new wordpress are sarted with this base as wp-content


## Starting the developer setup

**First install docker and docker-compose**

Start the setup with 

```
docker-compose up
```


This will bring up the developer docker images and setup the wordpress for you.
You can now wisit your wordpress on your local computer at


### For wordpress 

**http://localhost**

**http://localhost/wp-admin** (admin/admin)




If you need a nother port modify the docker-compose.yaml and change port 80 to other port.
You can also change so that wordpress 5 is running on port 80 and 443

```
     ports:
       - "80:8000"
       - "443":8443

```


### HTTPS
The docker will serve a page under https://localhost. The certificate is self signed and need to be accepted.


### DB Seed
When you run docker-compose the sql in the file seed/wordpress.sql will be seeden into the SQL server




### Phpmyadmin
phpmyadmin is a database tool included and can be found on **http://localhost:82** from here you can performe database actions to the database.

## Push your changes to the online Wordpress

When updating the online wordpress simply push your changes to github master barnch


```
git add .
git commit -a -m "Update"
git push origin master
```


**YOUR DB CHANGES WILL NOT BE PUSHED AND MUST BE APPLIED MANUALL**


### Get the online version

Backup of the corrent running version online are saved into the branch fromserver.
Simply check out that bransh and start the docker compose to get the current state of your wordpress.

### Migrate DB

when migrate the databse you need to update the wordpress siteurl. Read here how you update your site url

https://codex.wordpress.org/Changing_The_Site_URL this is best done in the SQL part and with the followinf phpmyadmin tool after the database.

** Move to devloping **

```
- Dump your old database and store it in a sql file in seed/wordpress.sql
- Startup the service with docker-compose up
- Login into phpmyadmin and change siteurl to http://localhost
- browse to your wordpress
```



** Move to hosting **

```
- Go into phpmyadmin and change siteurl to your site name example myblog.apps.example.com
- In phpmyadmin do a database dump of your database.
- Go to your hosted site and import your database dump
```
