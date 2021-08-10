Introduction to cockpits

Cockpits enable us to get a snapshot of the business as at a particular point in time. They give a summary of all business components in one screen or less. Consider an aircraft or automobile cockpit for example. Just by glancing at it, you will know the status of your aircraft or car in an instant. Similarly, in the world of business, you need a report that will tell you the status of your business in an instant without going through voluminous amounts of data. This is the function of a cockpit. In this lesson, we will learn how to create the various charts and then combine them to create a cockpit. 

Charts
A chart is a graphical representation of data and are important in easing the understanding of large amount of data. By just looking at the chart, we can easy understand trends and relationships in the data that would be very difficult to interpret by looking at the raw data in a tabular format.

Knowage supports several charts like bar, pie, line, word count, Sunburst, Chord, Heatmap, Radar, Treemap and many others. We shall begin our discussion of charts by looking at one of the most used charts, a bar chart.

Follow these steps.

1.	First, we need to create a data set where the simple bar chart will get its data. There is already an SQL statement under Cockpit\Data Sets\ bar_no_parameter.sql that we will use for this example.
2.	Login to Knowage and create a new dataset called DS_BAR_NO_PARAM with the content of this file and FoodMart database.

 ![image](https://user-images.githubusercontent.com/5442305/128863907-18e32539-290c-4072-b027-8ce5909b93c9.png)


3.	Ensure you set all other columns except column X as measures then save the data set.
4.	Then create a new cockpit.

 ![image](https://user-images.githubusercontent.com/5442305/128863928-fe10132f-6bb9-46e2-94c3-640db8b9b91e.png)


5.	Under cockpit menu, select data configuration.

![image](https://user-images.githubusercontent.com/5442305/128863952-329f2ca4-fd0c-441a-9f97-cf3448c3126c.png)

 
6.	Under datasets, click on “Add dataset”. Select “DS_BAR_NO_PARAM” and Save.

 ![image](https://user-images.githubusercontent.com/5442305/128863972-f8018f09-3893-45fb-940a-e56d02b202ab.png)


7.	Unser “Data Cockpit Settings”, click on Save.
8.	Under “Cockpit menu”, click on “Add Widget”.

 ![image](https://user-images.githubusercontent.com/5442305/128863977-fd3b526a-d7a7-43d2-b0a1-ccd20d39c71f.png)


9.	Under chart, click on add.

 ![image](https://user-images.githubusercontent.com/5442305/128863999-47018e29-cacb-4ff5-beb3-4d1c1bbf6514.png)


10.	On the “Dataset” tab, select the dataset we added previously.

![image](https://user-images.githubusercontent.com/5442305/128864020-47599155-7f80-4c66-b216-53b2478d1a80.png)

 
11.	On the “Chart Engine Designer”, under “Chart” tab, select Bar as the style.

 ![image](https://user-images.githubusercontent.com/5442305/128864093-e8e3dbd9-f447-4b60-ba19-a6e1b8c7da2c.png)


12.	 On the “Structure” tab,click on MONTH and MONTH_NUM to be the category.  Click on REVENUE, COSTS_STORE and SALES_STORE to be the Y axis.

 ![image](https://user-images.githubusercontent.com/5442305/128864111-eafbcbc4-00f6-4f4a-b433-2cf5d1b993b8.png)


13.	Under “Categories”, select ordering column.

 ![image](https://user-images.githubusercontent.com/5442305/128864131-08f128d9-9f96-4473-a52c-b6e02078852f.png)


14.	Select MONTH_NUM to be ordering column and type to be ascending. This way months will be ordered from January to December.

 
![image](https://user-images.githubusercontent.com/5442305/128864141-5de6dc96-ead6-4ef4-8c48-da9a39db783c.png)


15.	Under configuration tab, change the chart title to “Revenue by Month”. Change the font as desired.

 ![image](https://user-images.githubusercontent.com/5442305/128864230-854d64bf-7786-464d-b9fa-a9f85dd8d6a5.png)


16.	On the “Style” tab, select “Show borders” with properties shown below.

 ![image](https://user-images.githubusercontent.com/5442305/128864240-9b9f3650-5aa3-4f69-a3d5-976e7dd2f286.png)


17.	Now let us add some additional colors.

 ![image](https://user-images.githubusercontent.com/5442305/128864258-40dcf8bd-a5c9-4765-bb13-46d4685dd152.png)


18.	And legend.

 ![image](https://user-images.githubusercontent.com/5442305/128864284-804feb54-91fb-454a-b77f-e2eba6ef9f37.png)


19.	Save the cockpit as “Revenue”

 ![image](https://user-images.githubusercontent.com/5442305/128864304-ff25426a-a81f-4fda-b083-5a4ba4747d99.png)


20.	 Execute the document.

 

![image](https://user-images.githubusercontent.com/5442305/128864319-7293a119-d9ce-4faa-8ff9-02abbc4d79b1.png)






Assignment.

Using the already created documents and data set, modify your cockpit to look like the one shown below.

 

![image](https://user-images.githubusercontent.com/5442305/128864343-b43135b2-c0fc-47f4-adf1-9dcb06056c6c.png)





