---

---
[https://blog.aigents.co/understanding-docker-architecture-486b4b5bd296](https://blog.aigents.co/understanding-docker-architecture-486b4b5bd296)

## Docker Tutorial-1

![[1bESTMspLODDtndESmHOxvw.png]]

Docker Client-Server-Architecture

When developers build the software application, they install it on dev servers to test it. Then it is handed over test team, it is again installed on a test environment, and the test team tests the application. Finally, once everything is go green it is installed and deployed to the production environment.

In this process, the same application was getting configured and set up in different environments which is time-consuming and tedious. That is where Docker comes into the picture.

With the help of Docker, we can create a software package of our application called an `**image**` and this image can be deployed just with a single command on different environments as long as the environment also has Docker installed on it. This saves a lot of time deploying the Application in different environments.

# Image and Container:

If you know the *program* and *process* then it becomes very easy for you to understand docker. We can say an `image` is similar to a program, basically, a set of program files packed together having its own file system and a `container` is nothing but an isolated process running on a host machine that is built out of the image.

# Docker Desktop:

Docker Desktop is an easy-to-install application for your Mac or Windows environment that enables you to build and share containerized applications and microservices. Docker Desktop includes the Docker daemon (`dockerd`), the Docker client (`docker`), Docker Compose, Docker Content Trust, Kubernetes, and Credential Helper.

When you run the docker info command, the output looks as below:

```plain text
vikram@121212 ~ % docker infoClient:
 Context:    default
 Debug Mode: false
 Plugins:
    buildx:     Build with BuildKit (Docker Inc., v0.5.1-docker)
    compose:    Docker Compose (Docker Inc., v2.0.0-beta.6)
    scan:       Docker Scan (Docker Inc., v0.8.0)Server:
Containers: 87
    Running: 26
    Paused: 0
    Stopped: 61 Server Version: 20.10.7
 Storage Driver: overlay2
 Backing Filesystem: extfs
 Supports d_type: true
 Native Overlay Diff: true
 userxattr: false
 Logging Driver: json-file
 Cgroup Driver: cgroupfs
 Cgroup Version: 1
....
```

- **Docker uses a client-server architecture.**
- The Docker *client* talks to the Docker ***daemon***, which does the heavy lifting of building, running, and distributing your Docker containers.
- The Docker client and daemon can run on the same system, or you can connect a Docker client to a remote Docker daemon.
- The Docker client and daemon communicate using a **REST API**, over UNIX sockets or a network interface.
- Another Docker client is Docker Compose, which lets you work with applications consisting of a set of containers.

![[1pJGJHufMf845zvQXU27dRQ.png]]

Docker client-server architecture.

# Docker Architecture — Workflow with Examples:

Docker Client-Server-Architecture

**Let’s understand Some Docker terminologies :**

## 1. The Docker Daemon:

The Docker daemon (`**dockerd**`) listens for Docker API requests (docker build, docker run, docker push, docker pull, etc) and manages Docker objects such as `images`, `containers`, `networks`, and `volumes`. A daemon can also communicate with other daemons to manage Docker services.

## 2. The Docker Client:

The Docker client (`**docker**`) is the primary way that many Docker users interact with Docker. When you use commands such as *docker**run*, the client sends these commands to the ***dockerd***, which carries them out.

Internally the docker command uses the Docker REST APIs. The Docker client can communicate with more than one daemon.

## 3. Docker Registries:

A Docker *registry* stores Docker images. Docker Hub is a public registry that anyone can use, and Docker is configured to look for images on Docker Hub by default. You can even run your own private registry.

When you use the `docker pull` or `docker run` commands, the required images are pulled from your configured registry. When you use the `docker push` command, your image is pushed to your configured registry.

## 4. Docker Objects:

When you use Docker, you are creating and using `images`, `containers`, `networks`, `volumes`, `plugins`, and other objects.

*I mostly write on multiple topics — Java Programming, Data structure, and Algos, SQL, GIT, LINUX, Docker, Software development, and my experiences.*

That’s all for this article. Thank you for reading it.