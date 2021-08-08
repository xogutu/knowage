**Setup**  
To make our work easy in setting up the data science components in knowage, we will use the docker container images so that we dont have to manually setup the configurations needed for Python or R to work with Knowage. Secondly, docker is becoming the standard software distribution and you should embrace it.

**Step 1**  

We will need a database to use to store the Knowage metadata. Use the following to pull and run a mariadb database in your docker machine.

`docker run -p 3308:3306 -e MYSQL_DATABASE=db -e MYSQL_USER=knowage -e MYSQL_PASSWORD=pass123 --name knowage-mariadb -v /home/developer/knowage-mariadb:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=pass123 -d mariadb`

Replace `/home/developer/knowage-mariadb` with the location where you need your database to be persisted.

**Step 2**  
Pull and run Knowage server and try to use a stable version of Knowage to avoid errors during setup. As at writing this tutorial, the stable version is 7.4 so that is what I used.

`docker run  --rm --name knowage-server -p 8002:8080  -d -e DB_USER=root -e DB_PASS=pass123 -e DB_ROOT_PASS=pass123 \
-e DB_DB=db -e DB_HOST=10.0.2.4 -e DB_PORT=3308 -e HMAC_KEY=pass123 -e PASSWORD_ENCRYPTION_SECRET=pass123 \
-e CACHE_DB_HOST=10.0.2.4 -e CACHE_DB_PORT=3308 -e CACHE_DB_DB=db -e CACHE_DB_USER=root -e CACHE_DB_PASS=pass123 \
-e PUBLIC_ADDRESS=10.0.2.4 knowagelabs/knowage-server-docker:7.4`

**Step 3**  
Lastly, pull and run the python image. Again, use a stable version. Alternatively, you can use R.

`docker run --rm --name knowage-python -d  -v /home/developer/datasets:/datasets -e HMAC_KEY=pass123 -e KNOWAGE_PUBLIC_ADDRESS=http://10.0.2.4:8002 \
-e PUBLIC_ADDRESS=10.0.2.4 -p 5000:5000 knowagelabs/knowage-python-docker:7.4`

** Server Settings**
Under server settings menu, select Configuration management then search for python. For both `python.virtualenv.0.backend.url` and `python.virtualenv.0.frontend.url` configure them to have the IP address and port where the `knowagelabs/knowage-python-docker` container is running.
Configure settings and setup your IP for both.

![image](https://user-images.githubusercontent.com/5442305/128616279-3fbb1a3f-70b4-44d2-80e6-7466fd515733.png)

Go to roles and under authorizaion enable federated dataset and python scripts. This is very important otherwise your dataset will not work and also you will not be able to view lbraries in your python container.

![image](https://user-images.githubusercontent.com/5442305/128616320-3157913f-74bf-4a85-9f8d-0cf92ba55bb0.png)

Still under roles, click on default model category.  

![image](https://user-images.githubusercontent.com/5442305/128616329-a24d0faa-164e-4909-9f3b-cdcb57c15fbb.png)

Under dataset select default dataset category.  

![image](https://user-images.githubusercontent.com/5442305/128616343-2ac9c721-52f5-4383-ae29-2a50976a0c4a.png)

Create a new dataset with options below under Detail tab.    

![image](https://user-images.githubusercontent.com/5442305/128616363-2b7aa4ba-c6ca-47da-99ba-c78e7840944b.png)

Click on the Type tab and for Dataset Type select `Python/R` and for environment, select `python.virtualenv.0.backend.url`. Click on Check environment.  

![image](https://user-images.githubusercontent.com/5442305/128616378-21e94eb0-3f68-4e29-ad71-e344d0f9413b.png)

Enter your dataframe variable in my case `df`. For dataset, we can use pandas to read an excel file on our disk. use whatever method you are comfortable with.

`import pandas as pd`    
 `df = pd.read_csv('/datasets/students.csv',sep=',')
`
![image](https://user-images.githubusercontent.com/5442305/128616584-4b1103f5-9185-423f-8430-88ccc0c477b6.png)

Preview your data and save dataset

![image](https://user-images.githubusercontent.com/5442305/128616603-f47867b6-13b0-437d-b32a-1225d37e713f.png)

You are now ready to use python for analysis.
