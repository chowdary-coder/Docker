MODULE 1
--------

Overview the Devops (Introduction)
==================================

### Traditional Waterfall Model:

    In a waterfall model, each phase must be completed before the next phase can begin and there is no overlapping in the phases. The waterfall Model illustrates the software development process in a linear sequential flow

    Requirment and Gathering Analysis ===> Design ===> IMPLEMENT ===> TEST ===> DEPLOY ===> MAINTENANCE

    # Dis-Advantages:
        1. Time Consuming - Not Effective - Not Productive
        2. Not a good model for complex and long projects
        3. No Customer Feedback
        4. No Way Back (Incase we need back loose Money and Time)
        5. Cost are always High
        6. Delayed Delivery
        7. Make change is very Difficult

### Agile Model:

    "Agile process model" refers to a software development approach based on iterative development. ... Agile methods break tasks into smaller iterations, or parts do not directly involve long term planning. The project scope and requirements are laid down at the beginning of the development process.

    Agile = Deploy --> Build --> Test

    Analyse ===> Plan ===> Agile   Analyse ===> Plan ===> Analyse
    
    # Dis-Advantages:
        1. Operation team stuggle with the Development team
        2. Lack of continuos Monitoring & Communication b/w the operation and Development Team
        3. Unstability in Production

### DEVOPS: (Dev + Ops)

    End 2 End Responsibile for Development and Operation Teams

    # Dis-Advantages:
        1. Knowledge on various tools to Automate

    # Application use in DEVOPS:

        |---------------|-------------------------------|-----------------------|
        | PROCESS       | APPLICATIONS                  | Know's                |
        |---------------|-------------------------------|-----------------------|
        |   PLAN        |  Jira, Trello                 |                       |
        |   CODE        |  Git, Jira, Confluence        | Git                   |
        |   BUILD       |  Maven, Jenkins,Gradle        | Jenkins,Maven         |
        |   TEST        |  Selenium, JUnit              |                       |
        |   RELEASE     |  Bamboo, Gitlab               | Gitlab                |
        |   DEPLOY      |  AWS, Ansible, Chef           | Ansible,AWS           |
        |   OPERATE     |  AWS, Ansible, Chef           | Ansible,AWS           |
        |   MONITOR     |  Nagios, Splunk, DataDog      |                       |
        | ORCHESTRATION |  Kubernetes                   | Kubernetes            |
        |  CONTAINERS   |  Docker                       | Docker                |
        |---------------|-------------------------------|-----------------------|
    
    PLAN ===> CODE ===> BUILD ===> TEST ===> RELEASE ===> DEPLOY ===> OPERATE ===> MONITOR

    # DEVOPS ADOPTION:

        Cultural Transformation ---> Process Transformation ---> Technology Transformtion ---> Automate Everything ---> Adoption of Tools

### DEVOPS LIFECYCLE:
    1. PLAN:    
        First Stage of devops Cycle, Where you plan,Track, Visualize and Summarize our project
    
    2. CODE: 
        Second stage of Devops Cycle, Where the Developer write the Code
        (Git Repo)

    3. BUILD:
        Build is a pre-release version and is Identify by a build number
        (compile + Unit Testing + Packaging (jar, war, ear) --> Docker Image)

    4. TEST:
        Process of executing automated tests as part of the Software delivery pipeline in orderto obtain Feedback
        (Testing the Application {Executing Automated test cases --> Selinum})

    5. RELEASE:
        This Phase help to integrate code into a shared repository using which can detect and locate errors Quickly and Easily
        (Creates final Artefact to be deployed to the Production)

    6. DEPLOY:
        Manage and Maintain development and deployment of software systems and servers in any computational environment
        (Create Infra and Configure Infra)

    7. OPERATE:
        The Phase is to keep the system upgrated with the Latest update
        (Managing --> Kubernetes)

    8. MONITOR:
        It Ensure the  application is performing as desired and the environment is stable.It quickly determine when a service is unavailable and understand the underlying causes.
        (Collecting Logs and Visualization of Reports)
        
### Devops Stages:

    | Agile                     | Plan --> Code --> Build                                |
    | Continuos Integration     | Agile --> Test --> Feedbck                             |
    | Continuos Delivery        | Continuos Integration --> Deploy --> Test --> Feedback |
    | Continuos Deployment      | Continuos Delivery --> Release --> Test --> Feedback   |
    | devops                    | Continuos Deployment --> Operate --> Test --> Feedback |


##########################################################################################################################

MODULE 2
--------

Version Control with GIT
========================

