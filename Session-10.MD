# Recap of MVN 

* Maven is a build tool , primarly used building the JAVA Projects 

# Repositories:
1. Local Repo  - .m2/ 
2. Remote Repo - Private Repo
3. Central Repo - Public repo 

# Goals:
1. compile  - Class file in the server 
2. test     - Unit test cases 
3. pacakge  - Creates a artifact .war/.jar 
4. install  - store the artifact in to the local repository (.m2/)
5. deploy   - it going to push the artifact to the remote repo from local repo 
6. clean    - clean the previous stuff 

```
mvn compile  >> create some class files 
mvn compile  >> 
mvn clean compile 
```

# pom.xml 
* Information about artifact , versions , dependencies for the code to be build 

* /usr/share/maven/conf/settings.xml - Global configuration 
* ~/.m2/settings.xml                 - User Configuration 

* Jfrog - User configurations of settings.xml 

# Note : Run the ```mvn compile ``` from the folder where the pom.xml is present. 

* When you want to push the Artifact from local repo to Remte repo using ```mvn deploy``` . You need to setup a section called distributionManagement in the pom.xml 

# Skip test results failure :

```
mvn install -Dmaven.test.skip=true
mvn install -DskipTests-true

```

# Pull request :
* Generally when people want to merge the code to the master branch .T hey will create a pull request , so that it can be reviewed by the lead, sr colleagues in your team. Then can approve or reject by reviewing . 
* PR can also have conditions like atleast 1 or more people need to approve to merge the code 