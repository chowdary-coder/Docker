MODILE 8
--------

Orchestration using Kubernetes Part-1
=====================================
    Kubernetes is a portable, extensible, open-source platform for managing containerized workloads and services, that facilitates both declarative configuration and automation. 
    Kubernetes also known as K8

### WHY:
    1. High Availability
    2. Sclability or High Performance
    3. Disaster Recovery - Backup and Restore

## KUBERNETES:
    Kubernetes has the following main components:
        1. Master Nodes
            a. Controller   | Responsible for the control resources and loads
            b. Api-Server   | Collection all the API
            c. Scheduller   | Check the Availability & Schedule the load to worker nodes/pods
            d. etcd         | Key-Value store

        2. Worker Nodes
            a. Kubelet      | (Agent) Responsible for mking that the container running on the nodes as expected 
            b. Kubeproxy    | Enables config the network cluster (Managed by the proxy for External user)

    ***Note: All the Node will be shifted to  Worker nodes***

### Install EKS in AWS:
    # Crete a EKS Flow:
        Goto Services --> EKS --> Create Cluster --> configure Cluster --> Specify Networking --> Review & Create

    # Add a Node Flow:
        Goto --> Add a Node -->  Configure Node Group --> Set compute  configuration --> Set scalling Configuration --> Create
    # How to Create a EKS:
    Steps: 1
        s