### VERSION CONTROL:
    The practice of tracking and managing changes to software code

    # WHY:
        Version control systems allow you to compare files, identify differences, and merge the changes if needed prior to committing any code.
    
    # TYPES:
        1. Local Version Control --> Only Stored in Local Server
        2. Centralized Version Control --> Stored in Centralized Server
        3. Distributrd Version Control --> Stored in Centralized Server and Local Server
    
### GIT:
    Git is an Open-Source Distributed Version Control system (DVCS) which records changes made to the files laying emphasis on Speed, Data Integrity and Distributed, Non-linear workflows

    # CLONE:
        The creation of an organism that is an exact genitic copy of another 
        (Creting a Replica to the Remote repository Project)
    
    # PUSH:
        The Changes of the Local Repository move to the Remote repository
        (Move to our changes to the Remote Repository)

    # FETCH:
        Bring the latest repository to the Local repository
        (When using Fetch Both Old and New Versions are Available Local Repository)
    
    # PULL:
        PULL = FETCH + MERGE
        Bring the latest repository to the Local repository and Working Area also
        (Get the New Version Working Area and Local)

    Working Directory   Staging Area    Local Repo      Remote Repo

    | --Add-->        | --Commit-->         |  --Push-->    |
    
    | <-------------Checkout -------------- |               |

    |                 |                     |  <---Fetch ---|

    | <-------------Merge-------------------|               |

    | <--------------------------Pull---------------------- |

### GIT COMMANDS:
    # Add File to Staging Area
    **git add .**
        
    # Check Status
        **git status**
    # Commit the staged files to local Repository
        **git commit**

    # Diff between from Local and Working area Repository
        **git diff**

    # Show all the Commits
        **git log**

    # Create a Branch
        **git branch <branch_name>
    
    # Change the Branch
        **git checkout <branch name>

    # Channge the  last comit message using --amend option
        **git commmit --amend**
        
    # Remove from the staging area
        **git rm --cached <reponame/filename>
    
    # Add to Remote Repo
        **git remote add <Alias name (origin)> <git url>

    # Push the Data to repo master
        **git push <alias (origin)> <branch name (master)>**
    
    # Delete the Branch
        **git delete -d <Branch_name>

########################################################################################################################

MODULE 3
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
    


########################################################################################################################

MODULE 4
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
    

##########################################################################################################################

MODULE 5
--------

Configuration Managment using ANSIBLE
=====================================
    Its Automates Provisioning,Configuration managment,Application deployment,Orchistration and Many other IT Process
    Ansible is 'Agentless' (Push based tool)
    Ansible writing scripts in YAML (yet another markup language)
    Push approch to archive the its objectives

### Types:
    Ansible CLI
    Ansible Tower (RedHat) --> Ansible GUI

### Ansible:
    Asible allows users to utomate their environment using two different waays:
        1. Ad-Hoc Commands --> (Used to execute one-off tasks)
        2. Playbooks 

    # Create a New User
        ansible -b -K -m user -a 'name=idrbt' AppServer

        -b = 
        -K = Ask for a Password
        -m = Module Name
        -a = Arguments
        AppServer = Group Name (Create a Group in /etc/ansible/hosts)

    ***Note:The user creaated on slave server (/etc/passwd)***

### Ansible Commands:
    ansible -b -K -m user -a 'name=idrbt' AppServer
    ansible -m setup all

### Ansible Roles:
    Ansible role is a set of tasks to configure a host to serve a certain purpose like configuring a service.

    Ansible roles allow you to develop reusable automation components by grouping and encapsulating related automation artifacts, like configuration files, templates, tasks, and handlers.

    # How create a `Ansible Role`
    *** Flow***
        Goto https://galaxy.ansible.com/ ( we can find prebuid roles)
    
    # Roles Default path:
        /etc/ansible/roles

        # Incase we need to chnge the path
        /etc/ansible/ansible.cfg  ---> Here we can change the path where we need store

    # Create
    1. ansible-galaxy init <role-name>
        # Sample of Role
            role-name
            |- Readme.md
            |- Templates
            |- tasks --> main.yml (Create Task)
            |- handlers --> main.yml (Add Handlers)
            |- vars
            |- defaults
            |- meta

    2. Add role in Playbook
        # Sample:
            ---
            - host: localhost
              become: true
              vars:
                sample_var: edureka
              roles:
              - role: <role-name>
         
###########################################################################################################################

MODULE 6-7
------------

Containerization using Docker Part-1
====================================

    Monolithic (VM) v/s Microservice Architecture (Continer)
    Diff b/w Virtualiztion and Containerazation

    VM --> It is Hardware level virtualization
    Container --> It is Operting level Virtualization

