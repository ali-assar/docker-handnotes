## Understanding Docker Networking

Docker networking allows containers to communicate with each other and with other network resources efficiently. Docker provides various networking options to suit different use cases, from single-host networking to complex multi-host setups. Understanding Docker networking is crucial for deploying and managing containerized applications effectively.

### Docker Network Models

#### 1. Bridge Network

By default, Docker creates a bridge network named `bridge` on the host. Containers connected to this network can communicate with each other directly. Each container on the bridge network gets its own unique IP address. This network model is suitable for standalone containers running on a single Docker host.

#### 2. Host Network

Containers using the host network mode share the network namespace with the Docker host. This means they bypass Docker's network isolation and behave as if they were running directly on the host. The host network mode offers better performance but sacrifices network isolation.

#### 3. Overlay Network

Overlay networks enable communication between containers running on different Docker hosts. Docker Swarm mode uses overlay networks to provide multi-host networking for containerized applications. Overlay networks use VXLAN encapsulation to extend the Docker network across multiple hosts while maintaining isolation between containers.

#### 4. MACVLAN Network

MACVLAN networks allow containers to have their own MAC addresses and appear as separate physical devices on the network. This network mode is useful for scenarios where containers require direct access to the physical network, such as when implementing network policies or integrating with legacy systems.

### Docker Network Commands

#### 1. List Networks

To view a list of Docker networks on the host:

```
docker network ls
```

#### 2. Inspect Network

To inspect details of a specific Docker network, including its configuration and connected containers:

```
docker network inspect <network name>
```

#### 3. Create Network

To create a custom Docker network:

```
docker network create <network name>
```

#### 4. Connect Container to Network

To attach a container to a specific Docker network:

```
docker network connect <network name> <container name or id>
```

#### 5. Disconnect Container from Network

To detach a container from a Docker network:

```
docker network disconnect <network name> <container name or id>
```

#### To summarize above lets explain with an example:
Run PostgreSQL Container
Run a PostgreSQL container, specifying options such as network, container name, environment variables, and port mapping:

```
docker run --name my_postgres \
  --network my_network \
  --net-alias postgres \
  -e POSTGRES_PASSWORD=my_password \
  -p 5432:5432 \
  -d postgres:latest
```
Explanation of options used:

--name my_postgres: Specifies the name of the container as my_postgres.
--network my_network: Attaches the container to the my_network Docker network.
--net-alias postgres: Gives an alias postgres to the container within the network.
-e POSTGRES_PASSWORD=my_password: Sets the PostgreSQL database password to my_password.
-p 5432:5432: Publishes container's port 5432 (PostgreSQL default port) to the host machine.
-d: Runs the container in detached mode (in the background).

