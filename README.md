# spring-carapp-demo-partial
This is project is a collection of tutorials to learn about creating a RESTful web services using Spring Boot, Maven, and PostgreSQL. Start with Tutorial 1 to familiarize yourself with Spring Boot. Then, move on to Tutorial 2 to learn about RESTful web services.

## Tutorial 1: Hello World
https://spring.io/guides/gs/rest-service/
<br> <i> Note: use Maven (not Gradle) </i>

## Tutorial 2: CarApp - Basic REST Service
<b>Tutorial Purpose:</b> The purpose of this tutorial is to demonstrate how to create a basic RESTful web service using Spring Boot, Maven, and PostgreSQL. The four major REST operations are demonstrated (GET, POST, PUT, DELETE). This tutorial intentionally excludes detailed steps on configuring your STS and PostgreSQL environments, as these steps are already well documented in numerous other resources.

### Configure PostgreSQL
1. Install PostgreSQL
2. Create new PostgreSQL database named 'CarApp' (username = postgres, Password = demoPass)
3. Initialize the schema by executing the script located at:
<br/> https://github.com/devmjm/spring-carapp-demo-partial/blob/master/Scripts/CreateAndPopulateCarappDb

### Configure STS Workspace
1. Clone the CarAppPartial repository from https://github.com/devmjm/spring-carapp-demo-partial to your STS workspace
2. Open the CarApp project in STS
3. Run the CarApp project as a 'Spring Boot App' and confirm it compiles and runs
4. Stop the project

### Start Building the REST Service
1. Review the "REST Basics" resource below to familiarize yourself with REST
2. Navigate to the CarController. Note that there are GET, POST, PUT, and DELETE methods outlined.
3. Fill in the logic for these methods in accordance with RESTful standards (http://www.restapitutorial.com/lessons/httpmethods.html). Your methods should return the following responses:

| VERB         | URI                          | Request Body         | Expected Response                                          |
| :---         | :---                         | :---                 | :---                                                       |
|GET           | localhost:8080/cars          | N/A                  | HttpStatus OK (200). <br/> List of all cars in your database.|
|GET           | localhost:8080/cars/{vin}    | N/A                  | HttpStatus OK (200). <br/> Car with vin is returned |
|POST          | localhost:8080/cars/         | { "Vin": 9, "Driver": "fb35753c-668c-11e7-ae07-d790c545bb70" } | HttpStatus Created (201). <br/> Car created created              |
|DELETE        | localhost:8080/cars/{vin}    | N/A                  | HttpStatus OK (200). <br/> Car is deleted. |
|PUT           | localhost:8080/cars/{vin}    | {	"Vin": 111, "Driver": "fb35753c-668c-11e7-ae07-d790c545bb70" }| HttpStatus OK (200). <br/> Car is updated. |

### Test Your Service
1. Run the project as a 'Spring Boot App'
2. Use Postman to make REST requests to your service
3. Confirm you are able to achieve the behavior described in step 3 above.

### Further Help
A completed version of this demo can be found at: https://github.com/devmjm/Demo/tree/master/CarApp

## Tutorial 3: Deploy CarApp Demo to Azure
<b>Tutorial Purpose:</b> The purpose of this tutorial is to get an introduction to Azure. You will deploy the CarApp you built in Tutorial 2 as an Azure Web Service. Instead of using your local PostgreSQL instance, you will point your application to a pre-configured Azure SQL database.

### Update the CarApp to use Azure SQL Database
1. Replace your application.properties file with the below values. Ask a team member to provide the username and password for the database.
```
spring.datasource.url=jdbc:sqlserver://fuller-sql-dev1.database.windows.net;databaseName=FULLER_SQL_DEV01
spring.datasource.username= {db username}
spring.datasource.password= {db password}
spring.datasource.driverClassName=com.microsoft.sqlserver.jdbc.SQLServerDriver
spring.jpa.show-sql=true
spring.jpa.hibernate.dialect=org.hibernate.dialect.SQLServer2012Dialect
spring.jpa.hibernate.ddl-auto=validate
```

2. In the pom.xml file, remove the dependency for PostgreSQL.
3. Add the dependency below for Azure SQL Server:
```
<dependency>
   <groupId>com.microsoft.sqlserver</groupId>
   <artifactId>mssql-jdbc</artifactId>
   <version>6.2.1.jre8</version>
</dependency>
```

### Deploy the CarApp as an Azure Web Service
To deploy the CarApp as an Azure Web Service, follow the steps outlined here: 
https://docs.microsoft.com/en-us/azure/app-service-web/web-sites-java-custom-upload

### Test the CarApp Service
Test REST endpoints outlined specified in the "Start Building the REST Service" section of Tutorial 2. In the request URLs, replace "localhost:8080" with the domain of your web application. 

## Additional Resources
- REST basics: https://spring.io/understanding/REST
- REST Standards: http://www.restapitutorial.com/lessons/httpmethods.html
- Advanced REST tutorial: https://spring.io/guides/tutorials/bookmarks/
- Deploy Java web app to Azure: https://docs.microsoft.com/en-us/azure/app-service-web/web-sites-java-custom-upload
