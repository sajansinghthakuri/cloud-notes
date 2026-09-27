# Week 2 – Linux I: Filesystem, Users, Permissions & Packages

Date: August 23 2026

## Goal

Get comfortable working with Linux from the terminal and understand the fundamentals of the Linux filesystem, users, permissions, packages, and processes.

---

## Overview

This week was my first deeper dive into Linux.

Instead of relying on a graphical interface, I spent most of my time working directly from the terminal on my Ubuntu Server VM. The focus was on understanding how Linux organizes files, manages users and permissions, installs software, and handles running processes.

---

## Linux Filesystem

I started by exploring the Linux Filesystem Hierarchy Standard (FHS).

Some important directories I worked with:

```text
/
├── etc
├── var
├── usr
├── opt
├── proc
├── tmp
└── home
```

### What I learned

* `/etc` — system configuration files
* `/var` — variable data such as logs and application data
* `/usr` — user-space programs and libraries
* `/opt` — optional/additional software
* `/proc` — virtual filesystem containing information about processes and the kernel
* `/tmp` — temporary files
* `/home` — users' personal directories

Understanding where things belong makes navigating and troubleshooting a Linux system much easier.

---

## Navigation & File Management

I practiced the commands I will regularly use when working with Linux:

```bash
pwd
ls
cd
cp
mv
rm
mkdir
find
```

I also practiced using `locate` and `tree` to find and visualize files and directories.

### File Inspection

I worked with:

```bash
cat
less
head
tail
wc
file
stat
```

These commands helped me inspect files without relying on a GUI.

---

## Pipes, Redirection & Text Processing

One of the most useful parts of this week was learning how Linux commands can be combined.

### Redirection

```bash
>
>>
2>
```

### Pipes

```bash
|
```

Instead of running commands independently, I can pass the output of one command into another.

For example:

```bash
command1 | command2
```

I also practiced:

```bash
grep
cut
sort
uniq
tr
sed
awk
```

These tools are especially useful when working with large amounts of text and system data.

---

## Users & Groups

Linux is a multi-user operating system, so understanding users and groups is important.

I learned about:

```text
/etc/passwd
/etc/shadow
/etc/group
```

And practiced commands such as:

```bash
useradd
usermod
passwd
su
sudo
visudo
```

I also practiced creating users and groups and managing access between them.

---

## File Permissions

Linux permissions were an important part of this week.

The basic permission model is:

```text
r = read
w = write
x = execute
```

Permissions are applied to:

```text
User → Group → Others
```

I practiced both symbolic and numeric permissions.

Example:

```bash
chmod 755 script.sh
```

I also worked with:

```bash
chmod
chown
chgrp
umask
```

and learned the purpose of:

* SUID
* SGID
* Sticky Bit

Understanding permissions is essential because Linux systems rely heavily on controlled access to files and resources.

---

## Package Management

I learned how Ubuntu manages software packages.

Main tools:

```bash
apt
dpkg
```

I also learned about:

* Package repositories
* Installing packages
* Removing packages
* Holding packages
* Package versions
* Snap
* The basic differences between `apt`/`dpkg` and `dnf`/`yum`

---

## Processes

I started learning how Linux handles running programs.

Commands I practiced include:

```bash
ps
top
htop
kill
```

I also learned about:

* Process IDs (PIDs)
* Signals
* Foreground and background processes
* `jobs`
* `nohup`
* Process priority with `nice`

This helped me understand that applications running on Linux are represented as processes managed by the operating system.

---

## Hands-on Practice

During this week, I practiced directly on my Ubuntu Server VM.

Some of the exercises included:

* Exploring the Linux filesystem
* Creating and managing files and directories
* Working with pipes and redirection
* Searching and processing text
* Creating users and groups
* Managing file permissions
* Installing and removing packages
* Inspecting running processes
* Experimenting with permissions and fixing incorrect configurations

The hands-on practice was the most valuable part because it forced me to understand what each command was actually doing.

---

## What I Learned

A few things stood out to me this week:

1. Linux is much easier to understand when I stop thinking of commands as isolated instructions.
2. The filesystem structure gives Linux a predictable way to organize system files, configuration, applications, and user data.
3. Permissions are a fundamental part of Linux security.
4. Pipes and text-processing tools make the command line extremely powerful.
5. Understanding processes will be important when I move into services and system administration.

---

## Challenges

The areas that required the most practice were:

* Understanding Linux permissions
* Getting comfortable with pipes and redirection
* Remembering the different filesystem directories
* Understanding users, groups, and ownership
* Working with processes and signals

I found that practicing these concepts repeatedly was much more effective than trying to memorize them.

---

## Reflection

Week 2 was my first real step into Linux administration.

I'm still getting comfortable with the command line, but I can already see why Linux is such an important skill for cloud engineering. A lot of cloud infrastructure runs on Linux, so being comfortable in the terminal is something I want to develop properly rather than treating it as just another topic to finish.

Next week I'll continue with **Linux II**, focusing on **SSH, services, Bash, cron, and logs**. 🐧

---

## Next Week

**Week 3 — Linux II: SSH, Services, Bash, Cron & Logs**

* SSH and remote access
* System services
* Bash scripting
* Cron and scheduled tasks
* Logs
* Linux troubleshooting
