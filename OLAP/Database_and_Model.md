**Step 1: Load database.**

Navigate to the folder Database that came with this book and load the file foodmart.sql to your database if you have not already done so. Here are the steps to load the file.
1.	Visit the link https://dev.mysql.com/downloads/workbench/ to download the graphical tool MySQl workbench that will help us import the data and easily manage MySQL.
2.	Install MySQl workbench and connect to your MySQl server and select Data Import/Restore.

![image](https://user-images.githubusercontent.com/5442305/128617673-53e47c34-8fa1-4a11-94d2-354b32ae0db9.png)

3.	On the next screen, click on Import from Self-contained file and select the foodmart.sql file that came with this book.

![image](https://user-images.githubusercontent.com/5442305/128617681-0e7e5349-5104-490f-954c-848d50b3b629.png)

4.	Click on start import. It will take you to a screen where you can monitor the import progress

![image](https://user-images.githubusercontent.com/5442305/128617691-23293d76-c41e-4ba7-94b3-9431364d7353.png)

**Step 2: Create Data source connection.**

Once we have imported the sample data we will need to demonstrate OLAP, we need to login to Knowage instance that we installed previously and create a connection to the MySQL database. Proceed as follows.

1.	Navigate to http://localhost:8080/knowage  and login with username biadmin and password biadmin.

![image](https://user-images.githubusercontent.com/5442305/128617713-116349b2-a9ec-449b-a609-0ef25cbd793e.png)

2.	Click on highlighted region below to open menu.

![image](https://user-images.githubusercontent.com/5442305/128617721-b305aff4-7706-4b90-bbf8-18c9793a82db.png)

3.	Under Data Providers, select Data source

![image](https://user-images.githubusercontent.com/5442305/128617727-1805b0b4-ff95-4cad-a123-2a79444a45c2.png)

4.	Click on add new.

![image](https://user-images.githubusercontent.com/5442305/128617733-1b8617a3-2c6b-46eb-9ec2-7912b67ff883.png)

5.	On the next screen:
a.	For label use “MySQL Foodmart”.
b.	For description, use “MySQL Database”.
c.	For dialect, use MySQL.
d.	For URL use jdbc:mysql://localhost/foodmart
e.	Enter username and password
f.	For driver, use com.mysql.jdbc.Driver
g.	Click on Test. It should be successful.

![image](https://user-images.githubusercontent.com/5442305/128617748-07adfe4e-4841-470c-b002-093a8afce346.png)

h.	Click on Save

**Step 3: Create Business Model**

To create a business model, proceed as follows:

1.	Under catalogs, select Business Models catalog.

![image](https://user-images.githubusercontent.com/5442305/128617765-32e3568a-2d1c-4f95-a7f9-b96c09ebf425.png)

2.	Select new button.

![image](https://user-images.githubusercontent.com/5442305/128617767-c6d81804-02a4-468e-b9a3-b6a3aa474be4.png)

3.	Use the following to fill the fields:
a.	For name use “Sales Model”.
b.	For description use “Sales Model”.
c.	For category, use “Default Model Category”.
d.	Select the “MySQL Foodmart” as data source then click on “Save”.

4.	Click on enable “Enable Meta Web”

![image](https://user-images.githubusercontent.com/5442305/128617778-fbeb2b4f-e721-4c7d-82d1-ceafb1f5da46.png)

5. Click on “Meta Web”

![image](https://user-images.githubusercontent.com/5442305/128617781-a1ff15fc-2681-4301-a932-3d1467d3d347.png)

6.	Select the tables sales_fact, store and  time_by_day. Ensure the checkbox for “Physical Model” and “Business Model” are selected.

![image](https://user-images.githubusercontent.com/5442305/128617785-6faaff76-e042-4ceb-ae71-4c6f917ef729.png)


From our discussions on Dimensions and Fact tables in Lesson One, we will notice that the table “sales_fact” is the fact table here as it contains all the measures that we want that we will be summarizing for this cube. These measures are highlighted below.

![image](https://user-images.githubusercontent.com/5442305/128617791-c67e6838-70ba-4702-81ab-ecb02ab0a761.png)

Also notice that there are two important foreign keys; TIME_ID which is used to link the sales_fact table to the dimension table time_by_day which contains the sales day, sales quarter, sales year e.tc and STORE_ID which is a foreign key that links the sales_fact table to the dimension table store. Our star schema therefore looks like this:

![image](https://user-images.githubusercontent.com/5442305/128617799-169cc3d1-e378-42b5-82c0-43206036b218.png)

7.	On the Business Model tab, expand Sales fact by clicking on the highlighted icon below.

![image](https://user-images.githubusercontent.com/5442305/128617804-907f135b-7218-4343-bde7-de5932b76de4.png)

8.	Click on “STORE SALES” and change the type to Measure.

![image](https://user-images.githubusercontent.com/5442305/128617812-8dd01a99-e08a-42b3-abdf-478cc50268cc.png)

9.	Do the same for “STORE COST” and “UNIT SALES”.
10.	Click on Save

![image](https://user-images.githubusercontent.com/5442305/128617815-51789b58-5f32-4db3-8b79-bcb1da8c3d52.png)

11.	Under “BUSINESS MODELS' CATALOGUE”, click on “Sales Model” and then select “Enable Meta Web”.

![image](https://user-images.githubusercontent.com/5442305/128617822-5e650be4-1525-4b06-a324-228faf1bc17b.png)

12.	Next, select Generate.

![image](https://user-images.githubusercontent.com/5442305/128617828-6949f2ce-e603-4472-ad13-f8b86461d258.png)

13.	On the next dialog click on Create

![image](https://user-images.githubusercontent.com/5442305/128617832-7d572544-eff1-4343-b390-46c3dd5b5194.png)

14.	Creation of the business model is now complete. Next we need to create a Mondrian schema which together with the model we will use to create an OLAP document.


















