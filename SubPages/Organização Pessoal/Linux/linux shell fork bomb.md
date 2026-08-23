---

---
[https://www.cyberciti.biz/faq/understanding-bash-fork-bomb/?s=09](https://www.cyberciti.biz/faq/understanding-bash-fork-bomb/?s=09)

![[terminal.png]]

Can you explain the following bash code or bash fork() bomb code?
 :(){ :|:& };:

The fork bomb is a form of denial-of-service (DoS) attack against a Linux or Unix-based system. It makes use of the fork operation. The :(){ :|:& };: is nothing but a [bash function](https://www.cyberciti.biz/faq/bash-shell-script-function-examples/). This function get executed recursively. It is often used by sysadmin to test user process limitations on server. Linux process limits can be configured via /etc/security/limits.conf and PAM to avoid bash fork() bomb. Once a successful fork bomb has been activated in a system it may not be possible to resume normal operation without rebooting the system as the only solution to a fork bomb is to destroy all instances of it.

| Tutorial details |
| --- |
| Difficulty level |
| Root privileges |
| Requirements |
| Category |
| Prerequisites |
| OS compatibility |
| Est. reading time |

## Understanding :(){ :|:& };: fork() bomb code

**WARNING!** These examples may crash your computer if executed.

The :() – Defined the function called :. This function accepts no arguments. The syntax for bash function is as follows:

fork() bomb is defined as follows:

```plain text
:(){
 :|:&
};:
```

**:|:** – Next it will call itself using programming technique called recursion and pipes the output to another call of the function ‘:’. The worst part is function get called two times to bomb your system.

**&** – Puts the function call in the background so child cannot die at all and start eating system resources.

**;** – Terminate the function definition.

**:** – Call (run) the function aka set the fork() bomb.
 Here is more human readable code:

```plain text
bomb() {
 bomb | bomb &
}; bomb
```

Properly configured Linux / UNIX box should not go down when fork() bomb sets off. See the [comment # 5 below](https://www.cyberciti.biz/faq/understanding-bash-fork-bomb/?s=09#comment-37097) for more fork bomb examples created in Perl, Windows XP (batch) and C.

## Preventing fork bomb on Linux

Please note that ulimit is a shell builtin. You can verify this using the [type command](https://bash.cyberciti.biz/guide/Type_command?utm_source=Linux_Unix_Command&utm_medium=faq&utm_campaign=nixcmd) or [command command](https://bash.cyberciti.biz/guide/Command?utm_source=Linux_Unix_Command&utm_medium=faq&utm_campaign=nixcmd) as follows:`$ type -a ulimit``

ulimit is a shell builtin`

Type the following ulimit command to find out the current maximum processes you can run on Linux:

OR

The number 128038 indicates that you can run 128038 processes. To protect your Linux system from a fork bomb, you need to lower that number. To limit your session to 5000 processes, use the following command`$ ulimit -S -u 5000`

**WARNING!** Please don’t set ulimit numbers too low. This will prevent you from working on your system.

Now run fork bomb again:

And you will see messages as follows:

```plain text
bash: fork: Resource temporarily unavailable
bash: fork: Resource temporarily unavailable
bash: fork: Resource temporarily unavailable
bash: fork: Resource temporarily unavailable
bash: fork: Resource temporarily unavailable
bash: fork: Resource temporarily unavailable
bash: fork: Resource temporarily unavailable
```

You just avoided fork bomb on Linux. Run the following pgrep command to see the current threads limit:`$ pgrep -wcu $USER`
 Sample outputs:

```plain text
5002
```

## Summing up

You learned about a kind of denial-of-service (DoS) attack upon a Linux or Unix-based machine. Make sure you do read the following man pages using the [man command](https://bash.cyberciti.biz/guide/Man_command?utm_source=Linux_Unix_Command&utm_medium=faq&utm_campaign=nixcmd) or [help command](https://bash.cyberciti.biz/guide/Help_command?utm_source=Linux_Unix_Command&utm_medium=faq&utm_campaign=nixcmd):`$ man bash``

$ ulimit --help``

$ help ulimit``

$ man ulimit`