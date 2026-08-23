---

---
> [!note] 📌
> **Linuxopsys **[***@linuxopsys:***](https://www.twitter.com/linuxopsys)
In addition to UGO/RWX permissions and ACLs (Access Control Lists), Linux uses file and directory attributes to control the level of access that system programs and users have to files.

Let’s dive in!
> [https://pbs.twimg.com/media/FwRjsNxX0CAtnEk.jpg](https://pbs.twimg.com/media/FwRjsNxX0CAtnEk.jpg)

> [!note] 📌
> **Linuxopsys **[***@linuxopsys:***](https://www.twitter.com/linuxopsys)
File and directory attributes can be set and removed using different commands and utilities. Let's explore some commonly used attributes and how to manage them.

> [!note] 📌
> **Linuxopsys **[***@linuxopsys:***](https://www.twitter.com/linuxopsys)
1. Immutable Attribute:

The immutable attribute prevents a file or directory from being modified, renamed, or deleted, even by the root user. It provides an extra layer of security to critical system files or sensitive data.

> [!note] 📌
> **Linuxopsys **[***@linuxopsys:***](https://www.twitter.com/linuxopsys)
To set the immutable attribute, use the chattr command with the +i option:

$ chattr +i <file or directory>

> [!note] 📌
> **Linuxopsys **[***@linuxopsys:***](https://www.twitter.com/linuxopsys)
To remove one or more attributes from a file, simply change the "operator" used in chattr. Use - instead of +

To remove the immutable attribute, use the chattr command with the  -i option instead of +i option:

$ chattr -i <file or directory>

> [!note] 📌
> **Linuxopsys **[***@linuxopsys:***](https://www.twitter.com/linuxopsys)
2. Append-Only Attribute:

The append-only attribute allows new data to be appended to a file but prevents any modifications or deletion of existing content. It is useful for log files or other data that should be preserved without being altered.

> [!note] 📌
> **Linuxopsys **[***@linuxopsys:***](https://www.twitter.com/linuxopsys)
To set the append-only attribute, use the chattr command with the +a option followed by a file or directory:

$ chattr +a <file or directory>

> [!note] 📌
> **Linuxopsys **[***@linuxopsys:***](https://www.twitter.com/linuxopsys)
To remove it, use the chattr command with the -a option:

$ chattr -a <file or directory>

> [!note] 📌
> **Linuxopsys **[***@linuxopsys:***](https://www.twitter.com/linuxopsys)
3. No-Dump Attribute:

The no-dump attribute excludes a file or directory from the system backup process. It is typically used for files that don't need to be backed up, such as temporary files or caches.

> [!note] 📌
> **Linuxopsys **[***@linuxopsys:***](https://www.twitter.com/linuxopsys)
To set the no-dump attribute, use the chattr command with the +d option:

$ chattr +d <file or directory>

> [!note] 📌
> **Linuxopsys **[***@linuxopsys:***](https://www.twitter.com/linuxopsys)
4. Secure Deletion Attribute:

The secure deletion attribute ensures that a file's data is securely overwritten when it is deleted, making it harder to recover. This attribute is often used for files containing sensitive information.

> [!note] 📌
> **Linuxopsys **[***@linuxopsys:***](https://www.twitter.com/linuxopsys)
To set the secure deletion attribute, use the chattr command with the +s option followed by the file or directory name:

$ chattr +s <file or directory>

> [!note] 📌
> **Linuxopsys **[***@linuxopsys:***](https://www.twitter.com/linuxopsys)
Here is a list of some attributes you can set on files and directories:

c - compressed: it causes the kernel to compress data written to the file automatically and uncompress it when it’s read back.

> [!note] 📌
> **Linuxopsys **[***@linuxopsys:***](https://www.twitter.com/linuxopsys)
e - extent format: it indicates that the file is using extents for mapping the blocks on disk.

j - data journaling: it ensures that on an Ext3 file system the file is first written to the journal and only after that to the data blocks on the hard disk.

> [!note] 📌
> **Linuxopsys **[***@linuxopsys:***](https://www.twitter.com/linuxopsys)
t - no tail-merging: Tail-merging is a process in which small data pieces at a file’s end that don’t fill a complete block are merged with similar pieces of data from other files.

> [!note] 📌
> **Linuxopsys **[***@linuxopsys:***](https://www.twitter.com/linuxopsys)
u - undeletable: When a file is deleted, its contents are saved which allows a utility to be developed that works with that information to salvage deleted files.

> [!note] 📌
> **Linuxopsys **[***@linuxopsys:***](https://www.twitter.com/linuxopsys)
A - no atime updates: Linux won’t update the access time stamp when you access a file.

D - synchronous directory updates: it makes sure that changes to files are written to disk immediately, and not to cache first.

> [!note] 📌
> **Linuxopsys **[***@linuxopsys:***](https://www.twitter.com/linuxopsys)
S - synchronous updates: the changes on a file are written synchronously on the disk.

T - and top of directory hierarchy: A directory will be deemed to be the top of directory hierarchies for the purposes of the Orlov block allocator.

> [!note] 📌
> **Linuxopsys **[***@linuxopsys:***](https://www.twitter.com/linuxopsys)
Listing files attributes

To list file attributes on Linux, you can use the lsattr utility. This utility is included in the e2fsprogs package of most commonly used Linux distributions (despite its name, it can also be used on filesystems other than ext2/3/4, eg xfs).

> [!note] 📌
> **Linuxopsys **[***@linuxopsys:***](https://www.twitter.com/linuxopsys)
This utility takes one or more files as arguments and supports numerous options to modify its behavior.

> [!note] 📌
> **Linuxopsys **[***@linuxopsys:***](https://www.twitter.com/linuxopsys)
When invoked with no arguments or options, lsattr returns a list of attributes associated with files and directories in the working directory, much like the ls command.

Here is an example.

$ lsattr

To list attributes for specific file or directory:

$ lsattr <file or dir>

> [!note] 📌
> **Linuxopsys **[***@linuxopsys:***](https://www.twitter.com/linuxopsys)
By utilizing file and directory attributes, you can enhance the security, integrity, and control of your system's files and directories. These attributes provide additional layers of protection and customization beyond traditional permissions and ACLs.

> [!note] 📌
> **Linuxopsys **[***@linuxopsys:***](https://www.twitter.com/linuxopsys)
That's it for today's thread.

Thank you taking your time to read it.

If you enjoyed this thread, follow us [**@linuxopsys**](https://www.twitter.com/linuxopsys) for future Linux posts, which we will be posting on a daily basis.