### Virtualization:
    Infrastructure ==> Operating System ==> Hypervisor ==> VM ==> Applications

### Container
    Containers are completely isolated Environments.As in they can have their own processes

    Infrastructure ==> Operating System ==> Container Engine ==> Container ==> Applications

### Containerazation:
    It is process of packaging your application along with its dependencies/Libraries that the application would require to run.

### Docker: (Docker Engine)
    Docker is tool to enable containerazation 

    Docker File ==> Docker Imgage ==> Docker Container ==> Choose Type OS
    ----------(Build)------------(RUN)-----------------------------------

    Docker utilize `LXC` Continers ==> (Multiple isolated linux systems on control host using a single linux kernel)

### Run the Docker without sudo:
    sudo usermod -aG docker ${USER}
    sudo usermod -aG docker username

### Basic Commands on Docker:

    ## Docker Containers
        docker search                       | search the images in docker hub
        docker pull                         | pull image from docker hub
        docker images                       | list the images in local
        docker run (interactive / detached )| run a container from an image
        docker ps                           | list the running containers
        docker ps -a                        | list running + exited containers
        docker inspect                      | inspect a container
        docker stop|start|restart           | stop/start/restart a container
        docker rm / docker rm -f            | remove the containers from the server
        docker exec                         | get inside a running container
        docker build -t sampleimage/1.0 .   | Build with specific name

    ## Docker Images
        docker images               |list images in local
        docker commit ( manual )    |create image from container changes
        docker build ( automated )  | create image using a dockerfile
        docker history              | view the layers of an image
        docker inspect              | inspect an image
        docker rmi                  | remove image from local

    ## image repository
        docker hub (public)                     | docker image repository
        docker registry container (private)     | docker image repository open source
        DTR (private)                           | docker image repository licensed tool from docker org
        docker login                            | login to image repo from command line
        docker tag                              | create alias name for an image in local
        docker push                             | push images to docker image repository
        Docker Volumes
        docker volume ls                        | list volumes in local
        docker volume create                    | create a volume
        docker inspect volume                   | inspect the volume

### Docker File:

    FROM        |   Define a base Image on which the installation is based   | Ex: FROM ubuntu
    ENV         |   used to set the environment variables that is required   | Ex: ENV HTTP:PORT="9000"
    WORKDIR     |   it tells that the remaining commands will be run in /app | Ex: WORKDIR /path/to/workdir or WORKDIR /app
    ENTRYPOINT  |   its allows you to configure a container that will run as an executable. | ENTRYPOINT [ "sh", "-c", "echo $HOME" ]
    CMD         |   These will be executed after the entry point.            | CMD ["executable","param1","param2"]    
    RUN         |   Define commands that execute to create the docker image  | RUN ["executable","param1","param2"](exec form)
    COPY        |   Copy the files in the docker image                       | COPY <src>... <dest>
    ADD         |   adds  the files of the containers from destination path  | ADD <src>... <dest>
    EXPOSE      |   Expose aa port of the docker container                   | EXPOSE <port> [<port>/<protocol>...]


    ## Example of Docker File
    
    FROM ubuntu
    RUN apt update
    ENV TZ=Asia/Kolkata
    RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ /etc/timezone
    RUN apt install -y apache2
    COPY index.html /var/www/html/
    RUN echo "ServerName localhost" >> /etc/apache2/apache2.conf
    CMD ["apache2ctl","-D","FOREGROUND"]
    EXPOSE 80

### Volumes:

    Docker volumes are directories and files that exist on the host file system outside of the Docker container. These volumes are used to persist data and share data between Docker containers.

    # Commands:
    Create Volume:
        docker volume create <volume name>
    Attached the Volume:
        docker run -itd --name my-ubuntu -v addressbook-data:/addressbook ubuntu

### DOCKER COMPOSE
    Docker Compose is a tool that was developed to help define and share multi-container applications.

    # Sample of Docker-compose up File
        version: '3'
        services:
        db:
            container_name: wp_mysql
            image: mysql:5.7
            volumes:
            - "$PWD/data:/var/lib/mysql"
            environment:
            MYSQL_ROOT_PASSWORD: 123456
            MYSQL_DATABASE: wordpress
            MYSQL_USER: wordpress
            MYSQL_PASSWORD: wordpress
            ports:
            - "3306:3306"
        wp:
            container_name: wp_web
            image: wordpress
            volumes:
            - "$PWD/html:/var/www/html"
            depends_on:
            - db
            ports:
            - "9091:80"
            environment:
            WORDPRESS_DB_HOST: db:3306
            WORDPRESS_DB_USER: wordpress
            WORDPRESS_DB_PASSWORD: wordpress

    ## Start the Application
        docker-compose up

    ## Stop the Application
        docker-compose stop

