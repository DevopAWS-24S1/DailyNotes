# Basic DevOps Pipeline Recap 
# Maven:
* Maven is a build automation tool , primarly it is used for Java projects 

# Build Tools :
* Java >> maven , ANT , Gradle 
* .net >> MsBuild , Dotnet Build 
* C  >> make , GCC 

# If you want to build the code :
1. VM in AWS 
2. git clone repourl
3. Install maven 
4. cd gitrepo 
5. mvn package

# Install Maven :

```
sudo apt update 
sudo apt install maven -y 
mvn -version
```

# Build the code :
* mvn package 
* compile -- This goal compiles the source code of the project and create the class files
* test -- This goal runs the unit test cases of the project 
* package -- This goal creates the pacakage (artifact)- .war /.jar 

* mvn package = mvn compile + mvn test + mvn package 

* install - The package wil be stored in to the local repository 
* deploy -  It is going to store the package to the Remote repo from the Local repo 

# Repositories in Maven :
1. Local Repo 
2. Remote Repo 
3. Central Repo 

# pom.xml
* When mvn tries to build the code , it checks for the file called pom.xml
* pom.xml contains the artifact, Verion, Dependencies , plugins