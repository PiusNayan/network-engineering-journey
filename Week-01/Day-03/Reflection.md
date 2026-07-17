# Reflection — Week 1 Day 3

Today I investigated how frames and packets actually move through a network. Before this lesson, I had a surface-level understanding that data "travels through the Internet," but I did not appreciate the specific mechanisms that make this possible.

The concept of packet switching clicked for me once I understood the contrast with circuit switching. Circuit switching reserves a dedicated path for the entire conversation — like booking a restaurant table that sits empty until you arrive. Packet switching is more like a courier service where each letter finds its own route and the roads are shared by everyone. The Internet chooses efficiency over guarantees, which is why delivery times can vary but bandwidth is used far more effectively.

Store-and-forward transmission was a detail I had not considered before. The idea that a router must receive the **entire packet** before forwarding it helps explain why larger packets introduce more delay at each hop. The delay formula L/R gave me a way to reason about this quantitatively, which feels like a significant step from purely conceptual thinking toward engineering thinking.

Queuing delays and packet loss made intuitive sense once I visualized the output buffer as a waiting room. When too many packets arrive at once and the waiting room is full, the newest arrivals are turned away — that is packet loss. Understanding this made congestion feel like a concrete, physical problem rather than an abstract network issue.

DNS was one of the most satisfying topics today because it answered a question I had always taken for granted: how does typing a web address actually lead to a connection? The hierarchical chain from the local cache down through the resolver, root server, TLD server, and finally the authoritative name server made the process feel logical and traceable.

MAC addresses completed the picture by explaining how communication works at the local level before IP takes over at the global level. The distinction between Layer 2 (MAC, switches, LAN) and Layer 3 (IP, routers, Internet) is something I now understand as a fundamental architectural boundary rather than just a fact to memorize.

Overall, Day 3 significantly deepened my understanding of how the Internet actually functions at a mechanical level. My goal for the next session is to connect these forwarding and addressing concepts to a practical Packet Tracer exercise where I can observe packet flow directly.
