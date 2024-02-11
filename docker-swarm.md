## Docker Swarm

Docker Swarm is Docker's native orchestration tool used for managing a cluster of Docker hosts and deploying and scaling containerized applications across them. It provides features for automatic load balancing, service discovery, rolling updates, and fault tolerance, making it easy to deploy and manage distributed applications at scale.

![docker swarm](./images/docker-swarm-v2.png)


### Key Components of Docker Swarm

#### 1. Manager Nodes

Manager nodes are responsible for managing the swarm cluster. They handle tasks such as scheduling services, maintaining the cluster state, and orchestrating communication between nodes. A swarm cluster typically has multiple manager nodes for high availability and fault tolerance.

#### 2. Worker Nodes

Worker nodes are responsible for running containers and executing the tasks assigned by the manager nodes. They do not participate in managing the swarm cluster but only execute the containers deployed by the manager nodes.

![docker swarm](./images/Docker-Swarm-Networking-2.webp)
#### 3. Services

Services are the primary building blocks of applications in Docker Swarm. A service defines how a containerized application should be deployed and managed within the swarm cluster. Services can be scaled up or down, updated, and monitored easily using Docker Swarm commands.

#### 4. Tasks

Tasks represent the individual units of work that Docker Swarm schedules on worker nodes. Each service is composed of one or more tasks, with each task corresponding to a running container instance.

#### 5. Overlay Networks

Overlay networks provide connectivity between containers running on different nodes in the swarm cluster. They enable communication between services and allow containers to discover and communicate with each other seamlessly.

### Example: Deploying a Docker Swarm Service

Here's an example of deploying a simple web service using Docker Swarm:

1. Initialize Docker Swarm on a manager node:

   ```bash
   docker swarm init --advertise-addr <manager-node-ip>
   ```

2. Deploy a web service using Docker Swarm:

   ```bash
   docker service create --name my_web_service --replicas 3 -p 8080:80 my_web_image
   ```

   This command creates a service named `my_web_service` with three replicas, exposing port 8080 on the host to port 80 in the containers. Replace `my_web_image` with the name of your Docker image.

3. Scale the service:

   ```bash
   docker service scale my_web_service=5
   ```

   This command scales the `my_web_service` service to have five replicas, distributing the workload across multiple containers in the swarm cluster.

4. Update the service:

   ```bash
   docker service update --image new_web_image my_web_service
   ```

   This command updates the `my_web_service` service to use a new Docker image named `new_web_image`, rolling out the update to all replicas without downtime.
