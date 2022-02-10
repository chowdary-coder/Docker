MODILE 5
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
        

    
