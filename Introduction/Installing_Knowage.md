**Installing Knowage**  
We will be using the Community Edition of Knowage so go to the link http://forge.ow2.org/projects/knowage  and select Knowage Server. As at writing this tutorial, the version that was available for download was Knowage Installer 6.0.0 CE. Select this version and download for your platform. 

![image](https://user-images.githubusercontent.com/5442305/128587754-d3888461-2860-4266-a985-b27d5df30de4.png)

Secondly, download and install MySQL as it will be needed by Knowage. MySQL can be downloaded from https://www.mysql.com/downloads/
When you begin installation of Knowage, the first screen will be the welcome screen.  Click on Next on this screen.

![image](https://user-images.githubusercontent.com/5442305/128587810-37c832a4-ea40-4efd-8c5c-21a4e912c9c7.png)

 
On the next screen, you need to accept the GNU AFFERO GENERAL PUBLIC LICENSE and click on next.
![image](https://user-images.githubusercontent.com/5442305/128587815-e4779504-9eab-4bad-a116-6ef0108762c9.png)

 
On the next screen, we will select Chart.js as the other options are not open source. If you have license for or you want to pay for Highcharts JS, then you are free to do so.

![image](https://user-images.githubusercontent.com/5442305/128587827-5da5700d-3c12-495e-9b9a-be73a27fe4c4.png)

We will be installing all modules of Knowage so select everything on the next screen.

![image](https://user-images.githubusercontent.com/5442305/128587829-8b455156-6579-4227-b876-bad7fafb127a.png)

Then select the destination directory. We will install in C:\knowage\server and click Next.

![image](https://user-images.githubusercontent.com/5442305/128587833-070bffa9-2591-4de8-9d97-55f17e279552.png)

On the next screen, you will be asked for MySQL settings.  This will create a database called knowage_ce that will hold the Knowage metadata. Click on Next.

![image](https://user-images.githubusercontent.com/5442305/128587841-744f1bcc-0bff-4845-9c7f-0e2e38a9a81e.png)


Once everything has been specified, installation will begin.

![image](https://user-images.githubusercontent.com/5442305/128587847-8f71300c-0ec2-4850-ae85-1fb5a56f5753.png)

 
Once the installation is complete, you will get the screen below. Click on Finish for it to create desktop links for starting and stopping Knowage.

![image](https://user-images.githubusercontent.com/5442305/128587859-8a268c98-e745-4a05-b97b-8c4e1ef69c22.png)

 
**A word about Metadata**
Knowage Community Edition needs a database to store its own data for authorization, schedules, configurations, alerts and several other things. This information is called metadata and is stored in the MySQl database that you provided above. If you navigate to the MySQl database knowage_ce, you will find several tables created by Knowage installer as shown below. These are the metadata tables.

![image](https://user-images.githubusercontent.com/5442305/128587865-1019b918-c9cc-4ac7-91a0-d6ff1a39bfb8.png)

 

