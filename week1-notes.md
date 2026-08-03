Week 1 – Computer Fundamentals & Virtualization

Date: August 2, 2026

Goal

Understand how computers work and how virtualization powers cloud computing. Before deploying applications to the cloud, it's important to understand the hardware and software that make it possible.

---

Overview

This week focused on the building blocks of computing. I learned how a CPU executes instructions, how memory and storage affect performance, how operating systems manage resources, and how virtualization allows multiple virtual machines to run on a single physical server.

These concepts form the foundation for everything I'll learn later in Linux, networking, containers, and cloud platforms like AWS.

---

Topics Covered

CPU Fundamentals

I learned how the CPU processes instructions and why it's considered the "brain" of a computer.

Key concepts:

- CPU cores and threads
- Clock speed (GHz)
- Instruction cycle (Fetch → Decode → Execute → Store)
- Context switching

Takeaway: More cores improve multitasking, while context switching allows multiple processes to share CPU time efficiently.

---

Memory Hierarchy

I explored how memory is organized based on speed and size.

Registers
   ↓
L1 Cache
   ↓
L2 Cache
   ↓
L3 Cache
   ↓
RAM
   ↓
SSD / HDD

Key takeaway: The closer memory is to the CPU, the faster it is—but it also becomes smaller and more expensive.

---

Storage

I compared different storage technologies and their use cases.

Storage| Characteristics
HDD| Slower, mechanical, inexpensive
SSD| Faster, no moving parts
NVMe SSD| Very high speed using PCIe

I also learned about:

- IOPS
- Throughput
- Filesystems
- Partitions
- RAID basics

Takeaway: Storage performance has a significant impact on application performance.

---

Operating Systems

I studied how an operating system acts as the bridge between hardware and applications.

Topics included:

- Kernel vs User Space
- Processes vs Threads
- CPU Scheduling
- System Calls

Takeaway: The kernel is responsible for managing hardware resources and enabling applications to communicate with the system.

---

Virtualization

This was one of my favorite topics this week.

I learned:

- What a hypervisor is
- Type 1 vs Type 2 hypervisors
- Host vs Guest operating systems
- Why cloud providers use virtualization
- The difference between Virtual Machines and Containers

Since I'm using VirtualBox, I'm working with a Type 2 Hypervisor.

Takeaway: Cloud virtual machines are virtual computers running on powerful physical servers using virtualization technology.

---

Binary & Hexadecimal

I practiced converting between:

- Decimal
- Binary
- Hexadecimal

I also learned the difference between:

- Bits vs Bytes
- GB vs GiB

These concepts are important when working with networking, storage, and cloud infrastructure.

---

Hands-on Practice

During this week I:

- Continued working with my Ubuntu Server virtual machine.
- Practiced basic binary conversions.
- Reviewed virtualization concepts.
- Expanded my Markdown notes.
- Tracked my progress using Git and GitHub.

---

Key Takeaways

- Cloud computing starts with strong computer fundamentals.
- Understanding hardware makes cloud services easier to understand.
- Virtualization is one of the core technologies behind modern cloud platforms.
- Memory and storage performance directly affect system performance.
- Documenting what I learn helps reinforce concepts and measure progress.

---

Challenges

Some topics were completely new to me, especially:

- CPU scheduling
- Context switching
- Memory latency
- Binary conversions

After reviewing the concepts and practicing, they started to make much more sense.

---

Reflection

Week 1 showed me that cloud engineering is much more than learning AWS or deploying virtual machines. Every cloud service is built on computer science fundamentals.

Building this foundation now will make it easier to understand Linux, networking, containers, and cloud architecture in the weeks ahead.

---

Next Week

Week 2 – Linux Fundamentals

Next, I'll begin learning Linux, including:

- Linux file system
- Essential terminal commands
- Users and permissions
- Shell basics
- File management
- Linux administration

I'm excited to start working more directly with Ubuntu Server and become comfortable using the command line.