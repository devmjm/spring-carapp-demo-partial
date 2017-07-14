# spring-carapp-demo-partial
Partial CarApp demo of Spring Boot REST Service

## Tutorial 1: Hello World
https://spring.io/guides/gs/rest-service/
Note: use Maven (not Gradle)

## Tutorial 2: CarApp - Basic REST Service
<b>Tutorial Purpose:</b> The purpose of this tutorial is to demonstrate how to create a basic RESTful web service using Spring Boot, Maven, and PostgreSQL. The four major REST operations are demonstrated (GET, POST, PUT, DELETE). This tutorial intentionally excludes detailed steps on configuring your STS and PostgreSQL environments, as these steps are already well documented in numerous other resources.

### Configure PostreSQL…
1. Install PostgreSQL
2. Create new PostgresSQL database named 'CarApp' (username = postgres, Password = demoPass)
3. Initialize the schema by running script located at:  

### Configure STS Workspace…
1. Clone the CarAppPartial project from https://github.com/devmjm/Demo to your STS workspace
2. Open this project in STS
3. Run the project as a 'Spring Boot App' and confirm it compiles and runs
4. Stop the project

### Start Building the REST Service…
1. Review the "REST Basics" resource below to familiarize yourself with REST
2. Navigate to the CarController. Note that there are GET, POST, PUT, and DELETE methods outlined.
3. Fill in the logic for these methods in accordance with RESTful standards (http://www.restapitutorial.com/lessons/httpmethods.html). Your methods should return the following responses:

### Test Your Service…
1. Run the project as a 'Spring Boot App'
2. Use Postman to make REST requests to your service
3. Confirm you are able to achieve the behavior described in step 3 above.
