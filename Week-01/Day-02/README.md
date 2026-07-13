# Week 01 • Day 02

## Session 1 — Network Components

Today’s primary book is:

📘 Computer Networking: A Top-Down Approach

**Read:**
- Chapter 1
- Section 1.2 – The Network Edge

**Why this book today?**
Because today’s lesson focuses on understanding what actually makes up a network. The book explains the devices and systems at the edge of the network before moving into protocols and deeper networking concepts.

---

## Session 1 Objective

By the end of this session, you should be able to answer this question confidently:

> What are the main components that make up a computer network?

The goal is not to memorize a list, but to understand the role of each component.

---

## Think Before We Learn

Imagine a computer lab where students are:
- Browsing the internet
- Printing assignments
- Accessing the student portal
- Watching videos during breaks

A simple question to consider is:

> What devices might be involved between a student’s laptop and a website such as www.upsa.edu.gh?

The focus is not on getting the exact order right, but on identifying the devices and systems that could be involved in the communication path.

---

## Building the Network Story

A typical communication path might look like this:

```text
Your Laptop
   │
   ▼
Wi-Fi Access Point or Ethernet Port
   │
   ▼
Switch
   │
   ▼
Router
   │
   ▼
ISP Network
   │
   ▼
The Internet
   │
   ▼
UPSA Web Server
```

Each component plays an important role in moving data from one device to another.

---

## The Five Main Components of a Network

### 1. End Devices (Hosts)
These are the devices that send or receive data.

Examples:
- Laptop
- Desktop
- Smartphone
- Printer
- Server
- IP Phone

### 2. Intermediary Devices
These are devices that move or manage data between end devices.

Examples:
- Switch
- Router
- Firewall
- Wireless Access Point

### 3. Transmission Media
This is how data travels between devices.

Examples:
- Ethernet cable
- Fiber optic cable
- Wi-Fi
- Radio waves

### 4. Services
Networks exist to provide useful services.

Examples:
- Websites
- Email
- File sharing
- Cloud storage
- Video streaming

### 5. Protocols
Protocols are the rules that allow devices to communicate in a consistent way.

Examples:
- TCP
- IP
- HTTP
- DNS
- DHCP

Think of protocols as the language or grammar of networking.

---

## Big Picture

A simple model to remember is:

```text
End Device
   │
Transmission Medium
   │
Intermediary Device
   │
Transmission Medium
   │
Intermediary Device
   │
Transmission Medium
   │
End Device
```

Every network, from a home Wi-Fi connection to the global internet, is built from these basic concepts.

---

## Session 1 Checkpoint

Answer these questions in your own words:

1. Why is a laptop called an end device instead of an intermediary device?
2. What would happen if a switch in an office stopped working?

These questions encourage you to think beyond memorization and focus on the purpose and behavior of each device.

---

## Troubleshooting Mindset

A network engineer must think about both physical and logical connectivity.

For example:
- Devices must be physically connected using the correct cables.
- Devices must also be logically configured, such as using valid IP addresses in the same subnet.

This is the kind of reasoning used in real-world troubleshooting and in CCNA-style practical exams.

---

## Key Takeaway

A computer network is made up of multiple components working together:
- End devices create and receive data
- Intermediary devices forward and direct traffic
- Transmission media carry the data
- Services provide the purpose of the network
- Protocols ensure devices can communicate correctly

Understanding these components helps you build a strong foundation for more advanced networking topics.
