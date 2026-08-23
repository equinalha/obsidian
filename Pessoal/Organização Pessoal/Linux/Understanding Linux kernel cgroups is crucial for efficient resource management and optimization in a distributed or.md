---

---
> [!note] 📌
> **Krishnamohan Yerrabilli ☸️ **[***@K_Mohan_:***](https://www.twitter.com/K_Mohan_)
Understanding Linux kernel cgroups is crucial for efficient resource management and optimization in a distributed or cloud-based infrastructure.

It is key to building and maintaining high-performance and scalable systems.

Let's dive into the topic 🧵👇
> [https://pbs.twimg.com/media/FrbadS8XgAAtfvr.jpg](https://pbs.twimg.com/media/FrbadS8XgAAtfvr.jpg)

> [!note] 📌
> **Krishnamohan Yerrabilli ☸️ **[***@K_Mohan_:***](https://www.twitter.com/K_Mohan_)
/ Intro 

To begin with, we need a reminder that namespaces determine what a process can see.

Control Groups, also known as cgroups, determine what a process can use. 

Cgroups purpose is to manage resources for a group of processes. Let's see how they do it.

> [!note] 📌
> **Krishnamohan Yerrabilli ☸️ **[***@K_Mohan_:***](https://www.twitter.com/K_Mohan_)
/ Cgroup File System Interface

Cgroups are organized in a hierarchical structure that looks like a tree of process groups. 

We can view and manage this structure using the Cgroups file system interface, which is built into the Linux kernel.
> [https://pbs.twimg.com/media/Frbg-9QaIAIX5P-.jpg](https://pbs.twimg.com/media/Frbg-9QaIAIX5P-.jpg)

> [!note] 📌
> **Krishnamohan Yerrabilli ☸️ **[***@K_Mohan_:***](https://www.twitter.com/K_Mohan_)
/ Resource Control

Cgroups provide a way to manage system resources by allocating them to specific groups of processes. 

Resource control in Cgroups is achieved by setting limits on various system resources, such as CPU, memory, and I/O bandwidth.
> [https://pbs.twimg.com/media/FrbhY5IaYAEektf.jpg](https://pbs.twimg.com/media/FrbhY5IaYAEektf.jpg)

> [!note] 📌
> **Krishnamohan Yerrabilli ☸️ **[***@K_Mohan_:***](https://www.twitter.com/K_Mohan_)
/ Grouping of Processes

Cgroups provide a way to group processes together and manage them as a unit. 

By creating control groups and assigning processes to them, we can manage the resource usage and behavior of those processes.
> [https://pbs.twimg.com/media/Frbh_22aUAEk6FS.jpg](https://pbs.twimg.com/media/Frbh_22aUAEk6FS.jpg)

> [!note] 📌
> **Krishnamohan Yerrabilli ☸️ **[***@K_Mohan_:***](https://www.twitter.com/K_Mohan_)
/ Process Tracking

Devs can track and monitor the behavior of individual processes and groups of processes. 

We can assign processes to specific control groups, to monitor their resource usage and set limits on their behavior.
> [https://pbs.twimg.com/media/FrbnTD9aIAAZbJz.jpg](https://pbs.twimg.com/media/FrbnTD9aIAAZbJz.jpg)

> [!note] 📌
> **Krishnamohan Yerrabilli ☸️ **[***@K_Mohan_:***](https://www.twitter.com/K_Mohan_)
/ Memory Management

It provides a way to manage memory usage by allocating it to specific groups of processes

It is achieved by setting memory limits and swapping policies for each control group.
> [https://pbs.twimg.com/media/Frbn9p3aIAMD5Gz.jpg](https://pbs.twimg.com/media/Frbn9p3aIAMD5Gz.jpg)

> [!note] 📌
> **Krishnamohan Yerrabilli ☸️ **[***@K_Mohan_:***](https://www.twitter.com/K_Mohan_)
/ CPU Management 

Cgroups provide a way to manage CPU usage by allocating it to specific groups of processes

We can achieve this by setting CPU limits and priorities for each control group.
> [https://pbs.twimg.com/media/FrboSi3aUAE1CSe.jpg](https://pbs.twimg.com/media/FrboSi3aUAE1CSe.jpg)

> [!note] 📌
> **Krishnamohan Yerrabilli ☸️ **[***@K_Mohan_:***](https://www.twitter.com/K_Mohan_)
/ I/O Management

Cgroups provide a way to manage I/O bandwidth by allocating it to specific groups of processes.

The I/O management settings can be applied at different levels of the Cgroups hierarchy, allowing for great control over I/O bandwidth.
> [https://pbs.twimg.com/media/FrbozxJaMAIKmLK.jpg](https://pbs.twimg.com/media/FrbozxJaMAIKmLK.jpg)

> [!note] 📌
> **Krishnamohan Yerrabilli ☸️ **[***@K_Mohan_:***](https://www.twitter.com/K_Mohan_)
/ Monitoring

Cgroups provide a way to monitor the resource usage of individual processes and groups of processes

Tools like Prometheus and Grafana rely on the data provided by the Linux kernel's Cgroups subsystem to monitor resource usage and track system performance.
> [https://pbs.twimg.com/media/FrbpTqoacAMlNcF.jpg](https://pbs.twimg.com/media/FrbpTqoacAMlNcF.jpg)

> [!note] 📌
> **Krishnamohan Yerrabilli ☸️ **[***@K_Mohan_:***](https://www.twitter.com/K_Mohan_)
/ Integration with Other Sub-Systems

We can be integrated with other subsystems in the Linux kernel to provide more advanced resource management capabilities

It can be used in conjunction with other management tools like Docker to provide containerization capabilities.
> [https://pbs.twimg.com/media/FrbqctsaEAA9B4z.jpg](https://pbs.twimg.com/media/FrbqctsaEAA9B4z.jpg)

> [!note] 📌
> **Krishnamohan Yerrabilli ☸️ **[***@K_Mohan_:***](https://www.twitter.com/K_Mohan_)
My mission is to guide people who want to get into DevOps, from basics to advanced!!

If you had a good time reading this please retweet the first tweet to help others as well.

See you with another one soon, Have a Wonderful day!!

[**twitter.com/K_Mohan_/statu…**](https://twitter.com/K_Mohan_/status/1636933181659021312?s=20)
> > [!note] 📌
> > **Krishnamohan Yerrabilli ☸️ **[***@K_Mohan_:***](https://www.twitter.com/K_Mohan_)
> Understanding Linux kernel cgroups is crucial for efficient resource management and optimization in a distributed or cloud-based infrastructure.
> 
> It is key to building and maintaining high-performance and scalable systems.
> 
> Let's dive into the topic 🧵👇
> > [https://pbs.twimg.com/media/FrbadS8XgAAtfvr.jpg](https://pbs.twimg.com/media/FrbadS8XgAAtfvr.jpg)