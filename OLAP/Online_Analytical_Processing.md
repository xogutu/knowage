**OLAP (Online Analytical Processing)**  



|**Prepare the database**  | 
| ----------- | 
| The data for this assignment is in the MySQL dump foodmart.sql. If you have not already done so, load the MySQL dump in your database so that you follow along. Secondly, you will also need the csv file OLAP.csv and Microsoft excel to perform comparisons between OLAP and Pivot tables.      |

Online Analytical Processing (OLAP) enables one to analyze different dimensions of multidimensional data. It enables one to analyze data from different perspectives. Consider
sales data as an example. One might be interested in analyzing sales data in terms of the date
when the sale occurred, the region the sales occurred and the store the sales occurred. The
sales amount we are analyzing is called a measure. The way we analyze the measure (sales
amount) is called a dimension. Therefore, the sales date is one dimension of looking at the sales
data; the store where the sales occurred is another dimension of looking at the sales data. We
can therefore look at the sales data by date, by store etc.

To help you understand measures, dimensions and star schema, we would like to demonstrate using simple data with one dimension and one measure for a fictitious company Shemma Global.




|**Below is a sample problem description:**  | 
| ----------- | 
|Shemma Global is a Business intelligence company that specializes in data mining and analysis. They would like to view the memory usage of one of their servers by event time. The server event logs are stored in a MySQL table as shown below.|

![image](https://user-images.githubusercontent.com/5442305/128617461-8663fb75-b9ac-42c8-abca-c83288073a1d.png)

From the diagram above, we are only interested in two columns, the event_date and used_memory (highlighted in blue). The event_date is our dimension (how we would like to view the data) and the used_memory is the value we would like to measure (the measure).
Normally dimension data like date, sales region e.tc are not stored in a fact table which has measures but in a dimension table. A foreign key is then included in the fact table to link the two . Consider a telecommunication company as another example. We would make the fact table the central table in our schema surrounded by dimension tables as shown below. We call this kind of schema a star schema.

![image](https://user-images.githubusercontent.com/5442305/128617465-b9b487fa-5353-4e39-91fa-14e88c1595a9.png)


In the above example, it is easy to answer questions like how many mobile phone subscribers
were activated in the last quarter or how many subscribers are postpaid or prepaid. If we were to build an OLAP document for this assignment, we would build a single fact table (Table 1) and link it to the dimension tables using foreign keys.

**OLAP Cube**

An OLAP cube is a collection of measures (facts) and dimensions. In the telecommunication
example above, we can create a cube which can answer questions like how many subscribers
were activated on a certain year, certain quarter or certain month, or how much airtime was
consumed by customers from Nairobi region or how many subscribers are in pre-paid.


If you run a business, you might want to monitor several aspects of it to help you in planning and decision making. You may want to know your customer behavior for example, the number of men as opposed to women who patronize your business so that you create a specific product or service for them. You might also want to monitor which product is performing well so that you order more or which is not doing well so that you cancel its production. You might also be interested in stores that are losing money so that you make a decision on whether to close them or make changes in the processes or leadership. From this discussion, we see that a business can be viewed from different perspectives which can be time, product, customer, store etc.   
The different perspectives are called dimensions when using OLAP (Online Analytical processing). We can therefore see that most analysis is multidimensional. If you only have a single dimension to consider e.g. time in month, then you do not need an OLAP tool and can use a spreadsheet for example, as shown below in figure OLAP1.

![image](https://user-images.githubusercontent.com/5442305/128617483-e8ea816f-ea77-48de-a51a-7091635d3206.png)

Fig. OLAP 1

However, we know that businesses are normally complex and we have many variables to track. For the remainder of this chapter, we will use the sample data shown in figure OLAP 2 below to aid in our discussion.

![image](https://user-images.githubusercontent.com/5442305/128617486-6b3fb4b2-fa5c-4d6b-8def-da86da747f15.png)

This data is from the sample foodmart database that comes with the SpagoBI All in one installation. All we have done is to convert it from HSQLDB to both MySQL and Excel which we will use to demonstrate OLAP. From the excel data in figure OLAP 2, there are six dimensions that we want to track namely product, sales month, sales quarter, sale year, customer and store. The three measures that we are interested in are store sales, store cost and unit sales.
To aid us in understanding OLAP in Knowage, we would like to present a simple problem and solve it using excel. Once we understand how to do this in excel, it will become clear why OLAP is a superior solution than excel.

***Problem description:***

Sega Food Limited is a private company that owns several food stores throughout Kenya. The General manager would like a report that summarizes:
1.	The total store sales per store summarized by year, quarter and month.
2.	Ability to compare sales between years.
3.	The total store cost summarized by year, quarter and year.

***Solution:***

Open the Excel CSV file Store Sale.csv that came with this book. You will notice that under worksheet Store Sale we have 251,359 rows of data that we want to analyze. The first column is the product name, the second column contains the month the product was sold, the third column has the sales quarter, followed by sales year, customer account, store name, store sales, store cost and lastly unit sales as shown below.

![image](https://user-images.githubusercontent.com/5442305/128617507-786fc980-1357-4395-a4f5-4674d9e565ec.png)

The second worksheet Pivot, contains a pivot table that has the summaries of the data and can therefore be used to answer the questions outlined above. So let us walk through them one by one.

What is the total sales per store summarized by year, quarter and month?

Before we can answer the question above, we need to understand what we are measuring. In this case, it is sales per store. The question is, how do we need to look at the store sales? How do we want to summarize it? This brings in the idea of time dimension. We want to summarize the store sales using time but in what hierarchy? First, we will need a summary for the year, then the quarter and lastly the month. So to use OLAP terms, store sales is the measure, and we have three dimensions; year, quarter and month.  The dimension hierarchy is:
1.	Year
2.	Quarter
3.	Month

***Solution 1: Excel***

We can solve this using pivot table in excel as shown below. You can click on the worksheet pivot on the file Store Sale.csv  to see how it is done.

![image](https://user-images.githubusercontent.com/5442305/128617525-383cac56-e0d4-4ef8-8ef7-e8e9740a42ae.png)

From the pivot table above, we can get the total sales for each store summarized by year, quarter and month.  Let us take Store 11 for example, we can see that for 2011, the total sales for this store was ***55,044.29*** (cycled in yellow). The total sales for quarter 2 was ***14,333.48*** (cycled in red) and sales for October was ***4,077.27*** (cycled in blue).

***Solution 2: Knowage***

Let us compare results above to what we would get if we used OLAP in Knowage.   

![image](https://user-images.githubusercontent.com/5442305/128617546-135b88ac-0d6e-48ec-897c-4d4ba8c562de.png)

Just like in excel, we can see that the store sale values for 2011 is ***55,044.29*** and total sales for Quarter 2 is ***14,333.48***. So the values are the same. The question therefore is, why should we use OLAP tool in Knowage if excel does the same thing and is easy to use? There are several advantages of using Knowage over excel namely:

1.	Knowage supports several datasets both traditional and big data.
2.	It is easy to share as all you need is a browser.
3.	It is secure and supports profiles for different users.
4.	Supports what-if analysis
5.	There is a limit to how much data excel can accommodate where as Knowage is limited only by system resources and underlying DBMS or data source.


