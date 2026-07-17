# How Frames Move Around a Network
Week 1 • Day 3

Date: Thursday, 17 July 2026

---

# Learning Objectives

* Understand how the network core operates using packet switching.
* Explain store-and-forward transmission and calculate basic packet transmission delay.
* Describe queuing delays and the conditions that cause packet loss.
* Understand how forwarding tables and routing protocols direct traffic.
* Compare packet switching to circuit switching.
* Explain FDM and TDM as multiplexing techniques in circuit-switched networks.
* Describe the purpose and query process of the Domain Name System (DNS).
* Identify the structure, types, and role of MAC addresses at Layer 2.

---

# Recommended Resources

## Books

* Computer Networking: A Top-Down Approach
    * Chapter 1:
        - Section 1.3 – The Network Core
        - Section 1.4 – Delay, Loss, and Throughput in Packet-Switched Networks

## Videos

* Jeremy's IT Lab – How Data Moves Through a Network
* PowerCert – Packet Switching vs Circuit Switching

## Websites

* Cloudflare Learning Center – What is DNS?
* Cisco – Understanding MAC Addresses

---

# Key Concepts

## 1. Network Core

### Definition
The network core is the mesh of packet switches and links that interconnects the Internet's end systems.

### Explanation
The Internet's core operates on the principle of **Packet Switching**. Rather than establishing a dedicated connection for the entire duration of a session, data is broken into packets that travel independently through the network and are reassembled at the destination.

---

## 2. Packet Switching

### Definition
A method of transmitting data in which messages are broken into smaller chunks called **packets**. Each packet travels independently through communication links and packet switches from source to destination.

### Sub-concepts

#### 2a. Store-and-Forward Transmission

Most packet switches use **store-and-forward transmission** at the inputs to the links.

> **Key Rule:** The packet switch must receive the **entire packet** before it can begin to transmit the first bit onto the outbound link.

**Packet Transmission Delay Formula:**

```
Delay = L / R

Where:
  L = Size of the packet in bits
  R = Transmission rate of the link in bits per second (bps)
```

**Example:**
If a packet is 1,000 bits and the link rate is 1 Mbps (1,000,000 bps):

```
Delay = 1,000 / 1,000,000 = 0.001 seconds (1 millisecond)
```

#### 2b. Queuing Delays and Packet Loss

Each packet switch has an **output buffer** (also called an output queue) for each attached link. This buffer stores packets waiting to be transmitted.

| Situation | Result |
| --- | --- |
| Link is free when packet arrives | Packet is transmitted immediately |
| Link is busy when packet arrives | Packet waits in output buffer (queuing delay) |
| Buffer is completely full | **Packet loss** occurs — either the arriving packet or a queued packet is dropped |

> **Key Insight:** Queuing delays are variable and depend on the level of congestion in the network. Buffer space is finite, which is why packet loss can happen.

#### 2c. Forwarding Tables and Routing Protocols

Every device on the Internet has a hierarchical **IP address**, which is attached to a data packet's header. Routers use this address to decide where to send each packet.

**Process:**

```
Packet arrives at router
        │
        ▼
Router reads destination IP address from packet header
        │
        ▼
Router checks its Forwarding Table
        │
        ▼
Table maps the IP address to a specific outbound link
        │
        ▼
Packet is forwarded to the next hop
```

> **Key Insight:** Forwarding tables are updated automatically by **routing protocols**, which calculate the best and shortest paths across the network. This process happens hop-by-hop across the network.

---

## 3. Circuit Switching

### Definition
In circuit-switched networks, resources such as transmission rates and buffers are **reserved for the entire duration** of the communication session, establishing a dedicated connection with a guaranteed constant rate.

### Comparison

| Feature | Packet Switching | Circuit Switching |
| --- | --- | --- |
| Resource reservation | No — on demand | Yes — pre-reserved |
| Delivery guarantee | Best effort | Guaranteed rate |
| Efficiency | High (shares resources) | Low (idle slots wasted) |
| Example | The Internet | Traditional telephone lines |

### Real-World Analogy
Circuit switching is like making a **restaurant reservation in advance** — your table (resources) is held for you even if you arrive late. Packet switching is like a **walk-in restaurant** — you use a table only when you actually need one.

### 3a. Multiplexing in Circuit-Switched Networks

Circuit-switched networks manage multiple connections on a single link using one of two methods:

#### Frequency-Division Multiplexing (FDM)

* Divides the communication link's **frequency spectrum** into dedicated bands.
* Each connection is assigned its own frequency band for the entire session.
* The band remains reserved and **unused during silent periods**.

#### Time-Division Multiplexing (TDM)

* Divides time into revolving **frames**, and each frame is divided into a fixed number of time slots.
* Each connection is assigned a dedicated time slot in every frame.
* Like FDM, the slot is **reserved and idle during silent periods**.

> **Key Criticism of Circuit Switching:** It can be highly wasteful. Reserved frequency bands or time slots remain completely unused during any idle or silent periods in a communication session.

---

## 4. Domain Name System (DNS)

### Definition
The Domain Name System (DNS) is the Internet's directory service. It translates human-friendly **domain names** (e.g., `yahoo.com`) into numeric **IP addresses** that computers use to communicate.

### Analogy
DNS acts like a **digital phonebook** — you look up a name and get back a number.

