## Getting Started with Docker
Docker is a powerful tool for containerization, allowing you to package applications and their dependencies into lightweight containers that can run anywhere.
### 1.  Pulling Images
To get started with Docker, you often need to pull Docker images from a registry like Docker Hub
```
docker pull <image name>
```
Example:
```
docker pull ubuntu
```
### 2. Starting a Container
Once you have pulled an image, you can start a container from it:
```
docker container run <image name>
```
Example:
```
docker container run ubuntu
```
### 3. Useful Commands When Starting a Container
Here are some useful commands to enhance your container management:

```
docker container run --detach or -d     # To run a container detached
docker container run --name             # To give a name to a container
docker container run --publish or -p    # To expose a port to the local host
docker container run --env or -e        # To pass an environment variable to the container
docker container run --rm               # To remove the container after running it
```
Example: 
```
docker container run -d --name my_container -p 8080:80 -e MYSQL_ROOT_PASSWORD=password mysql
```

### 4. Viewing Logs
You can view the logs of a container using:
```
docker container logs <container name or id>
```
Example:
```
docker container logs my_container
```

### 5. Managing Containers
To start, stop, or remove a container, you can use the following commands:

```
docker container start <container name or id>
docker container stop  <container name or id>
docker container rm  <container name or id>
```
Example:
```
docker container start my_container
docker container stop my_container
docker container rm my_container
```
### 6. Inspecting Containers
To inspect what's going on inside a container, you can use these commands:

```
docker container inspect     # Details of one container's configuration
docker container top         # To see processes inside a container
docker container stats       # Performance stats for all containers
```
Example:
```
docker container inspect my_container
docker container top my_container
docker container stats
```
### 7. Accessing Container's Shell
You can access a container's shell using:
```
docker container run -it <image name> /bin/bash
docker container exec -it <container name or id> /bin/bash
```
Example:
```
docker container run -it ubuntu /bin/bash
docker container exec -it my_container /bin/bash
```
### 8. Docker Network
Docker also provides networking capabilities for connecting containers. Here are some useful networking commands:
```
docker network ls            # To see a list of existing networks
docker network inspect       # To inspect a network
docker network create        # To create a network
docker network connect       # To attach a network to a container
docker network disconnect    # To detach a network from a container
--net-alias                  # To give an alias to a network
```
Example:

```
docker network ls
docker network inspect my_network
docker network create my_network
docker network connect my_network my_container
docker network disconnect my_network my_container
```