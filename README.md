# SAP-Data-Warehouse-Cloud-
A repository to get hands-on experience with SAP DWC and build your first Data Warehouse

## Prerequisites:
SAP Data Warehouse Cloud 30-day free trial account

This guide is divided into four modules, by the end of the six modules you should be able to do the following:
* Implement data governance measures by assigning users to roles and define access for each user respectively
* Add more users in bulk as you scale your data warehouse across the organization
* Create spaces and assign users to spaces
* Establish remote connections and load data from SAP HANA and upload local files to the cloud
* Build ER models to define relationships between datasets
* Construct a basic data model in graphical view
* Build an analytical dataset with defined *Measures* and *Dimensions*
* Add business information to semantic layer
* Create interactive data stories


## Important keywords:


Spaces: these are virtual workspaces for an individual or a group of users for data modeling, data integration, and story dashboard building. Think of them as your isolated business functions such as Marketing, HR, Finance, Business Development, etc. 


Semantic Layer: this is where you give the data business meaning according the audience, organizational best practices and naming conventions. 


Entity Relationship Modeling is a database modeling technique that aims at establishing a diagram or visual representation of a system’s data.There are three basic elements in an ER Diagram: entity, attribute, relationship.

***

![alt text](https://ibb.co/pQ2MgNP"><img src="https://i.ibb.co/2SqCwR6/Capture.jpg)



### Module 1: Data Governance Measures and Spaces
Navigate to *Security* and click on Users. You should have a table to add users and their respectives roles. Note that only one **system owner** can be assigned to each data warehouse. The license is a feature to manage the number of concurrent users logging into the data warehouse. You can adjust it if needed.

Navigate to *Space Management* and add a space called Bike Run Sales. The space can be assigned quotas for available disc space, CPU usage, runtime hours, and memory usage. There are useful icons at the top to indcate if one space is overused or underused. 



### Module 2: Data Ingestion
In the same space, nagivate to *Connections*. Click the ➕ icon to add a connection. You can add a connection to an existing SAP HANA database if you are using it. Else, you can manually upload the excel files. Note that you can also add a connection to any ETL tool that speaks SQL using the *Open SQL Schemas*. <br/>
For local file uploads, navigate to *Data Builder* and create a table. You can upload CSV file directly but that didn't work for me. After creating the table, add business purpose of the table to keep some metadata and add columns as necessary. You can define data types and any constraint related to each column. Click on *Save* and *Deploy*. Note that the upload will only be available after you deploy the table. 




### Module 3: Build ER Model
Navigate back to the *Data Builder*, Go to *E/R models*. Click on New Entity Relationship Model to create one. On the left, there will find a list of all the tables uplaoded in the previous step under the *Repositories* tab .<br/>
Drag and drop the tables to connect Sales_Orders dataset to Sales_Order_Items and create the asscoiation based on the SalesOrderID. Repeat the same process for Sales_Orders, Business_Partners dataset and Addresses dataset and create the association based on the common keys, PartnerID and AddressID, respectively. Click on save and deploy to make the model available for use in the next step.



### Module 3: Build Data Model
Navigate back to the *Data Builder*, Go to *Views*. Click on New Graphic View to create one. On the left, there will find a list of all the tables uplaoded in step 2 under the *Repositories* tab .<br/>
Drag and drop the tables in the following order. Add Sales_Order_Items first and then add Sales_Order on top of it to INNER JOIN the two tables. Next, add Business_Parterns table and then JOIN it with Addresses table. At the end of the data model, you should have a View dataset that has the cumlative Inner Join of all tables. <br/>
Click on the View and rename it as desired. Change the *Type* from relational to analytical dataset. This will make it easier to analyze the data and draw visualizations in the following step. There are two categories now, *Dimensions* and "Measures*. Change [Quantity, GROSSAMOUNT_ITEMS, GROSSAMOUNT_ORDERS] to measures and leave all the dimensions as is.
Next to Attributes, click on the ✏ icon to add semantic layer to the data. Change the *Semantic Type* as seen fit. <br/>
Now save the dataset and click on the toggle bar to allow the dataset for consumption then deploy.



### Module 4: Build Business Story
Navigate to the *Story Builder*, Go to *New Story*. Click on add data and choose the dataset saved from the pervious step. The story can be built in several ways according to the business questions at hand. Two important features to highlight. One, the filter feature from input controls can apply filter by dimension across all charts. Two, the *linked Analysis* can link all the charts together so in the case of hovering over one product_id, you get to see its related information only. 


A list of possible questions answered by the Story in this repo are the following:

1. What total sales are by Region?
2. Which products are most selling, in which countries and regions?
3. Should we focus more on the low cost/high volume bikes or high cost/low volume bikes?
4. Can we break down sales by clients? 
5. Which clients are purchasing which of the top selling products?




I hope you find this helpful for you to start using SAP data warehouse right away. Stay tuned for more of these guides on other cloud providers. Meanwhile, connect with me via LinkedIn [here](https://www.linkedin.com/in/marwa-ahmed98/) 
