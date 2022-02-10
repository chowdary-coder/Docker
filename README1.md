MODILE 1
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

