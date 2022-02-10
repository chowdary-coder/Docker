1. Overview the Devops (Introduction)
    1. Blog-Devops Tutorial: Introduction to Devops

2. Version Control with Git
    1. Get Basic Commnds
    2. Install Git on Windows and Centos
    3. How to create Branching, Merging, Rebashinng
    4. Git Merge and Rebase
    5. Git commands with examples

3. Git, Jenkins & Maven
    1. Assignment -1
    2. Assignment -2
    3. Branching and Merging in Git
    4. Merge Conflicts
    5. Build a Maven Project
    6. Install Jenkins 
    7. CI with Jenkins

4. Continuos Integration using Jenkins
    1. Assignment
    2. Build project Pipeline
    3. Add a slave Node
    4. Pipeline Project through Pipeline Script
    5. Jenkins Pipeline Tutorial
    6. Docker Jenkins Pipeline 
    7. Pipeline Script
    8. Install Jenkins and Tomcat Configuration

5. Configuration Managment Using Ansible
    1. Ansible Commands
    2. Ansible Playbook
    3. Variables and Handlers
    4. Ansible Roles
    5. Configuration Management and automtion Wiith Ansible
    6. Write Ansible Playbooks
    7. Install Ansible in Two easy steps
    8. ansible Provisioning

6. Containerization using Docker Part-1
    1. Docker  CLI Commands
    2. Port Binding
    3. Detached and Foreground mode
    4. Docker File
    5. Introduction to Docker and Containerization
    6. Docker Container
    7. Docker Guide
    8. Docker installation (Ubuntu & CentOS)
    9. Docker installation (windows) Setting
    10. Docker Tutorial
    11. Docker Container
    12. Docker commands with Exaample

7. Containerization using Docker Part-2
    1. Demo 1,2,3,4
    2. Docker Session Slides/Images
    3. Docker Session Installation and Demos

8. Orchestration using Kubernetes Part-1
    1. Demo 1,2,3,4,5

9. Orchestration using Kubernetes Part-2
    1. Demo 1,2,3,4,5

10. Monitoring using Prometheus and Grafana
    1. Demo 1,2

11. Provisioning Terraform Part -1
    1. Demo 1,2,3,4,5

12. Provisioning Terraform Part -2
    1. Demo 1,2

13. Selinium (Self-Paced)
    1. Demo 1,2

14. Nagios (Self-Paced)
    1. Demo 1,2

15. Devops on Cloud (Self-Paced)
    1. Devops on Cloud

16. AWS (Self-Paced)
    1. IAM(1), EC2(1), EC2(2), IAM(2), IAM Demo 1,2,3,4,EC2 Demo 1,2,3,4,5,6,7
    2. Instance Connection 

# README FOR LIST CONTENT

    README1  --->  Overview the Devops (Introduction)
    README2  --->  Version Control with GIT
    README3  --->  GIT, Jenkins & Maven Integration
    README4  --->  Continuos Integration using Jenkins
    README5  --->  Configuration Managment using ANSIBLE
    README6  --->  Containerization using Docker Part-1
    README7  --->  Containerization using Docker Part-2
    README8  --->  Orchestration using Kubernetes Part-1
    README9  --->  Orchestration using Kubernetes Part-2
    README10 --->  Monitoring using Prometheus and Grafana
    README11 --->  Provisioning Terraform Part -1
    README12 --->  Provisioning Terraform Part -2
    README13 --->  Selinium (Self-Paced)
    README14 --->  Nagios (Self-Paced)
    README15 --->  Devops on Cloud (Self-Paced)
    README16 --->  AWS (Self-Paced)


# VIDEOS

    MODULE1    ---> Video: 1, Video: 2[End: 01:31:00]
    MODULE2    ---> Video: 2[Start: 01:31:00],Video: 3[End: 01:40:00]
    MODULE3    ---> Video: 3[Start: 01:40:00],Video: 4, Video: 5 [End: 00:51:00]
    MODULE4    ---> Video:5 [Start: 00:51:00], Video: 6, Video: 7
    MODULE5    ---> Video: 8,Video: 9[Start: 01:60:00]
    MODULE6-7  ---> Video: 9[End: 01:60:00], Video: 10 , Video: 11, Video: 12[End: 01:30:00]
    MODULE8    ---> Video: 12[Start: 01:30:00],Video: 13      


### INstall Java8 in Ubuntu
    sudo apt update
    sudo apt install openjdk-8-jdk openjdk-8-jre

### Install Tomcat in ubuntu
    sudo apt install tomcat9
    sudo apt install tomcat9-admin

    # Configure the Tomcat9:
        cd /var/lib/tomcat9/conf
        sudo nano server.xml (Change the Port 8080 to 8081)
        ------------
         <Connector port="8081" protocol="HTTP/1.1"
               connectionTimeout="20000"
               redirectPort="8443" />
        -----------------
        sudo nano tomcat-user.xml
        ------------------
        # Add Below Lines:

            <role rolename="manager-script"/>
            <role rolename="manager-jmx"/>
            <role rolename="manager-gui"/>
            <role rolename="manager-status"/>

            <user username="admin" password="admin" roles="manager-script","manager-jmx","manager-gui","manager-status"/>
        -------------------
        systemctl restart tomcat9.service 