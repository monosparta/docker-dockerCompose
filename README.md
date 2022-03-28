# Concepts

## Container

### What is the container

Containers are a form of operating system virtualization. A single container might be used to run anything from a small microservice or software process to a larger application. Inside a container are all the necessary executables, binary code, libraries, and configuration files. Compared to server or machine virtualization approaches, however, containers do not contain operating system images. This makes them more lightweight and portable, with significantly less overhead. In larger application deployments, multiple containers may be deployed as one or more container clusters. Such clusters might be managed by a container orchestrator such as Kubernetes.


A container is a package of software that includes all dependencies: code, runtime, configuration, and system libraries so that it can run on any host system. At runtime, the container is also granted its own isolated slice of operating system resources like CPU, RAM, Disk, and Networking.

Benefits of containers
Containers are a streamlined way to build, test, deploy, and redeploy applications on multiple environments from a developer’s local laptop to an on-premises data center and even the cloud. Benefits of containers include:

1. Less overhead
   Containers require less system resources than traditional or hardware virtual machine environments because they don’t include operating system images.
2. Increased portability
   Applications running in containers can be deployed easily to multiple different operating systems and hardware platforms.
3. More consistent operation
   DevOps teams know applications in containers will run the same, regardless of where they are deployed.
4. Greater efficiency
   Containers allow applications to be more rapidly deployed, patched, or scaled.
5. Better application development
   Containers support agile and DevOps efforts to accelerate development, test, and production cycles.

### Different from VM


## Docker

### Introduction
Build, Ship and Run Any App, Anywhere

### Why to use Docker

## Docker Compose


## Reference

1. [AWS Docker](https://aws.amazon.com/tw/docker/)
2. [Docker Engine](https://docs.docker.com/engine/)
3. [ATLASSIAN CI/CD-Containers](https://www.atlassian.com/continuous-delivery/microservices/containers)