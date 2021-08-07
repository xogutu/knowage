**Setup**  
To make our work easy in setting up the data science components in knowage, we will use the docker container images so that we dont have to manually setup the configurations needed for Python or R to work with Knowage. Secondly, docker is becoming the standard software distribution and you should embrace it.

**Step 1**  

We will need a database to use to store the Knowage metadata. Use the following to pull and run a mariadb database in your docker machine.

`docker run -p 3308:3306 -e MYSQL_DATABASE=db -e MYSQL_USER=knowage -e MYSQL_PASSWORD=pass123 --name knowage-mariadb -v /home/developer/knowage-mariadb:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=pass123 -d mariadb`

Replace `/home/developer/knowage-mariadb` with the location where you need your database to be persisted.

**Step 2**  
Pull and run Knowage server and try to use a stable version of Knowage to avoid errors during setup. As at writing this tutorial, the stable version is 7.4 so that is what I used.

`docker run --rm  -p 8002:8080  -d -e DB_USER=root -e DB_PASS=pass123 -e DB_ROOT_PASS=pass123 \
-e DB_DB=db -e DB_HOST=192.168.8.167 -e DB_PORT=3308 -e HMAC_KEY=pass123 -e PASSWORD_ENCRYPTION_SECRET=pass123 \
-e PUBLIC_ADDRESS=192.168.8.167 knowagelabs/knowage-server-docker:7.4`

**Step 3**  
Lastly, pull and run the python image. Again, use a stable version. Alternatively, you can use R.

`docker run --rm --name knowage-python -d  -v /home/developer/datasets:/datasets -e HMAC_KEY=pass123 -e KNOWAGE_PUBLIC_ADDRESS=http://192.168.8.167:8002 \
-e PUBLIC_ADDRESS=192.168.8.167 -p 5000:5000 knowagelabs/knowage-python-docker:7.4`
