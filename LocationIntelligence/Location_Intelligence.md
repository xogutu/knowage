**What is Location Intelligence?**

Location Intelligence is the integration of Business Intelligence and Geographical data. This gives a visual representation of the data on a map.

![image](https://user-images.githubusercontent.com/5442305/128625566-e3ba2d4d-9667-4235-a879-a4ed09674986.png)

Consider the document above. This is a document that shows the number of livestock that are at risk due to famine to be used by a disaster preparedness organization. For
the policy makers, it would be easier to understand as they will be interested in regions with red color. You can see that we have different tones of green color on the map. The regions which have a higher tone like Upper Eastern have more livestock at risk compared to other regions. 

In this chapter, we will learn how to create such documents. The document shown above is created using both an SVG map and an xml template. Apart from the map and the template, you will also need a source of data. So we need
to understand how to create these 3 components:

1.	An SVG map.
2.	An XML template.
3.	Data source.

The Problem.
Assume you are a consultant for the Kenya Red Cross and you are tracking an upcoming famine in the month of August. You have data from various provinces and regions in Kenya and you would like to put them in a map so that you can project it in the big screen on the conference room. The map will be updated automatically as data comes from the provinces.

Solution.
To solve this problem, we will need two things:
•	We will need the data. For this exercise the data is in the table livestock_by_county in the database bidb.
•	We will need to create an SVG map.

SVG or Scalable Vector Graphics is XML based standard. We will be creating the map of Kenya with its various regions. We can do this with a free tool called Inkscape or you can use Corel Draw if you have a license for it. Instead of starting from scratch, follow these steps to create a map based on an already existing map. If you are good with inkscape or Corel draw, you can skip this and draw your own SVG map. Note that if you are not interested in creating the svg map, there is already an existing one under the folder “Location Intelligence” with the CD that came with this book. It is called Kenya_Map.svg. If you chose not to create the the map, jump to step (iii) otherwise follow the following steps to create the map.

Creating SVG map with Inkscape.

1.	Navigate to the link below to download a sample SVG map that we will modify. http://upload.wikimedia.org/wikipedia/commons/2/2c/Kenya_location_map.svg

2.	Once the map is opened in your screen, take a screenshot of the page and crop the image using Microsoft Paint or any tool of your choice. Save the image as Kenya.png. If you open your file, it should look like below.

 ![image](https://user-images.githubusercontent.com/5442305/128625582-f82c3c07-3159-42e1-b692-8262b2430fb2.png)

We will use this image as the base of our SVG map since we do not want to  waste time drawing the map of Kenya with all its borders.

3.	Download and install Inkscape.

4.	Open Inkscape.

5.	Go to File->Open then Select the PNG image we had downloaded above.

6.	Select embed.

 ![image](https://user-images.githubusercontent.com/5442305/128625586-f7c82370-d283-4012-b129-deded2ccbc49.png)

7.	You can see that the regions are already separated by lines so we will just use a fill tool with white color to segment and name each region we need. We will start with Upper Eastern, (III) on the map.
 
![image](https://user-images.githubusercontent.com/5442305/128625591-b7d59801-5199-4494-bbd2-c19676dc2f50.png)

8.	Click on the fill tool (I) then select the green color (II) and then click on the area III. The map will change as show below.

![image](https://user-images.githubusercontent.com/5442305/128625606-c71cf12f-149f-499f-b0d1-c9cdb5591d9e.png)

9.	To see how this region will look like in xml, use the selection tool to highlight it (I) then click on Edit - > XML Editor (II).

 ![image](https://user-images.githubusercontent.com/5442305/128625613-b3e17d7f-5232-4863-ad74-ffd1cbbc6372.png)

10.	Click on id (I) and on box (III), type the name of the region you had selected as “Upper North Eastern” then click on “Set”.

![image](https://user-images.githubusercontent.com/5442305/128625621-9f90496c-a514-4978-ab7d-1eac33a72aca.png)

Note that the fill color is 00FF00 i.e green. We need to change it back to white so click on fill and change it to fill:#ffffff i.e white. Why are we doing this? We do this because once we are done with naming all regions, they should all be white and will only take the color based on data from the database. Click on Set to make the changes permanent.


11.	Next we need to give the region a label so using the text tool, label it as “Upper North Eastern” as shown below.

 ![image](https://user-images.githubusercontent.com/5442305/128625628-d1e35840-59ac-43f9-8dac-2713e365b7a5.png)

12.	We are finished with the region “Upper North Eastern”. Now do the same for “Lower North Eastern”.

![image](https://user-images.githubusercontent.com/5442305/128625638-f70acb7e-d394-42d2-aa0e-a5cabff89350.png)

 
13.	Finish the other areas. Your map should look like this.

![image](https://user-images.githubusercontent.com/5442305/128625648-2af64787-be73-4ed9-b5ca-7d3c98bc3f79.png)

 
14.	Now we need to select all regions and group them. Name this new group “county”. How do you do this? Click on a region, say “Western” then hold down the shift key and then click on the other regions. Once all the regions are selected, to group them, go to object and select group.


15.	When you look at the xml, it should be as shown.

 ![image](https://user-images.githubusercontent.com/5442305/128625656-85eeccc0-c60a-48f8-b43e-7fb4e242e191.png)

Note that all regions are under the county group. So how will Knowage know how to color the various regions based on the data from the database? It will compare the names of the regions against a column called county in the database. This column will have names similar to the various regions in the SVG map. So always ensure your group name is same as the column name where the region names are stored. See below for a sample table we will be using for this assignment.

![image](https://user-images.githubusercontent.com/5442305/128625661-b1d183d6-bb59-4485-863b-03831ad352fb.png)

IMPORTANT:

Open the SVG with a text editor, search for style="fill:#ffffff;stroke-width:1.1509186" or equivalent and replace with fill="#ffffff". We have noticed that if you use the first one, then your map will not be filled with color coding in Knowage!


Now save the file as Save.svg.Your map is ready!

**SVG Catalog**

Now that we have the map, let us load it into Knowage. Login to Knowage as user biadmin and under Catalogs select SVG.

 ![image](https://user-images.githubusercontent.com/5442305/128625669-5fbbf3ad-7b98-414b-a62a-e0d6dcd9107a.png)

Click on Insert. Under name use KENYA_PROVINCES. For Description use “Kenyan Provinces”.  Enter “Kenya” as Hierarchy and 1 for Level and lastly county for Member. Then for Template, browse for the file we created in previous step or if you did not create it, you can use the map in the “SVG\Kenya.svg”  from the resources folder that came with this book. Click on Save once you are done.

![image](https://user-images.githubusercontent.com/5442305/128625673-248551a7-93db-453b-a3b8-8e901734f6d8.png)
 
**Template**

Now we that we have finished with the map, let us create the location intelligence
document template. Most documents in Knowage needs a template that defines the structure and source of data and the location intelligence document that we are going to create is no different. Remember up to this point, we have managed to create the SVG map to be used in the document and saved it in Knowage with the name KENYA_PROVINCES. The template we are going to create has the structure outlined below and will be rendered with the SVG Viewer Engine.

NOTE: If you do not want to type in your own template, you can use the template that
came with this book under “SVG\Kenya_Livestock.xml”.

The HIERARCHY tag must match what we had used when saving the SVG file in Knowage catalog. In the MEMBER tag, we need to specify the dataset where data will come from as measure_dataset and the level must match what we had used in the SVG catalog.

 ![image](https://user-images.githubusercontent.com/5442305/128625692-96852ab0-b479-413c-ac17-f879ea2799cd.png)
 
Dataset
The final piece that is missing is creating the data set. From Knowage, create a dataset with same name “kenya_county” which is what we have specified in the template above. It should read from the table “livestock_by_county”. This is from the database bidb that came with this book.

![image](https://user-images.githubusercontent.com/5442305/128625696-67bfb257-de74-4045-92bd-8c479033239f.png)

Create a document with the properties shown below

![image](https://user-images.githubusercontent.com/5442305/128625707-a24d8e9f-1c25-41c8-a906-3467d1ae06eb.png)

Save your document and execute. You will get the results below. Now highlight on any area, having in mind that the stronger the color, the more livestock at risk in that area.

![image](https://user-images.githubusercontent.com/5442305/128625714-2e7e9a15-bf03-4bb2-9d12-78261a64dc9b.png)





