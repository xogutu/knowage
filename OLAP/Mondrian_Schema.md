**Mondrian Schema**

We have now created our business model but before we use it in Knowage to create an OLAP document, we need to create a Mondrian schema. So what is a schema? Basically, a schema is a structure used to define either a relational database or multi-dimensional database. In a multi-dimensional database, the schema is usually a star schema as we have discussed in previous chapters. The schema defines several items including:
1.	The logical model which describes the entities, relationships, attributes for entities etc.
2.	How the logical model is mapped to the physical model.
3.	Hierarchies which are levels of the dimension attribute. For example, for the time attribute, we can have the following hierarchy:
  a.	Year
  b.	Quarter
  c.	Month
4.	Members
5.	Cubes

**Creating a schema**

A Mondrian schema is represented as an XML file and you can create one is a text editor like notepad. However, this is a time consuming activity which we need not go through as there are now graphical editors that can generate the schema XML which we can then upload into Knowage to create our OLAP document.

Follow the steps below to download and install a free GUI tool to use in creating the schema.

1.	Go to https://sourceforge.net/projects/mondrian/files/schema%20workbench/  and download the latest version of Schema Workbench which is 3.14.0 as at writing this book. This software is licensed under Eclipse Public License v1.  
2.	Both the Schema Workbench and Knowage requires Java so install the latest version in the machine where you will be using these tools.  
3.	Once the Schema Workbench is installed, use the workbench.bat file to start it then under Options, select Connection.   

