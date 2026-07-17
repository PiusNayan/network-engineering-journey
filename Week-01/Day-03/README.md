# Week 01 • Day 03

## Session — How Frames Move Around a Network

Today's primary book is:

📘 Computer Networking: A Top-Down Approach

**Read:**
- Chapter 1
- Section 1.3 – The Network Core
- Section 1.4 – Delay, Loss, and Throughput in Packet-Switched Networks

**Why this book today?**
Because today's lesson focuses on understanding how the Internet's core actually moves data — through packet switching, queuing, and forwarding — before diving into supporting systems like DNS and MAC addressing.

---

## Session Objective

By the end of this session, you should be able to answer this question confidently:

> How does a frame or packet actually travel from one device to another across a network?

The goal is not just to name the steps, but to understand **why** each mechanism exists and what problem it solves.

---

## Think Before We Learn

Imagine you send a WhatsApp message from your phone to a friend on the other side of the country.

Consider these questions:
- Does your message travel as one whole unit, or is it broken up?
- Is a dedicated path reserved just for your message?
- How does the network know where to send it?
- How does your phone find the IP address of WhatsApp's servers?

These are exactly the questions today's lesson answers.

---

## The Journey of a Packet

A simplified view of how data moves from source to destination:

```text
Your Device (Source)
       │
       ▼
Packet is created and broken into smaller chunks
       │
       ▼
Packet enters the Network Core
       │
       ▼
Packet Switch reads the destination IP address
       │
       ▼
Router checks its Forwarding Table
       │
       ▼
Packet is sent to the next hop (store-and-forward)
       │
       ▼
Process repeats at each router until destination is reached
       │
       ▼
Destination Device (Host) receives and reassembles packets
```

---

## Core Topics Covered Today

### 1. Network Core and Packet Switching
The Internet's core is a mesh of packet switches and links. Instead of reserving a dedicated path, data is broken into packets that travel independently and are reassembled at the destination.

### 2. Store-and-Forward Transmission
A packet switch must receive the **entire packet** before it can begin forwarding it. The transmission delay per hop is **L/R** (packet size ÷ link rate).

### 3. Queuing Delays and Packet Loss
Output buffers absorb bursts of traffic. When a buffer fills up, arriving packets are dropped — this is **packet loss**. The amount of queuing delay depends on network congestion.

### 4. Forwarding Tables and Routing Protocols
Every router maintains a **forwarding table** that maps destination IP addresses to outbound links. **Routing protocols** automatically update these tables to reflect the best paths.

### 5. Circuit Switching
An alternative to packet switching used in traditional telephone networks. Resources are **reserved for the entire session** using either FDM (frequency bands) or TDM (time slots). Efficient for voice but wasteful during silence.

### 6. DNS — Domain Name System
The Internet's directory service. Translates domain names like `google.com` into IP addresses through a hierarchical query process: Cache → Resolver → Root → TLD → Authoritative Name Server.

### 7. MAC Addresses
A 48-bit hardware identifier burned into a Network Interface Card (NIC). Used at **Layer 2** (Data Link) for local communication within a LAN. Three types: Unicast, Multicast, Broadcast.

---

## Lesson Notes

Full detailed notes for today's topics are available here:

- [Day-03-How-Frames-Move-Around-a-Network.md](Notes/Day-03-How-Frames-Move-Around-a-Network.md)

---

## Practical Labs

| Lab | Status |
| --- | --- |
| Packet Tracer – Observing Packet Flow | ⏳ Pending |

---

## Session Checkpoint

Answer these questions in your own words:

1. Why does packet switching not guarantee delivery time, while circuit switching does?
2. What happens when a router's output buffer is completely full?
3. Why does a device need both a MAC address and an IP address to communicate on the Internet?
4. At what point in the DNS query process does caching help, and why?

---

## Key Takeaway

Data does not travel as a single block. It moves as small, independent packets that are forwarded hop-by-hop across the network. Each router reads the destination IP address, checks its forwarding table, and sends the packet one step closer to its destination. Supporting systems like DNS and MAC addressing make this process possible at both the local and global scale.
