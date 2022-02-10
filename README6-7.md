MODILE 6 & 7
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
    