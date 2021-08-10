**BIRT**

BIRT is the acronym for Business Intelligence and Reporting Tools and is an open source initiative to create a fully functional reporting tool using open source tools. BIRT supports various types of reports such as lists, charts, crosstabs and compound reports. In this chapter, we will learn how to create BIRT reports and how to publish them in Knowage server. The first report we will create is a simple list report similar to the one shown below. It has a logo, aheading and data from the database.

![image](https://user-images.githubusercontent.com/5442305/128867339-a9bb0aff-76f9-4045-885a-5db30951507c.png)

NOTE: If you are not interested in following these steps, you can find the complete report file under BIRT\Administrative Costs.rptdesign which you can deploy in your Knowage.


Let us proceed and create a new report.
1.	We will need data from the database bank that came with this book. Import the contents of the file Database\bank.sql to your MySQL server.
2.	Download Software.
In this chapter, we will be using the eclipse based BIRT reporting software Knowage Report Designer. Download the Knowage Report Designer if you have not already done so as it comes with everything we need. To download the software, go to the URL below http://forge.ow2.org/project/showfiles.php?group_id=442&release_id=6002 

3.	Select the Knowage designer for your platform.
4.	Ensure that your already have java installed and that the JAVA_HOME variable is set correctly.
5.	Extract the designer to a folder of your choice e.g C:\Knowage\KnowageReportDesigner_6.1.0_win64
6.	Start the Knowage Report Designer by clicking on the file KnowageReportDesigner.exe if on windows. You will notice that this is very similar to the SpagoBI studio if you had used it in previous versions.

 ![image](https://user-images.githubusercontent.com/5442305/128867371-de4798bd-6e25-4c8c-b60b-14bda8dfb48d.png)


7.	Create a new project by going to File->New->Project..

 ![image](https://user-images.githubusercontent.com/5442305/128867386-435d0842-2f29-4734-a894-abf5548946e7.png)


8.	Under Business Intelligence and Reporting Tools select Report Project.

 ![image](https://user-images.githubusercontent.com/5442305/128867401-16dc39a2-c2fd-44d8-b264-6fc215902d98.png)


9.	Click Next.
10.	Under project name use “Business Intelligence”. For the storage location, use default.
11.	Your new project will now be visible on the navigator on the bottom left of the page.

 ![image](https://user-images.githubusercontent.com/5442305/128867422-6051f0f2-8e52-4be1-a1a7-89bcc8e6ca54.png)


12.	Define a new report. Click on File -> New -> Report.

 ![image](https://user-images.githubusercontent.com/5442305/128867440-f9d7da66-be6f-4bf2-9cb5-e4c65c55cc9b.png)



13.	For the report name, enter “Administrative Costs”

 ![image](https://user-images.githubusercontent.com/5442305/128867453-e4e46846-ff49-4732-aa35-0d8b4115139c.png)


14.	For the report template, select blank report and click on finish.

 ![image](https://user-images.githubusercontent.com/5442305/128867470-4c3b6243-e965-41d7-9050-21c2e8f736ba.png)


15.	Your new report should be visible on the navigator.

 ![image](https://user-images.githubusercontent.com/5442305/128867489-f1cecfab-c38b-469c-ab47-ed7bce064014.png)


16.	Reports can get their data from various sources such as flat files or relational databases.





Database connection.

Reports can get their data from various sources such as flat files or relational databases.

We need to create a connection to the database from the Knowage Report Designer. Proceed as shown below.

1.	Click on Data -> New Data source.

 ![image](https://user-images.githubusercontent.com/5442305/128867549-46a99096-69d2-402d-846e-b57a82a6bc1b.png)


2.	Select JDBC Data Source, and on Data Source Name put “Mysql Local”

 ![image](https://user-images.githubusercontent.com/5442305/128867563-467d0ae1-b38c-4d4d-93ea-49134c27ee90.png)


3.	For the Data source details, enter the following. These might be different if you are running the database on a different port or location.

 ![image](https://user-images.githubusercontent.com/5442305/128867579-a5f935ce-4c0e-47b6-b2b8-b9670936edee.png)


4.	Change the URL, username and password appropriately. Click on Test Connection. This should be successful before you proceed. Click on Finish.

 ![image](https://user-images.githubusercontent.com/5442305/128867590-0a8195a5-bc5b-41ec-bf6d-bd5d3d5000ed.png)


5.	When you click on Data Explorer, your new connection should be visible under “Data Sources”.

 ![image](https://user-images.githubusercontent.com/5442305/128867606-54946a6f-43de-422e-9d2c-9896752e4b5e.png)


6.	With the Data Explorer still opened, right click on Data Sets, and select New Data Set.

 ![image](https://user-images.githubusercontent.com/5442305/128867619-898922d6-79b9-490c-99ea-d85dc641df0b.png)


7.	For the data source location select Mysql Local (The data source you just created above).
8.	For data set name, put AdminCost.
9.	For the query text, use “select * from admincosts2010”. This will select all the contents of the table admincost table.
10.	Click on finish.
11.	On your dataset, click on preview results, this will output the contents of the table admincost2010.

 ![image](https://user-images.githubusercontent.com/5442305/128867629-83927566-75ec-4dd9-8ed6-21ebcaa14056.png)


12.	Click on Palette and under report items, select grid and drag it to your report. The grid allows you to organize the items in your reports like images, charts, text etc.

 ![image](https://user-images.githubusercontent.com/5442305/128867648-de7c6405-3d56-4ad5-b3aa-0f578df0c6d0.png)


13.	Create a grid with 2 columns and one row.

 ![image](https://user-images.githubusercontent.com/5442305/128867670-744f3363-d6a5-43e9-917b-993139c19e0f.png)


14.	Drag an image icon to the first cell.

 ![image](https://user-images.githubusercontent.com/5442305/128867693-b123cb1a-5380-461d-acf1-facd901fbb2a.png)


15.	Click on embedded image then select the shemma.jpg image from the images folder that came with this book.

 ![image](https://user-images.githubusercontent.com/5442305/128867713-dab1d801-ce59-473e-8ab7-44888c7b69f5.png)


16.	Drag the image to make it smaller.
17.	Drag the text item to the second cell.

 ![image](https://user-images.githubusercontent.com/5442305/128867720-47abb883-9746-4d53-b1ac-353f1d34a8e3.png)


18.	For the type of text, select HTML. Write a header as shown. As you can see, you can use html to format your text.

 ![image](https://user-images.githubusercontent.com/5442305/128867737-e3c6c12d-5c93-4608-8e47-57047378c1fc.png)


19.	Next we will include the actual data on the report. To include data from the data set we created above on the report, click on the Data Explorer tab. Expand data sets and drag AdminCost on an empty area of your report.

 ![image](https://user-images.githubusercontent.com/5442305/128867746-4e8490ee-0df4-47ba-92db-a2842ecc80db.png)


20.	Select the columns that you want to include in your report. In this case, we want to include items for first quarter only (JAN, FEB, MAR).

 ![image](https://user-images.githubusercontent.com/5442305/128867759-12cbc83e-461a-472c-9d4e-81a8ff1ba3fe.png)


21.	Using the property editor, change the heading for id, item, january, february,march.You will get result below.
a.	Before change

 ![image](https://user-images.githubusercontent.com/5442305/128867777-88c397c1-18ac-4d2b-a9ae-be44a4c0ec95.png)


b.	After change

 ![image](https://user-images.githubusercontent.com/5442305/128867799-cc88cfd3-b911-4186-b49f-fcfbb587af3e.png)


22.	To test the report we just created, click on Run -> View Report -> In Web Viewer.

 ![image](https://user-images.githubusercontent.com/5442305/128867812-5bd868b2-e666-4b12-be7c-64bcc354592c.png)


23.	And there you have it, your very first BIRT report!


Publishing Report.

Next we need to publish our report to the Knowage server. The first thing we need to do is create parameters that will be used to pass database username, password, URL and class. If we do this, then our report will be dynamic and can be used in any Knowage server even if database name and password are different from the ones that we used to create the report. Proceed as follows. 

1.	In the data explorer, right click on Report Parameters then click on New Parameter. For the name enter driver.

 ![image](https://user-images.githubusercontent.com/5442305/128867837-a5418715-579b-4062-95f3-239685edbc3a.png)


2.	Create other parameters url, user and pwd.

![image](https://user-images.githubusercontent.com/5442305/128867932-b803f5c5-1c95-4545-a522-11bbc63de88b.png)

 
3.	Right click on the data source “Mysql Local”, click on edit and select Property Binding. Attach the parameters as shown below.

 ![image](https://user-images.githubusercontent.com/5442305/128867969-9463d846-4561-4157-be84-f0a7204405c0.png)


4.	We are going to manually deploy this report to Knowage. In our second report, we will show you how to upload automatically using Knowage Server. Right click on report and select properties.

 ![image](https://user-images.githubusercontent.com/5442305/128867988-e7e70863-c4f4-4941-bde5-f1a8958d2c2c.png)


5.	Note the file path.

6.	Login to Knowage and create a data source to point to the Bank database that we have used to create this report.

 ![image](https://user-images.githubusercontent.com/5442305/128868007-7a7269a6-a038-4f9b-b19e-198a7567a1c6.png)


7.	Create a new document with the following properties.

 ![image](https://user-images.githubusercontent.com/5442305/128868022-dcf64808-2638-4289-9300-99cb8fc9e430.png)


8.	Under Show document templates, select the folder you want your document to be stored.

 ![image](https://user-images.githubusercontent.com/5442305/128868038-0d3ccd22-a360-4cf5-90a5-aaad030dc2ef.png)


9.	Click on browse and navigate to where your “Administrative Costs.rptdesign” report file is stored. This is the path we highlighted in step 4 above.

 ![image](https://user-images.githubusercontent.com/5442305/128868068-b9baf4db-76d1-4e3f-bdad-48b1ea1d2396.png)


10.	Save and execute the document.

 ![image](https://user-images.githubusercontent.com/5442305/128868085-4504473d-e637-4718-a02b-2a4616813309.png)


11.	Congratulations on creating your first BIRT report on Knowage!