![image](https://user-images.githubusercontent.com/5442305/128617920-67ad164b-22f1-47d1-a40c-ec29ce7c0ab8.png)

4.	The connection menu is used to connect to the database that has the dimension and fact tables. You need to connect to the foodmart database that came with this book as shown below.

![image](https://user-images.githubusercontent.com/5442305/128617926-0529a563-b214-4c11-9c7a-34657e00aac7.png)

5.	Click on File->New->Schema

![image](https://user-images.githubusercontent.com/5442305/128617931-7e5dd4df-5dd9-4664-9949-b69aed298a81.png)

6.	Give the Schema a name “Store”.

 ![image](https://user-images.githubusercontent.com/5442305/128617940-42c4502f-37a3-4ebb-b6f1-f87c9779b6fb.png)

7.	The first thing we need to add is a cube. A cube is a collection of dimensions and measures and to create one, click on “Add cube” button.

![image](https://user-images.githubusercontent.com/5442305/128617944-5cfb57c4-35d4-46dd-a833-75dd0e42b56b.png)

8.	For the name of the cube use “Sales”,  description use “Sales Cube”.

![image](https://user-images.githubusercontent.com/5442305/128617947-673ffe4a-705a-466c-ab27-74a6b2e25b9b.png)

9.	From the definition of a cube, remember it is a collection of dimensions and measures and measures are normally found in a fact table so let us add a fact table. If you look keenly at the image above, you will see a message “Fact name must be set” at the bottom of the screen. This is because we have not added a fact table to our cube. To do so, right click on the cube and click on “Add Table”

![image](https://user-images.githubusercontent.com/5442305/128617952-34da0728-9eef-487d-9b69-63e59b34d85b.png)

10.	Select the sales_fact table from the foodmart database. This is the table that contains the Measures we want to look at.

![image](https://user-images.githubusercontent.com/5442305/128617957-2dbf66d6-695d-4452-bf0c-7fa134ed0924.png)

11.	Apart from measures, the other component of a cube is a dimension. Infact, if you look at the bottom of the image below, you can see that it says “Cube must contain dimensions”.  We have two dimension tables that we want to include in our cube namely store and time_by_day. Right click on the cube and select “Add Dimension”

![image](https://user-images.githubusercontent.com/5442305/128617966-3458cddb-df5c-4664-8770-a694ffcb8cfd.png)

12.	The first dimension we need to add is the time dimension that contains the year, quarter and month the sale occurred. Therefore, for name of the dimension, use “Time”. We also need to specify which column will be used by the fact table as a foreign key to help link with the dimension table. For foreignKey, use “TIME_ID”.

![image](https://user-images.githubusercontent.com/5442305/128617976-293d2d5a-7270-4ebe-b65e-c5ac76348d50.png)

13.	Next, we need to add a hierarchy to our dimension. Click on the dimension and add for name, use “Period”. Ensure hasAll is checked. allmemberName should be “Sales Period”. The primaryKeyTable should be “time_by_day” and primaryKey should be “TIME_ID”.

![image](https://user-images.githubusercontent.com/5442305/128617981-0f95b4fc-dd53-4a6a-9641-701e2b13d60c.png)

14.	Once you have added hierarchy, the next step is to add levels. Select the Period hierarchy and click on add level.

![image](https://user-images.githubusercontent.com/5442305/128617987-20359821-0cc5-4dc5-9810-c730ea0180f5.png)

15.	The first level we want to add is year. Therefore, for the level name, use “Year”, the table “time_by_day”, for description use “Year” and the column “THE_YEAR”.

![image](https://user-images.githubusercontent.com/5442305/128617993-ad10efb4-df1a-4fec-b40d-d0b6bc5150fe.png)

16.	Add the next which is Quarter with parameters shown below.

![image](https://user-images.githubusercontent.com/5442305/128617997-fc6dc470-3270-4fd7-86c2-7df891d9c588.png)

17.	Finally on levels for this dimension add the month level as shown below.

![image](https://user-images.githubusercontent.com/5442305/128618003-265ae078-7354-42fa-8822-38d9930e7fef.png)

18.	To finish off with this hierarchy, add the dimension table by right clicking on Period hierarchy and clicking on add table.

![image](https://user-images.githubusercontent.com/5442305/128618007-4af6b7d8-5ac2-4792-bce5-f6290c2655a6.png)

19.	Select the dimension table time_by_day. That will be it for this dimension.

![image](https://user-images.githubusercontent.com/5442305/128618011-c35b6019-c2b8-4c43-9518-31f676ca3113.png)

20.	The next dimension we need to add is the store dimension. So again, right click on cube and add dimension.

![image](https://user-images.githubusercontent.com/5442305/128618014-a44bb2dd-02f9-46f3-8258-33dd061381f6.png)

21.	Use the properties shown below.

![image](https://user-images.githubusercontent.com/5442305/128618019-8ecc6900-aa36-4ac7-8799-bca7d9d3228d.png)

22.	Next add the hierarch store with the following properties.

![image](https://user-images.githubusercontent.com/5442305/128618025-b11abb3e-1325-41b6-9bf2-6065082b24a2.png)

23.	Under store, add one level called “Store”.

![image](https://user-images.githubusercontent.com/5442305/128618034-a4946b0b-acee-4afb-859c-d6c794a3d5c6.png)

24.	For this hierarchy, add the dimension table.

![image](https://user-images.githubusercontent.com/5442305/128618043-8101058a-8a1a-437e-8310-645dd19e6362.png)

25.	Our cube now has two dimensions, time dimension and store dimension. It also has a fact table but what is missing are the measures. In the “sales_fact” table, what is it that we want to measure?  We will measure:  
  a.	Store sales in the column “STORE_SALES”.
  b.	Store cost in the column “STORE_COST”.

26.	Right click the sales cube, and select “Add Measure”

![image](https://user-images.githubusercontent.com/5442305/128618048-6d3c217b-cd0f-4ade-82b2-bf974b79db23.png)

27.	Use the following properties:
  a.	For name, enter "Store Sales".
  b.	For  column, use "STORE_SALES".
  c.	For  datatype, use "Numeric".
  d.	For  formatString, use "$#,###.##".
  e.	For  aggregator, use "sum".

28.	Once done, it should appear as below.

![image](https://user-images.githubusercontent.com/5442305/128618056-73086b00-dc26-4576-a599-ed3c7c8faf3d.png)

29.	Add another measure “store Cost” with the following properties.

![image](https://user-images.githubusercontent.com/5442305/128618058-cbff2624-a127-409f-852c-c22c3b9da26f.png)

30.	Lastly, we want to show you how to add a calculated member. This will be the difference between Store Sales and Store Cost. We will call it “Profit”. Right click on the cube and select “Calculated Member”

![image](https://user-images.githubusercontent.com/5442305/128618062-3c82cb8a-56ba-4a8d-8fd7-fb82f8fe6ab3.png)

31.	Use the following:
  a.	For name use "Profit".
  b.	For formula, use "[Measures].[Store Sales] - [Measures].[Store Cost]".
  c.	For dimension, use "Measures" 

![image](https://user-images.githubusercontent.com/5442305/128618069-f4da91bc-48a7-4084-a1f3-f62b6e08c780.png)

32.	Once you have added the calculated member, you need to add a calculated member property where you will specify the format string. Right click on the calculated member and select “Add Calculated Member Property”

![image](https://user-images.githubusercontent.com/5442305/128618072-5efe5846-f146-495b-9caf-454f00dd20e8.png)

33.	For name use “FORMAT_STRING” and value “$#,###.##”

![image](https://user-images.githubusercontent.com/5442305/128618075-8ff57292-f5a4-4c45-a134-cd7d3cb196c6.png)

34.	Save the schema as SchemaFoodMart.xml. It should look as follows.


`<Schema name="Store">`  
`  <Cube name="Sales" visible="true" description="Sales Cube" cache="true" enabled="true">`  
`    <Table name="sales_fact" alias="">`  
`    </Table>`  
`    <Dimension type="StandardDimension" visible="true" foreignKey="TIME_ID" name="Time">`  
`      <Hierarchy name="Period" visible="true" hasAll="true" allMemberName="Sales Period" primaryKey="TIME_ID" primaryKeyTable="time_by_day">`  
`        <Table name="time_by_day" alias="">`  
`        </Table>`  
`        <Level name="Year" visible="true" table="time_by_day" column="THE_YEAR" uniqueMembers="false">`  
`        </Level>`  
`        <Level name="Quarter" visible="true" table="time_by_day" column="QUARTER" uniqueMembers="false" description="Quarter">`  
`        </Level>`  
`        <Level name="Month" visible="true" table="time_by_day" column="THE_MONTH" uniqueMembers="false" description="Month">`  
`        </Level>`  
`      </Hierarchy>`  
`    </Dimension>`  
`    <Dimension type="StandardDimension" visible="true" foreignKey="STORE_ID" name="Store" description="Store">`  
`      <Hierarchy name="Store" visible="true" hasAll="true" allMemberName="All Stores" primaryKey="STORE_ID" primaryKeyTable="store" description="Store">`  
`        <Table name="store" alias="">`  
`        </Table>`  
`        <Level name="Store" visible="true" table="store" column="STORE_NAME" uniqueMembers="false" description="Store">`  
`        </Level>`  
`      </Hierarchy>`  
`    </Dimension>`  
`    <Measure name="Store Sales" column="STORE_SALES" datatype="Numeric" formatString="$#,###.##" aggregator="sum" visible="true">`  
`    </Measure>`  
`    <Measure name="Store Cost" column="STORE_COST" datatype="Numeric" formatString="$#,###.##" aggregator="sum" visible="true">`  
`    </Measure>`  
`    <CalculatedMember name="Profit" formatString="" formula="[Measures].[Store Sales] - [Measures].[Store Cost]" dimension="Measures" visible="true">`  
`      <CalculatedMemberProperty name="FORMAT_STRING">`  
`      </CalculatedMemberProperty>`  
`    </CalculatedMember>`  
`  </Cube>`  
`</Schema>`  






















