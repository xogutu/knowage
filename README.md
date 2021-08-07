# knowage
Knowage Administration
This repo contains doumentation and how to setup and make use of Knowage.
# Run knowage server as docker container

First you need to start a database container. Here we use mariadb.
docker run -p 3308:3306 -e MYSQL_DATABASE=db -e MYSQL_USER=knowage -e MYSQL_PASSWORD=pass123 --name knowage-mariadb -v /home/xman/knowage-mariadb:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=pass123 -d mariadb

Second, run the docker container. Use a stable version here we use version 7.4.

docker run  --rm --name knowage-server -p 8002:8080  -d -e DB_USER=root -e DB_PASS=pass123 -e DB_ROOT_PASS=pass123 \
-e DB_DB=db -e DB_HOST=10.0.2.4 -e DB_PORT=3308 -e HMAC_KEY=pass123 -e PASSWORD_ENCRYPTION_SECRET=pass123 \
-e CACHE_DB_HOST=10.0.2.4 -e CACHE_DB_PORT=3308 -e CACHE_DB_DB=db -e CACHE_DB_USER=root -e CACHE_DB_PASS=pass123 \
-e PUBLIC_ADDRESS=10.0.2.4 knowagelabs/knowage-server-docker:7.4

Third, if you are into data science, start the knowage-python container
docker run --rm --name knowage-python -d  -v /home/developer/datasets:/datasets -e HMAC_KEY=pass123 -e KNOWAGE_PUBLIC_ADDRESS=http://10.0.2.4:8002 \
