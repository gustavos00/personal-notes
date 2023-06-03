# Docker

## Glossary

**Host** - It is a computer, whether it's your home computer or a machine on AWS.  
**Kernel** - Creates a bridge between hardware and software (manages CPU, RAM, ...).  
**Binaries** - TBD
**Docker Tag** - It means the version of the image.

---

## What problem does Docker solve?

Let's assume we have a project that relies on NodeJS, Postgres, Redis, etc. as dependencies. Since they are all running on the same host, they share the same binaries and libraries.

This can make your application easily breakable. How? 
- Suppose you decide to upgrade Postgres to fix an issue. You do it, and suddenly everything breaks. Why? **Because they use the same binaries and libraries.**

---

## How can I prevent this issue from occurring?

You can prevent this by ensuring that the tools don't share binaries and libraries among themselves. But **how**?

- **VMs (Virtual Machines)**  
  By using VMs, you can enforce that each tool has its own specific OS.   

    - **Pros:** 
      - Isolation: Each tool can have its own OS in a separate VM.
      - Security: By isolating the OS, if one VM is compromised, the others remain unaffected.

    - **Cons:**
      - Resource Overhead: Each VM requires its kernel, which can consume significant resources.
      - Slower Startup: Starting a VM takes longer compared to starting a container. 

- **Linux Containers (Docker)**  
  Linux containers are a isolated and independent environments but they keep sharing the host system's kernel.  
  In pratical terms, means that each tool will have they specific binaries and libs but they will share the host system's kernel.  
  
  Docker is an example of a container engine, which is responsible for managing containers. 

    - **Pros:** 
      - Lightweight: Containers share the same kernel as the host, making them more lightweight compared to VMs. However, each tool still has its specific binaries and libraries.
      - Portability: Containers can run consistently across different environments.

    - **Cons:**
      - Weaker Isolation: Containers share the host system's kernel, which may result in weaker isolation. However, containerization technologies like Docker implement isolation mechanisms to mitigate this.
      - "Limited Operating System" Support: Containers primarily support Linux-based systems. While they can be used on macOS and Windows, there may be some issues or additional work required.

## What are Docker images?
Docker images is what say to docker what gonna be run inside the Linux Container. 
 
You can create custom images with the configuration of the environment, etc... but you can download images from the [docker hub](https://hub.docker.com/).  

---

## Basic commands on PostgreSQL

### Databases
  - #### List all
  
  ```mysql
  \l
  ```
  
  - #### Connect to a specific database
  
  ```mysql
 \c database_name
  ```
  
### Tables
 TBD...
