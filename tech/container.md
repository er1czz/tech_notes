# Container
- A collection of software processes unified by one namespace, 
- with access to an operating system kernel that it shares with other containers and little to no access between containers

## Docker Instance
- A runtime instance of Docker image contains
  1. A Docker image
  2. An execution environment
  3. A standard set of instructions

### Docker Engine
- Comprised of the runtime and packaging tool
- **Must** be installed on the host

### Docker Store (Docker Hub)
- An online cloud service where users can store and share their Docker images

# Container is NOT Virtual Machine (VM)
- VM: one or many applications, necessary binaries and libraries, entire guest operating system
- Container: applications and dependencies, shared the kernel with other containers, NOT tied to infrastructure (only need Docker Engine)
  - Run as isolated processes in user space on the host OS

### Container orchestrator (manager)
#### Kubernetes (K8s): an open-source platform designed to automate deploying, scaling, and operating application containers
- to foster an ecosystem of components and tools that relieve the burden of running applications in public and private clouds
- Kubernetes, easy to migrate containers to cloud environment

### When to go serverless
- Starting to build infra from scratch
- Running infra in the cloud
