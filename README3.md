MODILE 3
--------

GIT, Jenkins & Maven Integration
================================

### Reference:
    https://maven.apache.org/

### Branch:
    A branch is essentially is a unique set of code changes with a unique name. Each repository can have one or more branches.Branches help us take these different directions,test them out and in the end achieve the required goal

### Merging:
    Merging integrates the canges made in in different branches into one single branch
    
### How to Install Merge-Conflict Tool
    sudo apt update
    sudo apt install kdiff3

    # Configure to the GIT
    git config --global merge.tool kdiff3

    # Open Merge Conflict files
    git mergetool

### GIT Rebase:
    Git rebase used when changes made in one brach needs to reflect in another branch
    (Re-write the History)
    
    git rebase <branch-name>

### GIT Revert:
    Revert or undo the changes made in the previous commit

    git revert <commit-id>

### GIT Reset:
    Reset Command can be used to undo changes as different levels
        Types:
            1. Soft
                git reset --soft <commid_id>
                (Remove from Local repo but Available in Staging Area)

            2. Mixed
                git reset --mixed <commid_id>
                (Remove From Local and Staging Area but Available in Working Directory)

            3. Hard
                git reset --hard <commid_id>
                (Remove from Local,Staging and Working Directory and No backup)

    git reset <modifier> <commit-id>

### Types of Workflow:
    1. Centralized Work flow
    2. Feature Branching
    3. Gitflow 
    4. Forking Workflow

## MAVEN

    (Note: Apache ant  replaced by MAVEN)

    Maven is a tool that is used Compile,Validate codes, and analyse the test-cases in the code.Maven is a build automation tool used primarily for Java projects

    ###
    1. Build our Application
    2. All the configuration in maven are made in pom.xml
    3. Maven follows a specific naming convention (Group id, Artifactid, Version)
    4. Maven has distributed Architecture System

    # Dependency for Maven & How to Install:
        1. Maven needs JDK 1.8 
        2. sudo apt install maven

    # Command for  MAVEN
        1. mvn clean (Clean the Project--> remove already build projects)
        2. mvn compile (To compile the source code)
        3. mvn test (To test the Appliction)
        4. mvn package (To package the application --> jar(Normal java Application),war(Web Application),ear(Enterprise Application))
        5. mvn install (Install the Package)

### How to Create a MAVEN PROJECT
    mkdir maven-project && cd maven-project
    mvn archetype:generate -DgroupId:com.edureka.app -DartifactId=maven-demo 
    -DarchetypeArtifactId=maven-archetype-quickstart -DarchetypeVersion=1.4 -DinteractiveMode==false -DgroupId=143 -Dpackage=hazeevali

    mvn clean
    mvn compile
    mvn test
    mvn package

    # Display
    java -cp target/maven-demo-1.0-SNAPSHOT.jar com.edureka.app.App

    # How to  Work MAVEN
        1. Read POM.xml  ---> (Project Object Model)
        2. Download the Dependency into local repo  (jars)
        3. Execute life cycles, build phase and/or goals
        4. Execute Plugins

### Continuos Integration: (Jenkins)
    It is the process ofautomating the building and testing of code, each time one of the team member commits changes to version control

        Development ===> Source control ===> Build ===> testing ===> Report     (Automate the process Every single commits)

    Tools:
        Gitlab, Jenkins, CodeShip, Bamboo, Teamcity

    Why Jenkins:
        A Continuos Integration server which mnages and control process such as plan, code, build, test, deploy,operate and monitor in devops Environment and Good plugin support
    


