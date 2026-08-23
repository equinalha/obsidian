---

---
[https://www.linuxshelltips.com/linux-zombie-process/](https://www.linuxshelltips.com/linux-zombie-process/)

Exposure to the Linux operating system ecosystem introduces its users to an in-depth understanding of Linux process management footprints. By definition, a **process** is a program that is continually executing.

A **program** that is not executing does not qualify as a process since it is a passive entity. Its executing state makes it an active entity hence a process. It is also worth mentioning that a single program in execution can be associated with multiple processes.

Now that we have understood what a process is, it’s common courtesy to recognize the two types of processes in existence.

- **Foreground processes** – Another name for this type of process is interactive processes. A system user or programmer is behind the initialization and execution of these processes. The system services are not responsible for their initialization/execution. These processes return output from a user’s input. Once a process is already running, it is impossible to directly initiate a new one from the same terminal instance.
- **Background processes** – Another name for this type of process is non-interactive processes. The system services or users are responsible for their initiation and execution. The system users can also manage them. A unique process identifier (**PID**) is assigned to each of these processes.

### A Zombie Process in Linux

When a **process** is dead or defunct, it is referred to as a **zombie** process. A process table accommodates entries from processes that are still executing.

Once their execution completes, the process table gets rid of their entries. However, it is not the same case with **zombie** processes. Their entries remain valid on the process table even after their execution completes.

### Linux​ Processes States

The various process states that can be found on a Linux process table include:

- **Running(R)** – These are currently running/active processes.
- **Waiting(S/D)** – These processes are waiting on a currently-being-used resource or for an event and this wait can either be uninterruptible sleep (D) or interruptible sleep (S).
- **Stopped(T)** – The active status of these processes has been disabled by an appropriate signal.
- **Zombie(Z)** – These processes still exist on the process table despite finishing their assigned tasks and are associated with the EXIT_ZOMBIE status.

### How Zombie Processes are Created

Once a process completes its assigned task, that process’s parent is notified by the Linux kernel via a **SIGCHLD** signal. A `wait()` system call is executed by the parent process to read the child process’s status before reading its exit code.

This chain of events leads to the cleanup of the child process entry from the process table. However, when the parent process can’t handle or process the **SIGCHLD** signal related to the child process, a zombie process is created.

### How to Identify Zombie Processes in Linux

We can use the Linux **ps command** which outputs a snapshot report of current processes.

```plain text
$ ps aux

```

![[List-Running-Linux-Processes.png]]

List Running Linux Processes

If you find any **Z** entry in the **STAT column**, then you are dealing with a zombie process.

Alternatively, we could pipe the **ps command** through the [awk command](https://www.linuxshelltips.com/find-longest-lines-file-linux/) to filter out any zombie processes **(Z)** on your system.

```plain text
$ ps ux | awk '{if($8=="Z") print}'

```

### How to Clean a Zombie Processes in Linux

Since a **Zombie** process is already dead and can’t be killed, we are left with the alternative of cleaning it up.

We can manually target the parent process of the zombie process with a **SIGCHLD** signal to initiate a `wait()` system call from that parent process. This approach makes it possible to clean up; from the process table, the defunct child process entry.

The first step is to identify the defunct process’s parent id.

```plain text
$ ps -A -ostat,pid,ppid | grep -e '[zZ]'

```

If you have a zombie process on your system, the above command should list the associated STAT column, process id, and parent process id respectfully. The sample output is as follows:

```plain text
Z	208	203

```

From the above sample output, **203** is the parent process id (**ppid**), and to clean up the zombie process, we will execute:

```plain text
$ kill -s SIGCHLD 203

```

The above approach only cleans up the **zombie** process if the parent process successfully handles **SIGCHLD** signals.

In the approach discussed above, we have sampled and identified the parent process id as **203**. To kill the parent process, we will execute the command:

```plain text
$ kill -9 203

```

**[ You might also like: **[**Differences Between PID, TID, and PPID in Linux**](https://www.linuxshelltips.com/differences-between-pid-tid-and-ppid-in-linux/)** ]**

We can now comfortably handle zombie processes in Linux. Hope you enjoyed the article. As always, your comments and feedback are most welcomed.

## RECOMMENDED ARTICLES