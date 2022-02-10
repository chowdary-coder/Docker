MODILE 4
--------

Continuos Integration using Jenkins
===================================

### Architecture

    Devops Engineer ==> git ==> Automate Build (Maven) ==> Automate Testing (selinium) ==> Automate Deployment ==> QA ==> Production

    ( 1. Checkout the code from Repository
      2. Compile Source Code
      3. Exicuting Unit Test Cases
      4. Generate Code Coveraage report (Cobertura)
      5. Execute Static code analysis  (PMD)
      6. Package myApplication )
## Sapmple Example for CI

### Manual Installation

    Source = https://github.com/edureka-git/DevOpsClassCodes.git

    mkdir maven-project && cd maven-project
    git clone https://github.com/edureka-git/DevOpsClassCodes.git
    mvn clean
    mvn compile
    mvn test
    mvn package

    # Generate the Code Coverage Report
    mvn cobertura:cobertura
    # Display
    java -cp target/maven-demo-1.0-SNAPSHOT.jar com.edureka.app.App

### Jenkins

    # How to Install Maven in Jenkins
        Manage Jenkins ---> Global tool Configuration --> Add Maven

    # How to add a Plugins in Jenkins
        Manage Jenkins ---> Plugin Manager

    # How to Create Master & Slave in Jenkins
    (When we  need run Parllel nodes we use master &  Multiple slave )
        Manage Jenkins ---> Manage Nodes & Clouds --> New Nodes

### Automation (Install Automate):
    Step: 1
    # How to Create a User
        Jenkins Dashboard ---> People ---> Create User ---> User Details --> Create
    
    Step: 2
    # User permissions
        Jenkins Dashboard ---> Configure Global Security --> 

        # Authorization
            1. Anyone can do anything                       | Anyone can do Anything
            2. Legacy mode                                  | Its Allow to Existing/Old Projects
            3. Logged-in users can do anything              | Once login with Cedentials he can do Anything
            4. Matrix-based security                        | We can create User groups and give the permissions to Anonymus user/Login User
            5. Project-based Matrix Authorization Strategy  | We can create User groups and give the permissions to Anonymus user/Login User based on Specific Project

    Step: 3
    # How to Install Maven in Jenkins
        Manage Jenkins ---> Global tool Configuration --> Add Maven

    Step: 4
    # Create a New Item
    Types of Items:
        1. Freestyle Project            | Just drag and drop purpose
        2. PipeLIne                     | it is used to create a own pipeline for Automation
        3. Multi-Configuration Project  | It is Suitable for Large no.of Configurations
        4. Folder                       | Create folder to store
        5. Multibranch pipeline         | Create a Multiple branch Pipeline
        6. Organization Folder          | 

    # Build Triggers: 
        1. Trigger builds remotely              | Trigger Remotely from Scripts
        2. Build after other project are built  | Setup a Dependency of the project (Order of Projects)
        3. Build periodically                   | Set up a time when we need to Build
        4. Github hook triger for GITScm pilling| Git hub to calling to trigger then we need to build
        5. Poll SCM                             | When new commit in GITHUB the build start

    # 
### Cretae a Project Item: (single Project)
    A Jenkinsfile can be written using two types of syntax -
        1. Declrative
        2. Scripted

    # How to crete SMTP Server
        Note: SMTP Server is Responsible for sending the mail and POP3 server is responsible for Receiving the Mail

    # How to  Create a `PIPELINE Project`:
        jenkins Dashboard ---> New Item ---> Pipeline Project ---> Add Git link (General-> Github Project) ---> Pipeline ---> Apply and save

        1. For Publish Html Reports need to add plug-in 'HTML Publisher plugin'
        2. For Deploy need to add plug-in 'Deploy to container Plugin'

    # Syntax of PIPELINE
    ## Scrpted Script ##
        ' node {
            stage('Code Checkout'){
                git 'https://github.com/edureka-git/DevOpsClassCodes.git'
            }
            stage('code compile'){
                sh 'mvn compile'
            }
            stage('compile test'){
                sh 'mvn test'
            }
            stage('Code Analysis'){
                sh 'mvn pmd:pmd'
            }
            stage('Publish Html Reporets'){
                publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: false, reportDir: '/var/lib/jenkins/workspace/Deploy Pipeline Project/target/site/', reportFiles: 'POM.html', reportName: 'HTML Report-POM', reportTitles: ''])
            }
            stage('Package Application'){
                sh 'mvn package'
            }
        }'

    ## Declarative Script ##
        'pipeline{
            agent any
            stages{
                stage('code chekout'){
                    steps{
                        git 'https://github.com/edureka-git/DevOpsClassCodes.git'
                    }
                }
                stage('build and package'){
                    tools{
                        maven 'Maven01'
                    }
                    steps{
                        sh 'mvn package'
                    }
                }
        
            }
        }'   