### Docker Engine:
    Docker engine is an open source containerization technology for building & Containerizing application

    # Docker Engine:
        1. Docker CLI   | Command line Interface
        2. Rest API     | Docker provides an API for interacting the docker daemon
        3. Docker Daemon| Docker daemon lisen for docker API requests & manage docker objects

### Docker Storege:
    When install Docker the docker stored data in this path (default)
        /var/lib/docker 
        | -- aufs: 
        | -- containers: All details about container
        | -- images: All files stored related images
        | -- volumes: Any volume created its stored in volume
            | -- 1. Volume Mount [Create volume & Mount the runnung Container]
            | -- 2. Bind Mount [Create volume on host & Mount the running Container]

### Docker Networks:
    When install docker it creates three networks automatically
        1. Bridge | docker run ubuntu
        2. None   | docker run ubuntu --network=none
        3. Host   | docker run ubuntu --network=host

### Docker Registry:
    The Registry is a stateless, highly scalable server side application that  stores and lets distribute docker images

    image: docker.io/nginx/nginx  [public Repo]
    ------[Registry]-[user]-[Image-Name]

    image: <private-reponame.io>/application-path

### CGROUP:
    CGROUP is Control Group 
    (Limit the Resources per container[cpu,memory])

### Namespce:
    pid: Process Isolation
    net: Network Isolation
    mnt: Volume/file syatem Isolation
    uts: Hostname Isolation
    ipc: Inter process communiction isolation
    usr: For user isolation

## Container Orchestration: (DOCKER SWARM)
    Docker swarm is a container orchestration tool, meaning that it allows the user to manage multiple containers deployed across multiple host machines.

    Internal Distributed state store ===> [Manager] [manager] [manager] ===> [worker] [worker] [worker] [worker] [worker]
    
    ***Note: In Docker swarm we requiired minimum 3 managers*** Because of "RAFT CONSENSUS GROUP" This algorithum based 
    
    # How to Initiate a CLUSTER
        docker swarm init
        
        # For Worker Node
        sudo docker swarm join-token worker
        Token:  docker swarm join --token SWMTKN-1-0v8y2u89vobg9ykldqkkkqzd9aenvh3tbopj6e2oo6l76drwpt-239ar0h1ncx589li99xatit56 192.168.137.201:2377

        # For Master Node
        sudo docker swarm join-token manager
        Token : docker swarm join --token SWMTKN-1-0v8y2u89vobg9ykldqkkkqzd9aenvh3tbopj6e2oo6l76drwpt-b79xt3otiunpyzh86e252nisi 192.168.137.201:2377

        # Create a Service in Docker swarm
            sudo docker service create --name my-service -d -p 8888:8080 tomcat/1.0
        
        # Scale to Application /Replica
            sudo docker service scale my-service=4 
            sudo docker service ps <Application-name>

    ## Docker COMPOSE Commands:
        case 1: deploy multiple containers from a single image
        docker-compose -f docker-compose.yml up --scale web=4 -d ; docker-compose down

        case 2: deploy multiple containers from multiple images
        docker-compose -f docker-compose.yml -p webapps up -d --scale web=2 --scale app=2

        Docker Networking:
        docker network ls # list the default & custom networks on a docker host
        none|host|bridge|overlay|docker_gwbridge
        docker network create -d <driver> <network name> # create a custom network of
        bridge/overlay
        docker run -d --net host --name cont1 alpine    | attach a container to host network
        docker run -d --net none --name cont2 alpine    | attach a container to none network
        docker run -d --net ravinet --name cont3 alpine | attach a container to custom
        bridge/overlay network

    ## Docker Swarm
        docker swarm init ## initialize the swarm mode (swarm manager)
        docker swarm join ## join a node to manager as worker / manager
        docker swarm join-token worker/manager ## generate worker/manager token
        docker swarm leave ## run on worker nodes to leave the node from swarm
        docker node ls ## list the node part of swarm
        docker node inspect ## inspect a node
        docker node rm <nodename> ## run on manager node to remove a node from swarm

### LIMITATIONS:
    


###########################################################################################################################

MODULE 8
--------

Orchestration using Kubernetes Part-1
=====================================
    Kubernetes is a portable, extensible, open-source platform for managing containerized workloads and services, that facilitates both declarative configuration and automation. 