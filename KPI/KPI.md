**Strategy**

Businesses normally do not operate compulsively but they follow a well-defined plan to achieve a certain business objective. This involves setting goals and providing resources needed to meet those goals. This high level plan is called a strategy. 

**Performance measurement**
Once you have come up with a strategy, you need a way of monitoring the progress of executing it, otherwise, you may not meet the objectives you set out to accomplish. You do this through Performance measurement and it involves setting up performance measures. The performance measures are the indicators that track implementation of your strategy.

**Key performance indicators**

KPIs (Key Performance Indicators) are performance measures used to check performance of an organization. Remember that the KPI must align with your goal otherwise you will be measuring something that is not relevant to achievement of your objective. There are very many KPIs that one can use but we will limit our discussion to only one as it cuts across all industries, profit. We will use profit as our KPI and show you how to define this in Knowage. Note that any business that is not tracking its profit or loss will not be open for long. It is a very important financial metric.

**KPI in Knowage**
Now that we understand what KPIs are and the importance of performance measurement, we want to demonstrate how to perform performance measurement using Knowage. We will assume that we want to measure the gross profit of an organization by subtracting the costs from sales. To simplify this example, we will be using the query below which uses random numbers in MySQl to simulate the values of store sales, store cost and measurement date.

SELECT RAND()*(20000-10000)+10000 as STORE_SALES,RAND()*(10000-0)+0 as STORE_COST,now() as TODAY_DATE
If you run the query, you will get the result below.

![image](https://user-images.githubusercontent.com/5442305/128865391-d451e5be-760d-4ff2-9245-27fd20fd8c62.png)

 
We will divide the creation of KPI document into several steps as outlined below.
STEP 1 – Measures definition.
Remember from our definition of KPI that they are performance measures used to check performance of an organization. What we want to measure for now is profit and so this will be our performance measure. We need to define the profit measure in Knowage as the first item. Follow the steps outlined below to do this.
1.	Under KPI model, select “Measure/Rule Definition”.

![image](https://user-images.githubusercontent.com/5442305/128865455-186f0b8d-6406-4692-9792-b0cb914d037d.png)
 

2.	Click on the “Plus” icon.
3.	Under the “Query” tab, use the query below.

![image](https://user-images.githubusercontent.com/5442305/128865474-a67839e8-7851-4cf4-a1d9-b3f1bf55490a.png)
 

4.	On the metadata tab, we need to tell Knowage which of the columns returned by our query are measures or attributes. We have two measures, the store sales and store cost and one attribute, the date.

 ![image](https://user-images.githubusercontent.com/5442305/128865499-db8a7529-e0c0-4a2b-8927-4a27d50305ce.png)


5.	We have not defined any alias or placeholder so skip these and click on Save. Give the definition the name “Profit Measure”.

 ![image](https://user-images.githubusercontent.com/5442305/128865512-d25d18f0-d0c1-42bc-a329-8d3d5ae8ae9b.png)


6.	Close
STEP 2 – KPI definition.
Once we have measure, we need to define the KPI itself. To do this, follow the steps below:
1.	Under KPI model, select “KPI Definition”.

 ![image](https://user-images.githubusercontent.com/5442305/128865541-2901dc9f-645c-40cf-92d5-5c0fa92ea165.png)


2.	Click on the “Plus” icon.
3.	Under the “Formula” tab, press control key together with space. Select STORE_SALES.

 ![image](https://user-images.githubusercontent.com/5442305/128865558-0fae1142-0cb9-4239-88fd-158fde111349.png)


4.	Click on the function and select sum and then apply.

 ![image](https://user-images.githubusercontent.com/5442305/128865571-857ceb99-df95-4779-ab34-ce562435f92a.png)


5.	Press tab to get out of the function, then put a minus sign and repeat the procedure for store cost. From the below image, you can see that we have built the formula for gross profit i.e summing all sales and taking away the sum of costs.

 ![image](https://user-images.githubusercontent.com/5442305/128865591-4fcbc9dd-4fd0-4e4b-aea0-a8648ddc6e8e.png)


6.	On the “Cardinality” tab, there is nothing to change so skip.

 ![image](https://user-images.githubusercontent.com/5442305/128865606-ded9383c-7031-4105-bd53-9c5c8fcb6447.png)


7.	Next we need to create a threshold. Click on “add new threshold item”. We will have a range of three. From 0 to 5000, 5001 to 8000 and 8001 to 20000. We will then color the first range red, the second orange and the last green. This means that if the profit is below 5001, then it will show as red in the KPI tool and when profit hits 8001, it will be in the green region as the target will have been met.

 ![image](https://user-images.githubusercontent.com/5442305/128865625-d1f1ba4d-77f8-41b2-bbfd-8d426228db26.png)


8.	Save both the threshold and KPI definition.

 ![image](https://user-images.githubusercontent.com/5442305/128865644-d2b78a0b-2ef6-41f8-aa8a-614a244d817a.png)


STEP 3 – KPI Scheduler.
The next step is to define when the KPI will be executed by use of the KPI scheduler. Follow these steps to do this:
1.	Under KPI model, select “KPI Scheduler”

 ![image](https://user-images.githubusercontent.com/5442305/128865673-0e83d988-c776-4bc8-ab8d-ddfd48104068.png)


2.	Click on the “Plus” icon.
3.	Under “KPI” tab, click on “Add KPi associations” and select the “Profit KPI”.

 ![image](https://user-images.githubusercontent.com/5442305/128865687-5e80a7c4-79f3-4bf6-b5a1-7f9dedff20b5.png)


4.	There are no filters defined so skip this tab.
5.	Under “FREQUENCY” tab, select the Start date to be today and stop executing this KPI at the end of the year. We will be executing it every minute to allow us test.

 ![image](https://user-images.githubusercontent.com/5442305/128865712-5cd7912e-0a4d-4241-bca3-d5f93e16eef6.png)


6.	Save the scheduler.

 ![image](https://user-images.githubusercontent.com/5442305/128865738-88c8d3ee-b409-435f-b145-318dd6217d16.png)


STEP 4 – KPI Document.
The last step is to create the KPI document itself. Follow these steps:
1.	Create a generic document with the following properties.

 ![image](https://user-images.githubusercontent.com/5442305/128865764-788af7d1-2b3b-4e44-8e5f-c75c3a279eeb.png)


2.	Click on the “Template build”
 
3.	Under “KPI LIST”, click on “ADD KPI ASSOCIATIONS” and select “Profit KPI”

 ![image](https://user-images.githubusercontent.com/5442305/128865795-31be9fcf-c108-434b-8879-4c9b2db05843.png)


4.	Under “View As”, select speedometer. For minimum range use 0 and maximum 20000.

 ![image](https://user-images.githubusercontent.com/5442305/128865807-1ab524f6-f722-4347-8536-b8bfb9a6b473.png)


5.	Under options, select everything.

 ![image](https://user-images.githubusercontent.com/5442305/128865821-60f1bfef-1662-4b3a-8e93-fab3e5426ff7.png)


6.	Save the template and execute document.

 ![image](https://user-images.githubusercontent.com/5442305/128865833-8033b269-6626-47a9-bc5c-d5b298b9bc0e.png)


If you change template to use KPI card, this is what you will get if you execute document so the choice is yours.

 
![image](https://user-images.githubusercontent.com/5442305/128865876-1217c454-2dbd-40b3-94f2-537a916e1ed7.png)




