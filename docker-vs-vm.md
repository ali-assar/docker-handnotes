## Docker vs VM
Docker and virtual machines (VMs) both provide ways to isolate and run applications, but they have distinct differences in how they achieve this.

Resource Utilization:

Docker: Shares host system's kernel, resulting in lightweight containers with minimal overhead.
VMs: Emulate complete hardware environments, including operating systems, requiring more resources for each VM.
Isolation:

Docker: Provides process-level isolation, sharing the host system's kernel.
VMs: Offer stronger isolation with each VM running its own kernel, providing greater security but requiring more overhead.
Boot Time:

Docker: Containers start and stop almost instantly, allowing for rapid scaling and deployment.
VMs: Often take longer to boot up and shut down due to the need to boot an entire operating system.
Deployment:

Docker: Ideal for microservices architectures and cloud-native applications due to lightweight containers and fast deployment.
VMs: Better suited for running untrusted workloads or legacy applications that require specific operating systems.
Resource Management:

Docker: Offers better resource utilization and scalability, allowing for efficient use of system resources.
VMs: Require dedicated resources for each VM, potentially leading to underutilization of hardware resources.
Development Workflow:

Docker: Provides a consistent environment across different development, testing, and production environments, facilitating a smoother development workflow.
VMs: Require more overhead in managing different virtual environments, leading to potentially more complex development workflows.

<div style="text-align:center">
    <img src="./images/cc01-what-is-docker-figure1.webp" alt="docker vs vm">
</div>
