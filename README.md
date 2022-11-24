# <u>Project Service Documentation</u> :
### 1. Project Set Up And Build Locally :
a) `git clone` the Project Service repo and checkout to the dev branch and `git pull` [https://gitlab.mynisum.com/pmotracker/project-service.git]

b) In the terminal, cd to the path "ms-project-service" then run the command:
```maven
mvn clean install
```

Build them separately by running the command:
```maven
mvn clean install
```
d) Try to build _**ms-project-service**_ again.
### 2. Copy properties from Git Repository :
Go to GitLab repository "***Config Service***" and copy
project service properties from there [https://gitlab.mynisum.com/pmotracker](https://gitlab.mynisum.com/pmotracker/config-service/blob/dev/app-config/project-service.properties)
and paste them in a new file, should be created in resources folder named as "application.properties".

### 3. DataBase Connectivity :
Update the username and password in the application.properties as your local mysql username and password.
Go to any mysql design tool which is connected with the application and create database there with the name _**project_service_db**_ by executing the command
```sql
create database project_service_db;
```
### 4. Run the Application.
Run the project, check the logs for the _"Tomcat started on port(s): 9898"_ message and check the swagger endpoint for api documentations [http://localhost:9898/swagger-ui.html](http://localhost:9898/swagger-ui.html)

### 5. Verify Repositories on nexus :
Find the link of nexus present in a pom.xml [https://nexus.mynisum.com:8443/](https://nexus.mynisum.com:8443/)
Go to that link by entering the credentials provided by the project leads
then go to Browse -> maven-snapshots -> pmotracker -> com -> lib-commons and check the Snapshot version there if version is the same as
the local version then the nexus is connected locally successfully.

Check also for the ms-project-service, go to Browse -> maven-snapshots -> pmotracker -> com -> msproject -> ms-project-service
and check the snapshot version, if the version is the one present on local environment then the nexus connectivity is verified.

### 6. Config server errors :
Check the run logs and maven logs, there will be a couple of errors like _**IllegalArgumentException**_, _**IllegalClassFormatException**_,
_**IOException**_, or _**TransportException**_.
Please ignore these exceptions or errors as some of these errors are due to the Eureka Client or cloud related errors which will not occur
after the deployment of the application on the cloud for sure, but they will continue to show up on local environment.
To get rid of some errors, comment out the properties in bootstrap.properties file.

### 7. Postman Collection :
Check the "postman-collection" folder in "resources" folder. In that folder there is a file named "project-service-api-collection.json"
Try to open the file in postman and populate variables with relevant data and run the collection for testing the apis.

For creating the postman collection of apis, go to postman, in collections tab click import and select link tab and paste the link of swagger docs and click continue.
After a couple of seconds, the collection of apis will be appeared along with extra folders and sub folders. Move the apis and place them in folders same as in swagger docs.