### The DNS Query Process

```
User types a URL (e.g., www.google.com)
        │
        ▼
1. Cache Check: Browser or OS checks its local cache
        │ (not found)
        ▼
2. Resolver Server: Request goes to the Resolver (often your ISP)
        │ (not found)
        ▼
3. Root Server: Directs the resolver to the correct TLD server
        │
        ▼
4. TLD Server: Top-Level Domain server (.com, .net, .org)
              directs request to the Authoritative Name Server
        │
        ▼
5. Authoritative Name Server: Returns the specific IP address
        │
        ▼
6. Resolver caches the IP for future requests
        │
        ▼
Browser connects to the web server using the IP address
```

| Component | Role |
| --- | --- |
| Local Cache | Fastest lookup — checks browser/OS memory first |
| Resolver Server | First external stop, usually provided by ISP |
| Root Server | Knows which TLD server to contact |
| TLD Server | Manages domain extensions (.com, .net, .org) |
| Authoritative Name Server | Holds the definitive IP address for the domain |

> **Key Insight:** Caching speeds up future DNS lookups. Once the IP is retrieved, the resolver saves it so the same query doesn't need to travel the full chain again.

---

## 5. MAC Address

### Definition
A **Media Access Control (MAC) address** is a unique physical identifier assigned to a Network Interface Card (NIC). Unlike IP addresses, MAC addresses are "burnt into" the hardware by the manufacturer and are considered permanent (though they can be spoofed).

### Specification
* **Size:** 48 bits (6 bytes)
* **Written as:** 12 hexadecimal digits

### Structure of a MAC Address

```
| First 24 bits (OUI)                | Last 24 bits (Unique Value)          |
| Organizationally Unique Identifier | Assigned by the vendor               |
| Identifies the manufacturer        | Ensures global uniqueness per device |
```

**Example:**
```
AA:BB:CC:DD:EE:FF
└──────┬──────┘ └──────┬──────┘
  OUI (Vendor)    Unique Device ID
```

### Types of MAC Addresses

| Type | Description | Representation |
| --- | --- | --- |
| Unicast | Traffic sent to a single specific device | Unique per NIC |
| Multicast | Traffic sent to a group of devices listening for a specific protocol/application | Specific group address |
| Broadcast | Traffic sent to all devices on the local network | All F's — `FF:FF:FF:FF:FF:FF` |

### Display Formats by Operating System

| Operating System | Format | Example |
| --- | --- | --- |
| Linux / macOS | 6 groups of 2, separated by colons | `aa:bb:cc:dd:ee:ff` |
| Microsoft Windows | 6 groups of 2, separated by dashes | `AA-BB-CC-DD-EE-FF` |
| Cisco IOS | 3 groups of 4, separated by dots | `aabb.ccdd.eeff` |

### MAC vs. IP Addresses

| Attribute | MAC Address | IP Address |
| --- | --- | --- |
| OSI Layer | Layer 2 — Data Link | Layer 3 — Network |
| Scope | Local communication within a LAN | Global communication across the Internet |
| Used by | Switches | Routers |
| Assigned by | Manufacturer (hardware) | Network administrator or DHCP |
| Permanence | Permanent (hardware-burned) | Dynamic or static |

> **Key Insight:** MAC addresses handle communication **within** a local network (LAN). IP addresses handle communication **beyond** the local network. Both are needed for end-to-end communication.

---

# Key Takeaways

* The Internet's core uses **packet switching** — data is broken into packets that travel independently and are reassembled at the destination.
* **Store-and-forward** means a switch must receive the entire packet before forwarding it. Delay = L/R.
* **Output buffers** absorb bursts of traffic, but when full, **packet loss** occurs.
* **Routing protocols** automatically update forwarding tables so packets always find the best path.
* **Circuit switching** reserves resources for the entire session, guaranteeing a rate but wasting bandwidth during idle periods (FDM and TDM).
* **DNS** translates domain names to IP addresses through a hierarchical chain: Cache → Resolver → Root → TLD → Authoritative.
* A **MAC address** is a 48-bit hardware identifier used for Layer 2 (LAN) communication, while IP addresses are used for Layer 3 (Internet) communication.

---

# Common Mistakes

* Confusing **forwarding** (looking up the table and sending the packet) with **routing** (the process that builds and updates the table).
* Thinking MAC addresses and IP addresses serve the same purpose — they operate at different OSI layers and different scopes.
* Assuming circuit switching is more reliable than packet switching — circuit switching reserves resources but wastes them during silence; packet switching is more efficient overall.
* Forgetting that **broadcast MAC address** (`FF:FF:FF:FF:FF:FF`) reaches every device on the local network — this is used in protocols like ARP.

---

# CCNA Exam Tips

* Know the store-and-forward delay formula: **Delay = L / R** and be able to calculate it for multi-hop paths.
* Remember the three MAC address types: **Unicast, Multicast, Broadcast**.
* Know the DNS resolution hierarchy in order: **Cache → Resolver → Root → TLD → Authoritative Name Server**.
* Know which layer each address type operates at: MAC = Layer 2, IP = Layer 3.
* Remember the MAC address size: **48 bits / 6 bytes / 12 hex digits**.
* Know the difference between FDM and TDM in circuit-switched networks.
