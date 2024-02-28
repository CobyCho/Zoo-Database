# Zoo-Database
Inside this google drive Folder “ZooWeb Submission folder” you will find this README, Project Document, and Dump.bacpac.
Inside of the file named “Project Document” you will find a detailed documentation of our Database and how it is designed which includes our the types of data weve included, different roles on the website, the triggers and semantic constraints that accompany them, and the queries/reports that we have implemented.
How to use our Dump file:
To load the database locally using our dump.bacpac file, connect to a local server in Microsoft SQL Server Manager. Right click on the Databases file and select Import Data-tier application. Then select the dump.bacpac file. You should now be able to view our database locally.
Follow this link to our github to view everything there - https://github.com/zanecaa/ZooWeb
Here is where the website is hosted: https://zooweb20231125232946.azurewebsites.net/
Accounts:
Admin - Username: zooadmin, Password: password
Employee - Username: zookeeper, Password: password
Visitor - Username: zaneca, Password: password
Steps to clone the repository to our website:
Make sure you are using Microsoft Visual Studio with .net7
Under the get started menu locate the “clone a repository” option and click it.
Under the “repository Location” field paste this github link (https://github.com/zanecaa/ZooWeb) and choose the path you want to save it to.
From here you will have complete access to view all code associated with our website
If from here you would like to connect to our database on Visual Studios please follow these steps:
You will need the azure dev tools to accomplish this, if you do not have them you must first get them from the Visual Studios Installer and install them
Once inside of the Visual Studios solution Click “VIew” and then click “SQL Server Object Explorer”
Inside of the SQL Server Object Explorer locate “Add SQL Server” and click that
In the server name field paste “zoowebdb.database.windows.net”, for username paste “zooadmin”, for Authentication choose “SQL Server Authenticaton“, and for password paste “peanuts420!” and then click connect
You should now be connected to our database inside of the Visual Studios environment where you can view all tables alongwith the SQL code associated with them.

