---
layout: post
title:  Chapter 4 - Containerization
category: Web-Architecture
description: Chapter 4
---

# Containerization

### What is Containerization

-  *Containerization* is a lightweight alternative to a virtual machine that involves encapsulating an application in a container with its own operating system. 
-  A container takes its meaning from the logistics term, *packaging container*. When we refer to an application container, we mean packaging software.



### Why Cotainers 

-  Reduced Delivery Time
-  Increase Productivity
-  Cloud Compatibility
-  Environment-agnostic deliverables



### Containers 

-  flexible 
-  Lightweight（GB vs MB）
-  Interchangeable
-  Portable
-  Scalable
-  Stackable



### VM and Containers Difference 

| Virtual Machine                                              | Containers                                                   |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| ![Virtual machine stack example](https://docs.docker.com/images/VM%402x.png) | ![Container stack example](https://docs.docker.com/images/Container%402x.png) |
| Each VM includes the application, the necessary binaries and libraries and an entire guest operating system, all of which may be tens of GBs in size | Containers include the application and all of its dependencies, but share the kernel with other containers.<br> They run as an isolated process in userspace on the host operating. <br>They  are also not tied to any specific infrastructure—Docker Containers run on any computer , on any infrastrusture and in any cloud |



## Docker 

### What is Docker 

-  The leading containerization technology
-  Written in Go
-  Avaliable in both community and enterprise editions
-  runs natively on Linux, MacOs and Windows
-  Consiss of multiple Parts

### Docker Engine 

-  Consists of three parts
   -  Server which runs the Docker daemon
   -  REST API for communication between client and daemon
   -  CLI client(docker)



### Terminology for Docker 

| Term       | Explanation                                                  |
| ---------- | ------------------------------------------------------------ |
| Image      | Executable package containing the code, runtime, libraries, environment and configuration<br>Read Only<br>Can be Stored and transferred |
| Container  | A runtime instance of an image<br>An isolated workspace on the host machine |
| DockerFile | A file containting instructions how to create an image       |

### Docker Compose 

-  Multi- container application made easy 
-  Good for development environments and single host deployment
-  configured with a YAML file 



### Containerization for web application

#### The advantage 

-  Image as deliverable 
-  Good cloud support
   -  AWS, Azure, Digital Ocean, OpenStack, Google Compute Engine
-  On container for each process



#### The disadvantage

-  Yet antoher layer
-  A new tool to grasp
-  Monitoring can be hard
-  Managing Clustered Systems require additonal tools



