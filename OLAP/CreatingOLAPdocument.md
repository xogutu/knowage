**Mondrian Schema Catalog**

The schema that we have created above needs to be stored in Knowage as a Mondrian Schema catalog. Once this is done, then we can use it together with the business model we had created previously to create an OLAP document. Proceed as follows to save the schema to in Knowage.

1.	Under Catalogs, select “Mondrian schemas catalog”.
![image](https://user-images.githubusercontent.com/5442305/128624787-9536f721-eea8-41d9-be29-d4e27a7ae4b0.png)

2.	Click on add button

![image](https://user-images.githubusercontent.com/5442305/128624836-01e260a3-e03a-4e23-a127-549032a6cf46.png)

3.	For name use “Store” and description “Store Sales” and under “File Upload”, select the SchemaFoodMart.xml file we had created previously.

![image](https://user-images.githubusercontent.com/5442305/128624843-5fef7926-25c3-4d7c-b757-67485400846b.png)

4.	Click on Save.

**Creating OLAP document**

Finally, we have all the components we need to create an OLAP document. We have the source database, we have the business model and we have the Mondrian schema. To create the OLAP document, proceed as follows:

1.	First, we need to create a folder where we will save our OLAP document. Under “Profile Management”, select “Functionalities management”.

![image](https://user-images.githubusercontent.com/5442305/128624859-92ffde92-d4d0-467d-8772-f79974a322bd.png)

2.	Create a new folder with the options below. This means that anyone with admin role will be able to have full access to this folder. Save.

![image](https://user-images.githubusercontent.com/5442305/128624862-e0f22659-11ab-467a-a1cc-2c5f1ec4ef79.png)

3.	Click on “Document development icon”.

![image](https://user-images.githubusercontent.com/5442305/128624867-ba933e3c-f5ee-4706-9c5a-91689db634e9.png)

4.	Select New button then “Generic Document”.

![image](https://user-images.githubusercontent.com/5442305/128624872-ddffe85b-2540-48fe-b84b-e2016e872fc4.png)

5.	For label use “Store Sales”.
6.	For Name use “Store Sales”.
7.	For Description use “Store Sales”.
8.	Under type, use “On-line analytical processing”.
9.	For the engine, use “OLAP Engine”.
10.	Select the data source where Foodmart database is created.
11.	Under “Functionalities Tree”, select “OLAP” then Save.

![image](https://user-images.githubusercontent.com/5442305/128624884-d66597c9-a840-4d57-b0af-c0086be9bb07.png)

12.	Select “Generate new template”

![image](https://user-images.githubusercontent.com/5442305/128624898-e9a0722b-6b0d-4524-909e-9b4370d9f72d.png)

13.	For “Template Type” select Mondrian.
14.	Select the Mondrian Schema we had created previously.
15.	Select the cube

 ![image](https://user-images.githubusercontent.com/5442305/128625200-937dcaa9-c95a-4c5e-bacc-9282c16601bc.png)

16.	Click on “Start”. And you will have finished with your first OLAP document. By default, it will show you the total sales for all periods for all stores.

![image](https://user-images.githubusercontent.com/5442305/128625210-a4f8a188-3946-4887-8b94-b8503bc808be.png)

17.	Drag the Store dimension just beside the measures.

![image](https://user-images.githubusercontent.com/5442305/128625223-4f9ab1c2-59e2-4a10-9972-e10222959cef.png)

18.	Click on the highlighted icon (+) to view all stores.

![image](https://user-images.githubusercontent.com/5442305/128625228-8b716b98-9532-4232-bd3c-ad2417088a51.png)

19.	Then click on the measures filter (highlighted in yellow) so that we can add other measures like cost and profit.

![image](https://user-images.githubusercontent.com/5442305/128625233-8c3501fa-895f-4dbc-9ef7-8594314a3971.png)

20.	Select Store Cost and Profit and click on Save.

![image](https://user-images.githubusercontent.com/5442305/128625238-4670a662-760c-45b2-9316-4d9c0803656d.png)

21.	Now we can analyze the data in any way we desire.

![image](https://user-images.githubusercontent.com/5442305/128625245-8a26916b-8afd-4cb8-b4e4-029378be9b70.png)

22.	There are some additional configurations you can do by clicking on the button shown below on the right of the page.

![image](https://user-images.githubusercontent.com/5442305/128625261-fefe1cc0-b6d4-4ac4-99c9-d1d329d44d86.png)

23.	Then selecting “Configure buttons visibility”

![image](https://user-images.githubusercontent.com/5442305/128625270-f6e28968-ca60-4c76-ac80-90a93a6e1e7b.png)

24.	Then selecting the button you want to be visible and click on Save template and close the designer.

![image](https://user-images.githubusercontent.com/5442305/128625284-c7d1ddc3-596d-4c54-bc15-48a5ed02dd94.png)

25.	You will then need to save the document. See yellow arrow below.

![image](https://user-images.githubusercontent.com/5442305/128625292-4b8ef422-a9a7-4e3e-b56f-5c25de7f574e.png)

26.	Click on the back button then execute the document.

![image](https://user-images.githubusercontent.com/5442305/128625298-37f561f0-4090-4a0f-aec8-024fdf48ddb4.png)

27.	Now you can see the buttons have been added.

![image](https://user-images.githubusercontent.com/5442305/128625304-3c6ece0a-7958-47bb-a1ad-c2dd6a6e9676.png)

28.	Let us try one by viewing the OLAP MDX query

![image](https://user-images.githubusercontent.com/5442305/128625309-3b64bfb6-111e-4a48-a182-aa1bb97899db.png)

29.	It will display the MDX query. Try to use the other buttons.

![image](https://user-images.githubusercontent.com/5442305/128625310-b5f0d34c-1402-4e57-9aeb-4346c71330fa.png)






