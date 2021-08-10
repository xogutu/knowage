Introduction to GIS

In this chapter, we will learn how to integrate Knowage business intelligence software and a geographic information system (GIS). Business Intelligence systems are used to provide useful information from the millions of transactions done by businesses daily while GIS systems are used to analyze all types of geographical data. The marriage of these two systems provides a powerful platform that is used for visual analysis of data that can be appreciated by even non-technical users. This is not a chapter on GIS but rather a chapter on integration of GIS and Business Intelligence. However, the reader does not need to have any background training on GIS or Knowage because we will be introducing these concepts gradually and even readers new to these technologies will be able to pick up.

 ![image](https://user-images.githubusercontent.com/5442305/128825047-e2b10741-e140-440d-a7c6-458d189e407d.png)


Introduction to GIS 
So what is GIS? We can say that it is any system that stores and analyses geographical data. Several software does exist in the market that fills this role. Such software includes both desktop and browser based variants such as Bing Maps, ArcServer, Google Earth, Arcmap and QGIS. We will be using the free QGIS for this tutorial. 

When dealing with GIS, we normally store two types of data: 
1.	Attribute data – This is textual data that describes features in the map for example population information about countries. It basically says what a feature is. 
2.	Spatial data – This describes where the feature is to be found and is made up of coordinates and other information about map features. Further, spatial data can either be vector based or raster based. Vector based data uses paths to render the image while raster uses pixels. In this book, we will see how to represent several features in a map as vector consisting of points, lines, and areas. We will also use raster data. Do not worry about this verbose description, it will become clearer once we begin the practical exercise.  


To aide us in learning GIS, we will be using a real world problem and providing its solution. So let us first understand the problem outlined in Scenario one below.


Scenario one 
The SpagoBI training website www.learn-spagobi.com has several students from different countries all over the world. The owner wants to map the students in a map of the world so that he can easily see which countries has the most users of his website. This will allow him to customize the courses to better suit his audience. How can we use Knowage and GIS to achieve this?

Solution
 
 ![image](https://user-images.githubusercontent.com/5442305/128825104-efbdd69a-092a-48f2-aa9e-1b4be222bdbf.png)


Diagram 1 


Diagram 1 shows a sample location intelligence document that meets this need. We will create a document similar to this in Knowage. If you look at diagram one keenly, you will notice several things:


1.	Colored cycles are used to represent countries that has students in learn-spagobi.com. The size of the cycle denotes the number of students. A bigger cycle will represent more students in a country as opposed to a smaller cyle. Later on in the course, we will also see how to use thematic points with different colour coding to denote this. 

2.	The map has attribute data that gives more information about a country if a cycle is clicked. For example, when we click on the cyce on Kenya, it tells us that the ISO code for Kenya is KE, it gives us the population, longitude and latitude e.t.c. We will learn how to add our own attribute data, how to modify existing attribute data and how to reat attribute data from a relational database to make it dynamic. 

3.	Lastly, we note that this map came from existing sources like google map or any other source with up todate maps. We will use maps from http://thematicmapping.org but you can follow along with maps from your own sources. 


![image](https://user-images.githubusercontent.com/5442305/128825137-6df88877-39d8-4002-9c4d-22dff4eec077.png)

QGIS

To help us provide a solution to what have been described in scenario one, get started with Knowage and GIS, we will first need to download and setup a GIS software that we will need to manipulate and view the maps that we will then be analyzed together with additional data, by Knowage. 

So what is QGIS? Wikipedia gives a very good summary of what this software is. Here is what they say about it. QGIS (previously known as "Quantum GIS") is a cross-platform free and open-source desktop geographic information system (GIS) application that provides data viewing, editing, and analysis capabilities. Similar to other software GIS systems QGIS allows users to create maps with many layers using different map projections. Maps can be assembled in different formats and for different uses. QGIS allows maps to be composed of raster or vector layers. Typical for this kind of software the vector data is stored as either point, line, or polygon-feature. Different kinds of raster images are supported and the software can perform georeferencing of images. 
(http://en.wikipedia.org/wiki/QGIS) 

Now if you check our requirements for scenario one above, you see that the first thing we need is a world map. It is in the countries in this map that we will put cycles to denote a country where a student resides, the bigger the cycle, the more students we have in that country. Since we are not in the business of creating maps, we will need to download the world map from somewhere. Again as we do not want to pay for this map, we can get one from a reputed public source. Then once we have the map, we can use QGIS to modify its attributes. Follow these steps.



1.	Download QGIS Desktop 2.8.2 from https://www.qgis.org/en/site/forusers/download.html 
2.	Install the QGIS software in your machine. It will come with several other software that we will not be using e.g GRASS GIS 6.4.3, MSYS and QGIS Browser 2.8.2 and SAGA GIS (2.1.2). We are only interested in QGIS Desktop 2.8.2. 
3.	From your desktop or start menu, click on QGIS Desktop 2.8.2. icon. It has the icon similar to the one below. 

4.	This will open the QGIS desktop. 

 ![image](https://user-images.githubusercontent.com/5442305/128825194-deb25d9f-d259-4728-a9a7-62d0ed3fb77c.png)


5.	Now what we need is a map that we can manipulate in the QGIS software. Since in SpagoBI we need to show location of all students that have enrolled at learn-spagobi.com from all over the world, we will need to download a world map. You can get one from here http://thematicmapping.org/downloads/TM_WORLD_BORDERS-0.3.zip The file comes in a format called a shape file which is a data format for GIS systems. The zip file when extracted will contain several files: 

a.	A file with the extension .shp which has the geometry data.
b.	A file with the extension .shx which is the index for the .shp file. This allows you to go backwards and forward on the .shp file faster,much like indexes do in a book or a relational database.
c.	A file with the extension .dbf which stores attributes for each shape. This file is in the dBase format.
d.	A file with the extension .prj which has the coordinate system and projection information in the Well-known text (WKT) format.

6.	Extract the map to the location E:\BI\TM_WORLD_BORDERS-0.3. You will notice that the map comes as several files as discussed above. 
a.	TM_WORLD_BORDERS-0.3.dbf 
b.	TM_WORLD_BORDERS-0.3.prj 
c.	TM_WORLD_BORDERS-0.3.shp 
d.	TM_WORLD_BORDERS-0.3.shx 

7.	Now in QGIS, go to Layer Menu. Select Add Layer and click on Add Vector Layer as shown below. 

 ![image](https://user-images.githubusercontent.com/5442305/128825242-b54aafb7-e146-4e4d-967e-812982ac4db8.png)


8.	Browse and select the TM_WORLD_BORDERS-0.3.shp file then click on open. 

 ![image](https://user-images.githubusercontent.com/5442305/128825259-bdee0b0f-f142-43fb-a273-93897ad7081e.png)


9.	It will load the map. Now let us look at the attributes of this map. Under Layers, right click on TM_WORLD_BORDERS-0.3 and select “Open Attribute Table” 

 ![image](https://user-images.githubusercontent.com/5442305/128825279-77cea52c-44e5-474e-86ac-03427674b088.png)


10.	 This will allow you to view the attributes of the shapes. Do you remember, from our discussion in step 5, in which file these attributes are stored?

 ![image](https://user-images.githubusercontent.com/5442305/128825293-7f555328-873c-4e4a-ac27-9c3e371468ac.png)


In future, we will be using QGIS to change some of these attributes, modify column names, delete attributes, change color of maps, make them transparent etc. but for now, that will suffice for the introduction to QGIS.


GeoServer

Once we have modified the attributes of the map we had downloaded in QGIS, we will need a way of publishing or distributing it to Knowage. We do this using another software called GeoServer. This server allows you to share your map with a large audience who will just need a URL to be able to access it. So now let us go to http://geoserver.org/ and download the latest version of GeoServer in my case version 2.7.1.

Extract the file to the location C:\BI\geoserver-2.7.0-bin\geoserver-2.7.0 or any free location in your computer. Geoserver by default uses the port 8080 so you might want to change it to something else since SpagoBi also uses this as the default port. So open the file C:\BI\geoserver-2.7.0-bin\geoserver-2.7.0\etc\jetty.xml and change the port to 8090

 ![image](https://user-images.githubusercontent.com/5442305/128825325-25c01873-6161-4f9d-ae5c-b888ee198a47.png)

Then use the batch file on C:\BI\geoserver-2.7.0-bin\geoserver-2.7.0\bin\startup.bat to startup the Geoserver.

 ![image](https://user-images.githubusercontent.com/5442305/128825359-313e53f0-ee6c-4170-98d5-7fb73a9f9dac.png)

Open a web browser and navigate to the URL http://localhost:8090/geoserver/web which is the Geoserver URL. Login with username admin and password geoserver. The first thing we need to create is a workspace. A workspace is used to organize the items you will be creating in Geoserver. So to create a workspace, click on Workspaces (Arrow 1) then select Add new workspace (arrow 2)

![image](https://user-images.githubusercontent.com/5442305/128825394-29381b0a-1495-44e0-8ce4-80f2c9332f3d.png)

 For name, enter learnspagobi and for the URI use http://learn-spagobi.com and make it the default workspace then click on submit.

 ![image](https://user-images.githubusercontent.com/5442305/128825423-d6eab648-998c-42e9-9769-a7d0c974d269.png)



Next, we need to create a store. The store will be used to connect to a source of data which can either be vector or raster. In our case, we will create a store which will connect to the shapefile which we modified using QGIS previously. Remember, you can also have the data store come from a database for dynamic maps. 
Click on stores (arrow 1)and select add new store (arrow 2).

 ![image](https://user-images.githubusercontent.com/5442305/128825450-a72a7d41-8798-466f-90fa-23dd4b80e08c.png)



Select the first option, which is “Directory of spatial files (shapefiles)”

![image](https://user-images.githubusercontent.com/5442305/128825473-08f48c9b-5eca-4f34-947e-0dfcf1e23cef.png)
 
For workspace, use the workspace we created previously. For Data Source Name , use WORLDMAP. Put any description you like. Then under Connection Parameters, browse for the directory where we have the file TM_WORLD_BORDERS-0.3.shp and select it then click on save.

 ![image](https://user-images.githubusercontent.com/5442305/128825510-b19b683f-951d-4026-97f3-68d6664f2ab3.png)

On the next screen click on publish.

 ![image](https://user-images.githubusercontent.com/5442305/128825537-024faf25-1d71-4dd3-996d-74346e4d08d9.png)


Under Declared SRS (arrow 1) , enter EPSG:4326 and for SRS handling (arrow 2), use “Reproject native to declared” then under “Lat/Lon Bounding Box” click on “Compute from native bounds” (arrow 3) then save.

 ![image](https://user-images.githubusercontent.com/5442305/128825557-c07b23c2-615f-4b8a-a082-11982ef87fad.png)


This will automatically create for you a layer called TM_WORLD_BORDERS-0.3. This is the layer that we will call from Knowage. So let us check that it is working. Click on layer preview then search for your workspace you just created. Then click on OpenLayers KM.

 ![image](https://user-images.githubusercontent.com/5442305/128825571-de22a4a0-ef20-4e79-9179-c8b20d6a7a61.png)


If you have done all the steps correctly, you can see that the map will be rendered. If you click on any area of the map, it will show you details about it. If you check the image below, you can see that we selected China. You can also zoom in and out of the map. 

![image](https://user-images.githubusercontent.com/5442305/128825600-e06b559e-b725-4563-b13a-b4c27bf48cdb.png)


GeoJSON

You can directly call the map from geoserver in Knowage but we will show you how to use an offline method by converting the map to a GeoJSON file that you can use even without an additional overhead of geoserver. Follow these steps to create a GeoJSON file.

1.	Under layer preview, in “All Formats”, scroll down to “WFS” and select “GeoJSON”.

![image](https://user-images.githubusercontent.com/5442305/128825639-b6a623ed-4959-4495-aa7c-9eba671d0950.png)
 

2.	Click on “Raw Data”.

 ![image](https://user-images.githubusercontent.com/5442305/128825662-9d88a318-f32e-4310-b2d3-6ff18c084c6f.png)


3.	Click on copy, paste in a text editor like notepad and save the file as “World.json”
4.	Next, we need to create a layer catalog in Knowage using this file so that we can use it to create GIS documents.
5.	Under catalogs, select “Layers catalog”

 ![image](https://user-images.githubusercontent.com/5442305/128825685-2e44546e-873f-46a5-b4de-4afe42969bb0.png)


6.	Enter data as shown below then Save.

 ![image](https://user-images.githubusercontent.com/5442305/128825707-16b8bc08-2f01-4d13-bf83-36536d4423c1.png)

We will stop there for now, load some data into Knowage and see how to analyze it together with this map.




Knowage with GIS
We have now learnt how to modify our map data using QGIS and how to publish this map in the Geoserver ready for use by any map consuming application like Knowage. 
Like we had stated before, we will use the following scenario to help us make a sample map.


The scenario: 

The SpagoBI training website www.learn-spabobi.com has several students from different countries all over the world. The owner wants to map the students in a map of the world so that he can easily see which countries has the most users to his website. This will allow him to customize the courses to better suit his audience. How can we use Knowage to achieve this?

From the scenario above, you can see that we need several things. 
1.	We need a world map. We have already loaded one in Geoserver and is ready to be used by Knowage. 
2.	We need the student data that defines which country they come from so that we can link it to the map data. 

To achive number two above, that is load the student data, we will need to login to Knowage and create a dataset called “SpagoBI Students” with the contents of the file GIS/Learn-spagobi.com Users.csv which came with this book, proceed as follows:

Login to Knowage as user biadmin password biadmin. Navigate to Data Providers
 -> Data Set. 

 ![image](https://user-images.githubusercontent.com/5442305/128825773-aaa9efbd-f057-468c-8e22-dd7406c4efcf.png)


Create a new dataset called DS_SPAGOBI_STUDENTS.  Under detail tab, enter the following:

![image](https://user-images.githubusercontent.com/5442305/128825796-e5ec7f1b-e9d3-4eb0-9f5f-ae2ec7dce3a8.png)

Under type, select file and upload the Learn-spagobi.com Users.csv file that came with this book.

![image](https://user-images.githubusercontent.com/5442305/128825839-d43cd3ea-dffb-4cfb-beff-cdd54a6af59a.png)

 Put the delimiter and quote character.

 ![image](https://user-images.githubusercontent.com/5442305/128825871-cde598b8-a627-4185-9a0a-ae4e40848fe7.png)


Preview the file and if all is fine, save.

 ![image](https://user-images.githubusercontent.com/5442305/128825891-76da0e5a-6032-4df1-9b57-0cc516399d4b.png)


IMPORTTANT: - You should change STUDENTS to be of type measure otherwise you will have a problem when trying to create indicators in the Knowage GIS template.







GIS Document

Finally, we are ready to create a GIS document. Follow these steps:

1.	Create a generic document with these properties and click on “Save”.

 ![image](https://user-images.githubusercontent.com/5442305/128825909-2f257148-104a-4f17-8633-a1f75a9fb326.png)


2.	Next click on “Template build”

 ![image](https://user-images.githubusercontent.com/5442305/128825940-bb1fea92-15e3-4dee-9acd-8bf623c63d89.png)


3.	Under “Layer”, click on “ADD LAYER” and select the json file we had saved in Knowage catalog.

 ![image](https://user-images.githubusercontent.com/5442305/128825953-524167a5-399c-4632-acf7-980550d6acf0.png)



4.	Under “Dataset join columns”, click on “ADD JOIN COLUMN”. This is where we link the map with the data from Knowage data set. We will link them using the FIPS column.

 ![image](https://user-images.githubusercontent.com/5442305/128825969-4ca9ef71-7942-4117-9fce-554dae1b05eb.png)


5.	Under “Indicators”, select “ADD INDICATOR”, then select “STUDENTS”. Remember this is the value we want to output in the map. The STUDENTS column has the total number of students per country. Therefore, it will be used to color the map.

 ![image](https://user-images.githubusercontent.com/5442305/128825989-2fca0076-b32e-4ceb-abe4-77b37e0d4c3c.png)


6.	Under “Filters”, select “COUNTRY”. This is what we will use to filter the map data. For example, if we only want to view data for a particular country or countries, we will filter using this column.

 ![image](https://user-images.githubusercontent.com/5442305/128825998-4ade8867-b4c3-4191-a995-a070d86fdaca.png)



7.	Under “Map menu configuration”, select defaults.

 ![image](https://user-images.githubusercontent.com/5442305/128826017-36e9a0ad-e422-4697-b493-13ec881445ef.png)


8.	Save the template.


IMPORTANT: This book also comes with a ready template which you can use by clicking on “Browse” and selecting “World_Template.json” file. The file is in the GIS folder.

 ![image](https://user-images.githubusercontent.com/5442305/128826039-82a8e7dc-c122-45c3-ac5d-d42a775021bf.png)


Now that you are finished with the template, execute the document. The output is shown below.

![image](https://user-images.githubusercontent.com/5442305/128826077-2b8237e7-93e0-4262-9289-2e0da580efee.png)

Let us look at some of the map properties:

1.	Under the Map tab, you can see that the default map type is “Map Zone” as shown below. 

![image](https://user-images.githubusercontent.com/5442305/128826130-ff0a3f65-1dd5-4dd0-9f3b-409f42f4e7aa.png)

2.	However, this can be changed to “Map Point”

 ![image](https://user-images.githubusercontent.com/5442305/128826159-0e115a8e-a821-45af-9805-dbeaa88c2a8b.png)


3.	Since we had only specified on “INDICATOR”, we have it selected by default.

 ![image](https://user-images.githubusercontent.com/5442305/128826175-008b49ee-81ef-4b9b-b163-225cac3c2411.png)



4.	You can use the filter property to select only specific countries. In the example below, we have selected Brazil only.

 ![image](https://user-images.githubusercontent.com/5442305/128826203-597c798e-b908-455a-bdcc-5766099db6c6.png)



5.	You can also use the config tab to change the colors and the method used (either quantile or equals intervals).

 ![image](https://user-images.githubusercontent.com/5442305/128826228-2429a73f-154b-4c0d-8b35-6f8235ffd1b1.png)



Attribute table
If you click on any country, it will give you more information about that country. For example, if we click on Brazil, it will give us information about Brazil as shown below.
 
![image](https://user-images.githubusercontent.com/5442305/128826299-3716c4e1-c400-4d7d-b858-b4e85eb55c3f.png)


So the question is, where do the information like population, longitude and latitude come from? It is not in the dataset we created so where do Knowage get it? It gets it from the attribute table. In case you do not want to display some of this data, you can simply delete it using QGIS, or even add more information to be displayed if someone clicks on a country. We can also read this data from a database to make it dynamic. For the shapefile we used, physically, the information is stored in dBase, a type of database. So how do we view this information and how do we modify it if we need to? We can use the QGIS software to do this. 

Start your QGIS and open the TM_WORLD_BORDERS-0.3.shp shapefile as we had done previously and open the attribute table.

![image](https://user-images.githubusercontent.com/5442305/128826354-ae634a07-763b-4d80-aac4-18fe93410662.png)

 Let us look at the information for Brazil from the attribute table highlighted below in red.

 ![image](https://user-images.githubusercontent.com/5442305/128826383-ff8f3249-5edc-4290-a62e-293df983e89f.png)

Compare this information to what we were getting in Knowage.

![image](https://user-images.githubusercontent.com/5442305/128826403-4c010432-1cf7-4d63-bbf5-c251464fdc97.png)
 

You can see that the data is similar which means that both the data in QGIS and the one in Knowage came from the attribute table. From attribute table, we can see that Kenya’s population is 35 million. Let us change it to 42 million using the editing feature. 

 ![image](https://user-images.githubusercontent.com/5442305/128826428-28bafe89-88ca-4bd3-9d00-fa495043ff40.png)


Then enter the value 42,000,000 in the POP2005 field.

 ![image](https://user-images.githubusercontent.com/5442305/128826451-f7f87a67-a8e8-4b86-a5c5-4e253bd3b6d0.png)

Save your attribute table. Now reload your Knowage document and check if the population information have changed for Kenya. You will find that it is still reading the old values. This is because Knowage is not reading the information directly from the shapefile but from the GeoJson file you created using the Geoserver. So if you want the changes to be visible in Knowage, you will need to reload the shapefile in the geoserver and and create a new GeoJson file then upload to your layers catalog in Knowage.

What if you wanted to modify the column information in the attribute table? You might even want to delete the column entirely. All these can be done using QGIS. Let us say we want to delete the SUBREGION and modify POP2005 to be POP2015.

![image](https://user-images.githubusercontent.com/5442305/128826503-aae72964-f6e8-4c6a-8adc-e446afa63f20.png)
 

To make the changes above, proceed as follows. 
1.	Start the QGIS desktop. 
2.	We will need to download the Table manager plugin to help us modify columns. Click on Plugins then select Manage and Install Plugins… 

![image](https://user-images.githubusercontent.com/5442305/128826534-87cf7d00-b248-499b-b259-c1d822a7f822.png)
 

3.	Search for Table manager then install it. 

 ![image](https://user-images.githubusercontent.com/5442305/128826549-fa9b2445-0a9c-4738-91d0-9dae42e62054.png)

4.	Now, on the left bottom of QGIS, click on the double arrows and click on Table Manager icon. 

 ![image](https://user-images.githubusercontent.com/5442305/128826583-3025f2e4-de24-45f7-aaff-48ca50d75ce6.png)

 
5.	Select POP2005 and select Rename. 

 ![image](https://user-images.githubusercontent.com/5442305/128826602-1cccdfb2-5c19-48da-b51f-86a01594cd61.png)

6.	Change it to POP2015. 
7.	Select subregion and then select delete. 

 ![image](https://user-images.githubusercontent.com/5442305/128826638-331db6dd-2ae0-47c4-aade-a43574381faf.png)

8.	Confirm deletion. 

![image](https://user-images.githubusercontent.com/5442305/128826669-59967b4a-e740-4e03-83f8-93e896b2dc25.png)

9.	Save your new shapefile as World2. 
 
 ![image](https://user-images.githubusercontent.com/5442305/128826695-8c834f68-5091-4b65-8ac7-acb03634c93d.png)


10.	 Use this shapefile to create a new store in geoserver and from it a new GeoJSON file. Load it in Knowage and check if the changes have taken effect.