### Create a Project Item: (Multiple projects)

    Step: 1
    # Create a Project: (Compile Test)
        jenkins Dashboard ---> New Item ---> Free style Project ---> Add Git Link (Source Code Managment) & Select the Mster Branch ---> Select Build Environmet ---> Build (Select the Option ==> Invoke top-level Maven Target) --->  Select the Maven Version & Provide the Goal '(ex: test)' ---> Apply ---> save

    # Add Projects (After creating all Projects):
        Jenkins Dashboard ---> Select project ---> Add post-Build Action (in Build) ---> Add Project Names (second) ---> Apply and Save

    Step: 2
    # Build the Project:
        Jenkins Dashboard ---> Build Now

    Step: 3
    # Create a Project for 'CODECOVEREGE': (Code Coverage)
        jenkins Dashboard ---> New Item ---> Free style Project ---> Add Git Link (Source Code Managment) & Select the Mster Branch ---> Select Build Environmet ---> Build (Select the Option ==> Invoke top-level Maven Target) --->  Select the Maven Version & Provide the Goal '(ex: cobertura:cobertura)' ---> Apply ---> save

    # Add Projects (After creating all Projects):
        Jenkins Dashboard ---> Select project ---> Add post-Build Action (in Build) ---> Add Project Names (Third) ---> Apply and Save

    Step: 4
    # Build the Project:
        Jenkins Dashboard ---> Build Now

    Step: 5
    # Create a Project for Code Analysis: (Code Analysis)
        jenkins Dashboard ---> New Item ---> Free style Project ---> Add Git Link (Source Code Managment) & Select the Mster Branch ---> Select Build Environmet ---> Build (Select the Option ==> Invoke top-level Maven Target) --->  Select the Maven Version & Provide the Goal '(ex: pmd:pmd)' ---> Apply ---> save

    # Add Projects (After creating all Projects):
        Jenkins Dashboard ---> Select project ---> Add post-Build Action (in Build) ---> Add Project Names (Fourth) ---> Apply and Save

    Step: 6
    # Build the Project:
        Jenkins Dashboard ---> Build Now

    Step: 7
    # Deploy the Application: (Deploy Application)
        jenkins Dashboard ---> New Item ---> Free style Project ---> Add Git Link (Source Code Managment) & Select the Mster Branch ---> Select Build Environmet ---> Build (Select the Option ==> Invoke top-level Maven Target) --->  Select the Maven Version & Provide the Goal '(ex: package)' ---> Apply ---> save


    Step: 8
    # Build the Project:
        Jenkins Dashboard ---> Build Now

    Step: 9
    # Add a Build-Plugin
        Jenkins Dashboard ---> Manage Plug-in ---> Available (Click Option) ---> build pipeline ---> Install

    Step: 10
    # Add a Dependencies
        Add the Dependencies (Create the Queue --> Which project is which Dependency)

    Step: 10
    # Create Build Pipeline
        Jenkins Dashboard ---> Click plus Symbol ---> Create a Pipeline view ---> Create Initial Job ---> 

    Step: 11
    # Deploy The Application:
        1. Download the Apache tomcat9
        2. Add Plugin Deploy to container (In Jenkins)
        3. Create a Pipeline Script with tomcat credentials
        4. Add the Script on Deploy application stage

### Jenkins Master-Slave Architecture
    The Jenkins master acts to schedule the jobs, assign slaves, and send builds to slaves to execute the jobs. It will also monitor the slave state (offline or online) and get back the build result responses from slaves and the display build results on the console output. 

    # How to  Create a Jenkins Master-Slave:

    # Step: 1
    # Change the Security Permissions to Connnect Node
        Jenkins Dashboard ---> Mnage jenkins ---> Configure global tool security ---> Select option Random in agent ---> Apply and Save 

    # Step: 2
    # Create a Node:
        Jenkins Dashbooard ---> Manage  Jenkins ---> Manage Node and Clouds ---> New Node ---> Add Remote Directory (/var/lib/jenkins) ---> Save

    # Step: 3
    # Add a Slave node to Master Node:
        Open the Jenkins on slave node (With master ip) ---> Down load agent.jar file ---> Run the command
    
    # Example command:
        ***Note:Incase we getting JVM Error,we need install 8 verion***
        java -jar agent.jar -jnlpUrl http://localhost:8080/computer/Slave%2Dnode/jenkins-agent.jnlp -secret 7ddc88b4b72a42c802c17f8bad3af440d4abd45aaa2a7127e611f5ff22504dc4 -workDir "/var/lib/jenkins"

    Step: 4
    # Buildthe Application through SlaveNode;
        Follow the Create a Project Item (Multiple projects) Steps and Modify the Script
    
    # Script
        node ('slave-node'){
            ****Script****
            # This is thetxt csse for git diff
        }

### Slave node Setup:
    
    # Install Maven in Ubuntu (Slave Node)    
        sudo apt update
        sudo apt install maven

        java -jar agent.jar -jnlpUrl http://localhost:8080/computer/Slave%2Dnode/jenkins-agent.jnlp -secret 7ddc88b4b72a42c802c17f8bad3af440d4abd45aaa2a7127e611f5ff22504dc4 -workDir "/var/lib/jenkins"
    
