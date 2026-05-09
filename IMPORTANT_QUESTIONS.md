# DCCN — IMPORTANT QUESTIONS (MODEL EXAM ANSWERS)
**Course:** BCA / B.Sc(IT) | **Subject Code:** US6001 | **Sem VI**

> 📝 The answers below are written **as if a student is writing them in the exam answer sheet** — with full introduction, diagrams, working, tables, and conclusion. Read once, replicate the structure in your exam.

---

# 🔴 TOP 10 MOST LIKELY 5-MARK QUESTIONS

---

## Q1. Compare OSI and TCP/IP Models.

**Answer:**

The **OSI (Open Systems Interconnection)** model was developed by **ISO in 1984** as a 7-layer reference architecture for network communication. The **TCP/IP model** is the practical 4-layer protocol stack that powers the actual Internet.

Both models follow a layered approach but differ in number of layers, design philosophy, and adoption.

**Diagram — Layer Mapping:**

```
   OSI Model                    TCP/IP Model
+-----------------+         +-------------------+
| 7. Application  |         |                   |
+-----------------+         |                   |
| 6. Presentation |  ←→     |   Application     |
+-----------------+         |                   |
| 5. Session      |         |                   |
+-----------------+         +-------------------+
| 4. Transport    |  ←→     |   Transport       |
+-----------------+         +-------------------+
| 3. Network      |  ←→     |   Internet        |
+-----------------+         +-------------------+
| 2. Data Link    |         |                   |
+-----------------+  ←→     |   Network Access  |
| 1. Physical     |         |                   |
+-----------------+         +-------------------+
```

**Difference Table:**

| Feature | OSI Model | TCP/IP Model |
|---------|-----------|--------------|
| Number of layers | 7 | 4 (or 5) |
| Developed by | ISO (1984) | DARPA (1970s) |
| Approach | Theoretical reference | Practical implementation |
| Application equivalent | Application + Presentation + Session | Single Application layer |
| Transport layer | Strict (TP0–TP4) | TCP and UDP |
| Layer dependency | Strictly hierarchical | Loosely coupled |
| Adoption | Mostly conceptual | Used in Internet |

**Conclusion:** The OSI model is a *theoretical guideline* that helps us understand network design, while TCP/IP is the *real-world model* implemented across the Internet. Most modern networking concepts are taught using OSI but built using TCP/IP.

---

## Q2. Explain CSMA/CD with Flowchart.

**Answer:**

**CSMA/CD** stands for **Carrier Sense Multiple Access with Collision Detection**. It is the medium access control protocol used in **wired Ethernet (IEEE 802.3)** networks, where multiple stations share a common transmission medium.

The protocol works in three phases — *carrier sensing, transmission, and collision detection*.

**Working:**

1. Before transmitting, a station **senses the channel** to check if it is idle.
2. If the channel is **busy**, the station waits (according to persistence rule).
3. If the channel is **idle**, the station starts transmitting.
4. While transmitting, it continues to **listen for collisions**.
5. If a collision is detected, the station immediately **stops transmitting and sends a Jam signal** (32–48 bits) to inform all other stations.
6. The station then waits for a **random backoff time** (Binary Exponential Backoff) and **retries**.

**Flowchart:**

```
        START
          |
          v
   +---------------+
   | Sense Channel |
   +---------------+
          |
          v
       Idle?
       /    \
     No      Yes
     |        |
     v        v
   Wait    Transmit Frame
     |        |
     +--->    v
         Continue Listening
              |
              v
         Collision?
         /        \
       Yes         No
        |           |
        v           v
   Send Jam      Frame Sent OK
   Signal           |
        |           v
        v         STOP
   Backoff (BEB)
        |
        +-----> Retry
```

**Used in:** Original Ethernet (10BASE-T, 100BASE-TX). Modern switched Ethernet does not need CSMA/CD as switches eliminate collisions, but the protocol is still part of the standard.

**Conclusion:** CSMA/CD ensures fair channel access and detects collisions in a wired LAN, allowing efficient retransmission and reducing wasted bandwidth.

---

## Q3. Differentiate between TCP and UDP.

**Answer:**

**TCP (Transmission Control Protocol)** and **UDP (User Datagram Protocol)** are the two main transport-layer protocols in the TCP/IP suite. TCP is **connection-oriented and reliable**, while UDP is **connectionless and unreliable**.

**Difference Table:**

| Feature | TCP | UDP |
|---------|-----|-----|
| Type | Connection-oriented | Connectionless |
| Reliability | Reliable (ACK + retransmission) | Unreliable (no ACK) |
| Order | Maintains sequence | No order guarantee |
| Speed | Slower (more overhead) | Faster |
| Header size | 20–60 bytes | 8 bytes |
| Flow control | Yes (sliding window) | No |
| Congestion control | Yes (slow start, etc.) | No |
| Connection setup | 3-way handshake | Not required |
| Error checking | Yes + recovery | Yes (only detection) |
| Use cases | HTTP, FTP, SMTP, SSH | DNS, DHCP, video, gaming, VoIP |

**Header Comparison Diagram:**

```
TCP HEADER (20 bytes minimum)        UDP HEADER (8 bytes)
+----------------------------+       +----------------+
| Source Port | Dest Port    |       | Src | Dst Port |
+----------------------------+       +----------------+
| Sequence Number            |       | Length |Cksum  |
+----------------------------+       +----------------+
| ACK Number                 |
+----------------------------+
| HLen | Flags | Window      |
+----------------------------+
| Checksum  | Urgent Pointer |
+----------------------------+
```

**Conclusion:** TCP is preferred when **reliability and ordered delivery** are critical (web pages, email, file transfer); UDP is preferred when **speed matters more than reliability** (real-time streaming, online gaming, DNS).

---

## Q4. Explain the working of Go-Back-N ARQ Protocol with Diagram.

**Answer:**

**Go-Back-N ARQ** is a **sliding-window pipelined protocol** used at the data link or transport layer for reliable data transfer. It allows the sender to send up to **N unacknowledged frames** at a time without waiting for individual ACKs.

**Rules of operation:**

1. Sender's window size = **N**; receiver's window size = **1**.
2. Sender uses **cumulative ACK** — ACK *n* means "all frames up to *n-1* have been received correctly."
3. The receiver discards out-of-order frames (no buffering).
4. If a frame is lost or corrupted, the receiver does not send an ACK for it.
5. On **timeout**, the sender retransmits the lost frame **and all subsequent frames** in the window.

**Diagram (Window N = 4, F2 lost):**

```
Sender →   F0   F1   F2   F3   F4   F5   ...
            ↓    ↓    ✗    ↓    ↓
Receiver ← F0✓  F1✓       F3✗  F4✗   (out of order — discarded)
            ↑    ↑
           ACK1 ACK2  (cumulative — last in-order received was F1)

         [TIMEOUT for F2]
                                   ↓
Sender →   F2   F3   F4   F5   (retransmit ALL)
            ↓    ↓    ↓    ↓
Receiver ← F2✓  F3✓  F4✓  F5✓
            ↑    ↑    ↑    ↑
           ACK3 ACK4 ACK5 ACK6
```

**Efficiency:** η = N / (1 + 2a), where a = T_propagation / T_transmission.

**Advantages:** Better channel utilization than Stop-and-Wait, simple receiver design (no buffering).
**Disadvantages:** Wastes bandwidth on retransmission of correctly received frames.

**Conclusion:** Go-Back-N is widely used because it provides good throughput on high-bandwidth links while keeping the receiver implementation simple.

---

## Q5. Explain Hamming Code Construction with Example.

**Answer:**

**Hamming Code** is a **single-bit error detection and correction** code that adds redundant parity bits at positions which are powers of 2 (1, 2, 4, 8, …) to the data bits.

**Rule:** For *m* data bits, *p* parity bits are required such that **2ᵖ ≥ m + p + 1**.

**Example: Construct 7-bit Hamming Code for data 1011 using even parity.**

**Step 1 — Position layout:**
- Positions 1, 2, 4 → parity bits (P1, P2, P4)
- Positions 3, 5, 6, 7 → data bits (D1, D2, D3, D4)
- Data 1011 → D1=1, D2=0, D3=1, D4=1

| Position | 1 | 2 | 3 | 4 | 5 | 6 | 7 |
|---------|---|---|---|---|---|---|---|
| Type | P1 | P2 | D1 | P4 | D2 | D3 | D4 |
| Bit | ? | ? | 1 | ? | 0 | 1 | 1 |

**Step 2 — Calculate parity bits (even parity):**
- **P1** covers positions 1, 3, 5, 7 → P1 ⊕ 1 ⊕ 0 ⊕ 1 = 0 → **P1 = 0**
- **P2** covers positions 2, 3, 6, 7 → P2 ⊕ 1 ⊕ 1 ⊕ 1 = 0 → **P2 = 1**
- **P4** covers positions 4, 5, 6, 7 → P4 ⊕ 0 ⊕ 1 ⊕ 1 = 0 → **P4 = 0**

**Hamming Codeword: 0 1 1 0 0 1 1 = 0110011**

**Step 3 — Error detection (suppose received 1011011):**

| Position | 1 | 2 | 3 | 4 | 5 | 6 | 7 |
|---------|---|---|---|---|---|---|---|
| Bit | 1 | 0 | 1 | 1 | 0 | 1 | 1 |

- C1 = 1 ⊕ 1 ⊕ 0 ⊕ 1 = **1**
- C2 = 0 ⊕ 1 ⊕ 1 ⊕ 1 = **1**
- C4 = 1 ⊕ 0 ⊕ 1 ⊕ 1 = **1**

**Syndrome = C4 C2 C1 = 111 = 7** → Error in **bit 7**. Flip bit 7 → **Corrected: 1011010**.

**Conclusion:** Hamming code can detect and correct single-bit errors using the syndrome value, which directly indicates the position of the erroneous bit.

---

## Q6. Explain ICMP and its Types of Messages.

**Answer:**

**ICMP (Internet Control Message Protocol)** is a network-layer protocol used by IP to send **error-reporting and diagnostic messages**. ICMP is encapsulated within IP datagrams (protocol number 1) but is itself part of the IP suite.

ICMP messages are mainly used by routers and hosts to communicate errors and query network conditions, e.g., **ping** (Echo) and **traceroute** (Time Exceeded).

**ICMP Messages are categorized into two types:**

### A. Error-Reporting Messages

1. **Destination Unreachable (Type 3)** — sent when a router cannot deliver an IP packet (host/network/port unreachable).
2. **Source Quench (Type 4)** — sent for congestion control (deprecated).
3. **Time Exceeded (Type 11)** — sent when TTL expires; used by traceroute.
4. **Parameter Problem (Type 12)** — sent when there is an issue in the IP header.
5. **Redirect (Type 5)** — informs sender of a better route.

### B. Query Messages

1. **Echo Request / Echo Reply (Type 8 / 0)** — used by **ping** to check connectivity.
2. **Timestamp Request / Reply (Type 13 / 14)** — for clock synchronization.
3. **Address Mask Request / Reply (Type 17 / 18)** — to find the subnet mask.
4. **Router Solicitation / Advertisement (Type 10 / 9)** — host discovers routers.

**Diagram — ICMP Encapsulation:**

```
+-------------------+-------------------+----------------+
| IP Header         | ICMP Header (8B)  | ICMP Data      |
+-------------------+-------------------+----------------+
                    | Type | Code | Cks | Rest of header |
                    +------+------+-----+----------------+
```

**Conclusion:** ICMP is the *helper* protocol of IP — it does not transport user data but reports errors and supports diagnostics like ping and traceroute, making it essential for network troubleshooting.

---

## Q7. Compare Symmetric and Asymmetric Cryptography.

**Answer:**

**Cryptography** is the science of secure communication using mathematical algorithms. It is divided into two main types based on the keys used.

**Symmetric Key Cryptography** uses the **same secret key** for both encryption and decryption. **Asymmetric Key Cryptography** uses a pair of mathematically related keys — a **public key** for encryption and a **private key** for decryption.

**Diagram:**

```
SYMMETRIC                          ASYMMETRIC
Plain → [Encrypt-K]→ Cipher        Plain → [Encrypt-PubKey] → Cipher
Cipher → [Decrypt-K]→ Plain        Cipher → [Decrypt-PrivKey] → Plain
        ↑ Same Key                       ↑ Different Keys
```

**Difference Table:**

| Feature | Symmetric Key | Asymmetric Key |
|---------|--------------|----------------|
| Number of keys | 1 (shared) | 2 (public + private) |
| Speed | Fast | Slow |
| Key length | 56–256 bits | 1024–4096 bits |
| Key distribution | Difficult | Easy (publish public key) |
| Algorithms | DES, 3DES, AES, Blowfish | RSA, ECC, DSA, Diffie-Hellman |
| Use case | Bulk data encryption | Key exchange, digital signature |
| Computational cost | Low | High |

**Real-world example:** TLS/SSL combines both — asymmetric (RSA) for key exchange, then symmetric (AES) for actual data encryption.

**Conclusion:** Both cryptography systems are essential — symmetric is faster for bulk data, asymmetric is safer for key exchange and authentication. Together they form the backbone of modern internet security.

---

## Q8. Explain Three-Way Handshake with Diagram.

**Answer:**

The **Three-Way Handshake** is the procedure used by TCP to **establish a reliable connection** between client and server before data exchange begins. It synchronizes the **sequence numbers** of both sides and verifies that both are alive and ready.

**Working (3 Steps):**

1. **SYN (Synchronize):** Client sends a TCP segment with SYN flag set and an initial sequence number `seq = x`.
2. **SYN + ACK:** Server replies with SYN and ACK flags set, choosing its own `seq = y` and acknowledging client's seq with `ack = x + 1`.
3. **ACK:** Client sends ACK with `ack = y + 1`. Connection is now ESTABLISHED.

**Diagram:**

```
   CLIENT                                 SERVER
     |                                       |
     | -------- SYN, seq = x --------------> |   (Step 1)
     |                                       |
     | <----- SYN, ACK, seq = y, ack = x+1 - |   (Step 2)
     |                                       |
     | -------- ACK, ack = y+1 ------------> |   (Step 3)
     |                                       |
     |======= Connection Established ========|
     |                                       |
     | <======= Data Transfer =============> |
```

**Problem solved by 3-way handshake:**

- **Synchronization** of both sides' sequence numbers.
- Prevents **old duplicate connection requests** from creating false connections.
- Ensures both client and server are **alive and ready** to exchange data.

**Conclusion:** The three-way handshake is fundamental to TCP's reliability — without it, sequence numbers cannot be agreed upon and reliable transmission would be impossible.

---

## Q9. Explain Leaky Bucket Algorithm.

**Answer:**

The **Leaky Bucket** is a **traffic-shaping algorithm** used in computer networks to **control the rate of data flow** and convert bursty traffic into a smooth, constant rate.

**Concept:** Imagine a bucket with a small hole at the bottom. Water (data packets) is **poured in at any rate**, but **leaks out at a constant rate**. If the bucket overflows, excess water (packets) is discarded.

**Diagram:**

```
       Host (bursty input)
              ↓ ↓ ↓
           ┌───────┐
           │ FIFO  │  ← bucket (queue)
           │ queue │
           │_______│
                 |
                 ↓  (constant output rate)
            Network
```

**Working:**

1. Packets arriving from the host are placed into a **FIFO queue (bucket)**.
2. Packets are **transmitted at a fixed rate** (e.g., 10 packets/sec) regardless of the input rate.
3. If the bucket is full when a packet arrives, the packet is **dropped (overflow)**.
4. This guarantees that the output rate to the network is always ≤ the leak rate.

**Algorithm (in pseudocode):**

```
when a packet arrives:
   if bucket is full:
       discard packet
   else:
       add packet to queue

every (1/leak_rate) seconds:
   if queue is not empty:
       transmit packet
```

**Advantage:** Simple, ensures constant output rate, prevents network congestion.
**Disadvantage:** Cannot accommodate occasional legitimate bursts (Token Bucket addresses this).

**Conclusion:** The Leaky Bucket algorithm enforces a steady transmission rate by smoothing out bursty traffic, making it ideal for traffic policing in routers.

---

## Q10. Explain DNS Hierarchy and Resolution Process.

**Answer:**

**DNS (Domain Name System)** is a **hierarchical, distributed** naming system that translates human-friendly **domain names** (e.g., google.com) into machine-readable **IP addresses** (e.g., 142.250.190.46). DNS uses **UDP port 53** (TCP for zone transfers).

**DNS Hierarchy (Inverted Tree):**

```
                    [ Root DNS Servers ]   ← 13 globally (a.root-servers.net …)
                          |
        +----------+------+------+------------+
        |          |             |            |
     [.com]    [.org]         [.edu]       [.in]      ← TLD Servers
        |          |             |            |
   [google.com] [wikipedia.org] [mit.edu] [iitb.ac.in] ← Authoritative DNS
        |
   [www, mail, drive, …]                              ← Hosts
```

**Levels of DNS Servers:**

1. **Root Name Servers** — top-level directory of TLDs.
2. **TLD (Top-Level Domain) Servers** — manage `.com`, `.org`, `.in`, etc.
3. **Authoritative DNS Servers** — store actual IP records for domains.
4. **Local (Recursive) DNS Servers** — run by ISPs, cache responses.

**Resolution Process (Recursive Query):**

```
Step 1: Client → Local DNS: "What is the IP of www.google.com?"
Step 2: Local DNS → Root: asks for .com TLD server
Step 3: Root → returns address of .com TLD
Step 4: Local DNS → .com TLD: asks for google.com
Step 5: TLD → returns google's authoritative server
Step 6: Local DNS → google's authoritative: asks for www
Step 7: Authoritative → returns IP (142.250.190.46)
Step 8: Local DNS caches answer and returns to client
```

**DNS Record Types:**

| Record | Purpose |
|--------|---------|
| **A** | Domain → IPv4 |
| **AAAA** | Domain → IPv6 |
| **MX** | Mail exchanger |
| **CNAME** | Alias |
| **NS** | Name server |
| **PTR** | Reverse lookup (IP → name) |

**Conclusion:** DNS acts as the *phonebook of the Internet* — without it, users would have to memorize numeric IP addresses. Its hierarchical, cached, and distributed nature makes it scalable to the entire global internet.

---

# 🟠 TOP 10 MOST LIKELY 10-MARK QUESTIONS

---

## Q1. Explain the OSI Reference Model with all 7 Layers and their Functions.

**Answer:**

The **OSI (Open Systems Interconnection)** model is a **7-layer conceptual framework** developed by the **International Organization for Standardization (ISO)** in **1984**. It describes how data communication should occur between two devices in a network. Each layer performs a specific role and provides services to the layer above it.

**Mnemonic (top to bottom):** *All People Seem To Need Data Processing*

**Diagram — 7-Layer OSI Stack:**

```
+------------------------+
|  7. Application Layer  |   ← User interface (HTTP, FTP, SMTP)
+------------------------+
|  6. Presentation Layer |   ← Encryption, Compression, Translation
+------------------------+
|  5. Session Layer      |   ← Dialog control, synchronization
+------------------------+
|  4. Transport Layer    |   ← End-to-end delivery (TCP, UDP)
+------------------------+
|  3. Network Layer      |   ← Routing, logical addressing (IP)
+------------------------+
|  2. Data Link Layer    |   ← Framing, MAC addressing, error control
+------------------------+
|  1. Physical Layer     |   ← Bits as electrical signals
+------------------------+
```

**Layer-by-Layer Functions:**

| # | Layer | Function | PDU | Devices/Protocols |
|---|-------|----------|-----|-------------------|
| 1 | **Physical** | Transmits raw bits as signals; deals with cables, voltages, pins | Bit | Hub, Repeater, Cables |
| 2 | **Data Link** | Frames data, adds MAC addresses, handles errors and flow on a single link | Frame | Switch, Bridge, Ethernet |
| 3 | **Network** | Logical addressing (IP), routing across networks | Packet | Router, IP, ICMP |
| 4 | **Transport** | End-to-end (process-to-process) delivery, reliability, flow & congestion control | Segment | TCP, UDP |
| 5 | **Session** | Establishes, maintains, and synchronizes sessions between applications | Data | NetBIOS, RPC |
| 6 | **Presentation** | Translation (ASCII/Unicode), encryption, compression | Data | SSL, JPEG, MIME |
| 7 | **Application** | Services to end-user; HTTP, FTP, SMTP, DNS | Data | Browser, Email client |

**Encapsulation Process:**

When data moves down the stack, each layer adds its own header (and sometimes trailer):

```
Data (App)
| + L6 Header → Data
| + L5 Header → Data
| + L4 Header → SEGMENT
| + L3 Header → PACKET
| + L2 Header + Trailer → FRAME
| + L1 (signals) → BITS
```

The receiver reverses this process (decapsulation) at each layer.

**Why is OSI important?**

- Provides a **standard reference** for designing network protocols.
- Each layer is **independent** — change in one does not affect others.
- Helps in **troubleshooting** — issues can be isolated to a specific layer.
- Promotes **interoperability** between devices from different vendors.

**Conclusion:** The OSI model is the *foundation of network theory*. Although the actual Internet uses the simpler TCP/IP stack, the OSI model remains the dominant teaching framework because it cleanly separates network responsibilities across layers.

---

## Q2. Compare and Contrast all ARQ Protocols (Stop-and-Wait, Go-Back-N, Selective Repeat) with Diagrams.

**Answer:**

**ARQ (Automatic Repeat reQuest)** protocols are **error-control mechanisms** at the data link or transport layer. They use **acknowledgements (ACKs)** and **timeouts** to ensure reliable data delivery over unreliable channels. There are three main types: **Stop-and-Wait, Go-Back-N, and Selective Repeat**.

### 1. Stop-and-Wait ARQ

The sender transmits **one frame** and waits for its ACK before sending the next.

**Diagram:**
```
Sender:    F0 → → →     F1 → → →
                ← ACK0          ← ACK1
Receiver:    F0✓             F1✓
```

**Pros:** Simple to implement.
**Cons:** Very low channel utilization on high-bandwidth or long-delay links.
**Efficiency:** η = 1 / (1 + 2a) where a = T_prop / T_trans.

### 2. Go-Back-N ARQ

Sender can transmit **N frames** before waiting for an ACK. If a frame is lost, sender **retransmits that frame and ALL subsequent frames**.

**Diagram:**
```
Sender:    F0  F1  F2  F3  F4  F5
              ↓   ↓   ✗   ↓   ↓
Receiver:  F0✓ F1✓     F3✗ F4✗ (out-of-order discarded)
              ACK1 ACK2
                       [TIMEOUT]
Sender:    F2  F3  F4  F5  (re-send all)
```

**Pros:** Better than Stop-and-Wait, simple receiver.
**Cons:** Wastes bandwidth on retransmitting already-received frames.

### 3. Selective Repeat ARQ

Sender can transmit **N frames**; receiver **buffers out-of-order frames**; **only the lost frame is retransmitted**.

**Diagram:**
```
Sender:    F0  F1  F2  F3  F4
              ↓   ↓   ✗   ↓   ↓
Receiver:  F0✓ F1✓     F3 buf F4 buf
              ACK0 ACK1   ACK3 ACK4
                       [TIMEOUT for F2]
Sender:    F2 only
Receiver:  F2 ✓ → delivers F2, F3, F4 in order
```

**Pros:** Bandwidth-efficient — only the lost frame is re-sent.
**Cons:** Receiver requires a buffer; logic is more complex.

### Comparison Table

| Feature | Stop-and-Wait | Go-Back-N | Selective Repeat |
|---------|---------------|-----------|------------------|
| Sender window | 1 | N | N |
| Receiver window | 1 | 1 | N |
| Retransmission | One frame | All from lost onward | Only lost frame |
| Receiver buffer | None | None | N frames |
| ACK type | Individual | Cumulative | Individual |
| Complexity | Low | Medium | High |
| Bandwidth use | Poor | Good | Best |

**Conclusion:** Stop-and-Wait is the simplest but slowest; Go-Back-N is the most popular due to its simple receiver; Selective Repeat is the most efficient but adds complexity. The choice depends on link characteristics and required reliability.

---

## Q3. Explain IPv4 Header Format with all Fields.

**Answer:**

The **IPv4 header** is the leading portion of every IPv4 packet that contains routing and control information. It is **20 to 60 bytes** long (the 40 extra bytes are for optional fields).

**IPv4 Header Diagram:**

```
0       4       8              16                            31
+-------+-------+---------------+-----------------------------+
|Version| IHL   | Type of Service|       Total Length         |
+-------+-------+---------------+-----------------------------+
|       Identification          |Flags|   Fragment Offset     |
+-------------------------------+-----+-----------------------+
|     TTL       |   Protocol    |       Header Checksum       |
+---------------+---------------+-----------------------------+
|                       Source IP Address                      |
+--------------------------------------------------------------+
|                    Destination IP Address                    |
+--------------------------------------------------------------+
|                  Options (if any) + Padding                  |
+--------------------------------------------------------------+
```

**Field-by-Field Explanation:**

| Field | Size | Function |
|-------|------|----------|
| **Version** | 4 bits | IP version — value 4 for IPv4 |
| **IHL (Header Length)** | 4 bits | Length of header in 32-bit words (5 to 15) |
| **Type of Service / DSCP** | 8 bits | QoS / priority of the packet |
| **Total Length** | 16 bits | Total packet size including header (max 65535 bytes) |
| **Identification** | 16 bits | Unique ID used to group fragments of one datagram |
| **Flags** | 3 bits | DF (Don't Fragment), MF (More Fragments), reserved |
| **Fragment Offset** | 13 bits | Position of fragment in original datagram (in 8-byte units) |
| **TTL (Time to Live)** | 8 bits | Maximum hops; decremented by each router; if 0, packet dropped |
| **Protocol** | 8 bits | Upper-layer protocol (TCP=6, UDP=17, ICMP=1) |
| **Header Checksum** | 16 bits | Error check on header only (recomputed each hop) |
| **Source IP Address** | 32 bits | Sender's IPv4 address |
| **Destination IP Address** | 32 bits | Receiver's IPv4 address |
| **Options** | 0–40 bytes | Optional fields (source routing, timestamp, etc.) |
| **Padding** | Variable | Pad header to a multiple of 32 bits |

**Important Protocol Numbers:**
- **1** → ICMP, **6** → TCP, **17** → UDP, **2** → IGMP, **89** → OSPF

**Why these fields matter:**

- **TTL** prevents packets from looping forever (used by traceroute).
- **Fragmentation fields** allow large datagrams to traverse links with smaller MTUs.
- **Protocol field** lets the receiving host hand the payload to the right transport-layer protocol.

**Conclusion:** The IPv4 header carries all the information a router needs to forward a packet — from source/destination addresses and TTL to fragmentation control and the upper-layer protocol identifier.

---

## Q4. Explain Subnetting with Example. What are the Subnets and Hosts for 255.255.255.224 Mask?

**Answer:**

**Subnetting** is the process of dividing a single large network into smaller logical sub-networks (subnets). It improves **address usage, security, broadcast control, and management**.

**Why Subnetting is Needed:**
- Conserves IP addresses
- Reduces broadcast traffic
- Improves security (segments traffic)
- Easier management of departments/branches

**Subnetting Formulas:**

> Number of Subnets = **2ⁿ**
> Hosts per Subnet = **2ʰ – 2** (2 reserved: network + broadcast)

where:
- *n* = number of borrowed bits (from host portion)
- *h* = remaining host bits

**Example: Subnetting with mask 255.255.255.224**

**Step 1 — Convert mask to binary:**
255.255.255.224 = 11111111 . 11111111 . 11111111 . **111**00000

- Default Class C mask = /24, new mask = /27
- Borrowed bits = 27 – 24 = **3**
- Host bits remaining = 32 – 27 = **5**

**Step 2 — Apply formulas:**
- Subnets = 2³ = **8**
- Hosts per subnet = 2⁵ – 2 = **30**
- Total usable hosts = 8 × 30 = **240**

**Step 3 — Subnet ranges (example with 192.168.1.0/24):**

| Subnet | Network | Broadcast | Host Range |
|--------|---------|-----------|------------|
| 1 | 192.168.1.0 | 192.168.1.31 | 1 – 30 |
| 2 | 192.168.1.32 | 192.168.1.63 | 33 – 62 |
| 3 | 192.168.1.64 | 192.168.1.95 | 65 – 94 |
| 4 | 192.168.1.96 | 192.168.1.127 | 97 – 126 |
| 5 | 192.168.1.128 | 192.168.1.159 | 129 – 158 |
| 6 | 192.168.1.160 | 192.168.1.191 | 161 – 190 |
| 7 | 192.168.1.192 | 192.168.1.223 | 193 – 222 |
| 8 | 192.168.1.224 | 192.168.1.255 | 225 – 254 |

**CIDR notation:** 192.168.1.0/27

**VLSM (Variable Length Subnet Mask):** Different subnets can have different sizes — useful when departments have unequal host counts.

**Conclusion:** With mask 255.255.255.224, we get **8 subnets of 30 hosts each**. Subnetting and VLSM together enable efficient and flexible use of IP address space.

---

## Q5. Explain TCP/IP Protocol Suite with all Layers and their Protocols.

**Answer:**

The **TCP/IP Protocol Suite** is a **4-layer** (sometimes called 5-layer) practical model that powers the Internet. It was developed by **DARPA** in the 1970s and predates OSI. Unlike OSI (which is a reference model), TCP/IP is implemented in real systems.

**TCP/IP Layered Stack:**

```
+---------------------------+
|  4. Application Layer     |   ← HTTP, FTP, SMTP, DNS, Telnet
+---------------------------+
|  3. Transport Layer       |   ← TCP, UDP
+---------------------------+
|  2. Internet Layer        |   ← IP, ICMP, ARP, RARP, IGMP
+---------------------------+
|  1. Network Access Layer  |   ← Ethernet, Wi-Fi, PPP, ATM, Frame Relay
+---------------------------+
```

**Layer-by-Layer with Protocols:**

| Layer | OSI Equivalent | Function | Protocols |
|-------|----------------|----------|-----------|
| **Application** | App + Pres + Sess | Provides services to end-users | HTTP, HTTPS, FTP, SMTP, DNS, SSH, Telnet, POP3, IMAP, DHCP |
| **Transport** | Transport | End-to-end delivery, reliability | TCP, UDP |
| **Internet** | Network | Routing, logical addressing | IP, ICMP, ARP, RARP, IGMP |
| **Network Access** | Data Link + Physical | Hardware addressing, signal transmission | Ethernet, Wi-Fi (802.11), PPP, ATM, Frame Relay |

**Comparison with OSI:**

```
TCP/IP                 OSI
+-----------+         +-------------+
|Application|         |Application  |
|           |         +-------------+
|           |   ⇆     |Presentation |
|           |         +-------------+
|           |         |Session      |
+-----------+         +-------------+
| Transport |   ⇆     |Transport    |
+-----------+         +-------------+
| Internet  |   ⇆     |Network      |
+-----------+         +-------------+
| Network   |         |Data Link    |
| Access    |   ⇆     +-------------+
|           |         |Physical     |
+-----------+         +-------------+
```

**Why TCP/IP succeeded over OSI:**
- Practical, working implementation
- Open and free
- Adopted by ARPANET → grew into the Internet
- Simpler 4-layer model

**Conclusion:** The TCP/IP suite is the *de facto* model of the Internet, with each layer providing a clear set of services. Its simplicity and practicality have made it the backbone of all modern data communication.

---

## Q6. Explain Various Multiple Access Protocols (ALOHA, CSMA, CSMA/CD, CSMA/CA).

**Answer:**

In a shared-medium network, multiple stations want to transmit simultaneously. **Multiple Access Protocols** decide *who* can transmit and *when* to avoid or recover from collisions.

**Classification:**

```
                Multiple Access
       /              |               \
  Random          Controlled        Channelization
  Access            Access
   |                  |                 |
  ALOHA            Polling            FDMA
  CSMA            Reservation         TDMA
  CSMA/CD         Token Passing       CDMA
  CSMA/CA
```

### 1. ALOHA

Developed at the **University of Hawaii (1971)**.

**Pure ALOHA:** Any station can transmit anytime. If a collision occurs (no ACK received), wait a random time and retransmit. Vulnerable period = **2 × frame time**. Max efficiency = **18.4%**.

**Slotted ALOHA:** Time is divided into discrete slots; transmission can only begin at slot boundary. Vulnerable period = 1 × frame time. Max efficiency = **36.8%**.

### 2. CSMA (Carrier Sense Multiple Access)

Stations **sense the channel** before transmitting. Variants:

- **1-persistent:** If idle, transmit immediately (high collision risk).
- **Non-persistent:** If busy, wait random time before sensing again.
- **p-persistent:** If idle, transmit with probability p (used in slotted channels).

### 3. CSMA/CD (Collision Detection)

Used in **Ethernet (IEEE 802.3)**. Stations sense, transmit, and **monitor for collisions**. On collision: send jam signal, backoff, retry. Suitable for **wired LANs**.

### 4. CSMA/CA (Collision Avoidance)

Used in **Wi-Fi (IEEE 802.11)**. Wireless cannot detect collisions, so it tries to **avoid** them using:
- **IFS (InterFrame Space)** wait before transmission
- **Random backoff**
- **RTS/CTS handshake** before transmitting data
- **ACK** after receipt

**Comparison:**

| Protocol | Type | Used in | Max Efficiency |
|----------|------|---------|----------------|
| Pure ALOHA | Random | Early radio | 18.4% |
| Slotted ALOHA | Random | – | 36.8% |
| CSMA | Random | – | High (variable) |
| CSMA/CD | Random | Ethernet | High |
| CSMA/CA | Random | Wi-Fi | Medium (overhead) |

**Conclusion:** Multiple access protocols evolved from simple ALOHA to sophisticated CSMA/CD and CSMA/CA, each tailored to its physical medium. They form the basis of modern LAN and WLAN technologies.

---

## Q7. Explain Cryptography in detail with RSA Example.

**Answer:**

**Cryptography** is the science and practice of **secure communication** over insecure channels. It transforms plaintext into ciphertext (encryption) such that only authorized parties can recover the plaintext (decryption).

**Goals (CIA + N):**
1. **Confidentiality** – data hidden from unauthorized access.
2. **Integrity** – data not altered in transit.
3. **Authentication** – verify identity of sender.
4. **Non-repudiation** – sender cannot deny.

### Types of Cryptography

| Type | Key | Algorithms |
|------|-----|------------|
| **Symmetric** | Same key | DES, 3DES, AES, Blowfish |
| **Asymmetric** | Public + Private | RSA, ECC, DSA |

### RSA Algorithm

RSA was invented by **Rivest, Shamir, and Adleman** in 1977. It is based on the difficulty of factoring large prime numbers.

**Step 1 — Key Generation:**

1. Choose two large prime numbers *p* and *q*.
2. Compute *n* = *p* × *q*.
3. Compute Euler's totient: *φ(n)* = (p–1)(q–1).
4. Choose *e* such that 1 < *e* < φ(n) and gcd(e, φ(n)) = 1.
5. Compute *d* such that *e × d* ≡ 1 (mod φ(n)).

> **Public key:** (e, n)  |  **Private key:** (d, n)

**Step 2 — Encryption:** C = Mᵉ mod n
**Step 3 — Decryption:** M = Cᵈ mod n

**Numerical Example: Send the character 'F' using N = 119, E = 5, D = 77.**

**Step 1 — Convert character:**
F = 6 (alphabet position; A=1, B=2, …, F=6)

**Step 2 — Encrypt:** C = 6⁵ mod 119
- 6² = 36
- 6⁴ = 36² = 1296 mod 119 = 1296 – 1190 = **106**
- 6⁵ = 106 × 6 = 636 mod 119 = 636 – 595 = **41**

**Cipher Text: C = 41**

**Step 3 — Decrypt (verification):** M = 41⁷⁷ mod 119 = **6** ✓ (recovered F)

### Digital Signature using RSA

To sign a message, sender encrypts the **hash** of the message using their **private key**. Receiver decrypts using sender's **public key** to verify.

**Conclusion:** Cryptography secures modern internet communication. RSA is one of the most important asymmetric algorithms, used in TLS/SSL, SSH, digital signatures, and email security (S/MIME, PGP).

---

## Q8. Explain Routing Algorithms (Distance Vector and Link State).

**Answer:**

**Routing** is the process of selecting the best path for a packet from source to destination. Routing algorithms run on routers and update routing tables.

There are two main categories of dynamic routing algorithms: **Distance Vector** and **Link State**.

### 1. Distance Vector Routing (RIP)

Based on the **Bellman-Ford algorithm**.

**Working:**
- Each router maintains a vector of distances to all destinations.
- Periodically shares its vector with **direct neighbors only**.
- Updates its own vector if a shorter path is discovered:
  > *D(x, y) = min over neighbors n of [c(x, n) + D(n, y)]*

**Drawbacks:**
- Slow convergence
- **Count-to-infinity problem** when a link fails (looping updates).
- Solutions: split horizon, poison reverse, hold-down timers.

**Example Update Step:**

Router A's table updates if neighbor B has a shorter route to destination Y.

### 2. Link State Routing (OSPF)

Based on **Dijkstra's Shortest Path First (SPF)** algorithm.

**Working:**
1. Each router discovers its neighbors and link costs (using Hello packets).
2. Builds a **Link State Packet (LSP)** containing this info.
3. **Floods LSPs** to all routers in the network.
4. Each router builds a **complete topology map**.
5. Runs **Dijkstra's algorithm** to compute shortest path tree to all destinations.

**Advantages:**
- Faster convergence
- No count-to-infinity
- Scalable using areas (hierarchical OSPF)

### Comparison

| Feature | Distance Vector (RIP) | Link State (OSPF) |
|---------|----------------------|--------------------|
| Algorithm | Bellman-Ford | Dijkstra |
| Information shared | Distance vector | Full topology |
| Sent to | Neighbors only | All routers |
| Frequency | Periodic | On change |
| Convergence | Slow | Fast |
| Scalability | Limited | High |
| Count-to-infinity | Yes | No |
| Memory/CPU | Low | Higher |
| Examples | RIP, IGRP | OSPF, IS-IS |

**Conclusion:** Distance Vector is simple but slow and prone to loops; Link State is more complex but converges quickly and scales better. Modern large networks (ISPs, enterprise) use OSPF or IS-IS, while small networks may still use RIP.

---

## Q9. Explain Application Layer Protocols (HTTP, FTP, SMTP, DNS).

**Answer:**

The **Application Layer** is the topmost layer of both OSI and TCP/IP models. It provides services directly to end-user applications. Below are four of the most important application-layer protocols.

### Quick Comparison Table

| Protocol | Purpose | Transport | Port | Type |
|----------|---------|-----------|------|------|
| **HTTP** | Web pages | TCP | 80 / 443 | Pull |
| **FTP** | File transfer | TCP | 20, 21 | – |
| **SMTP** | Email send | TCP | 25 / 587 | Push |
| **DNS** | Name → IP | UDP | 53 | Query |

### 1. HTTP (HyperText Transfer Protocol)

- Stateless, request-response protocol over TCP port **80** (HTTPS = 443).
- Used by web browsers to fetch web pages.
- **Methods:** GET, POST, PUT, DELETE, HEAD, OPTIONS.
- **Status codes:** 1xx (info), 2xx (success), 3xx (redirect), 4xx (client error), 5xx (server error).
- Each request is independent; state is maintained externally via cookies.

### 2. FTP (File Transfer Protocol)

- Used for transferring files between hosts.
- Uses **two TCP connections:** **port 21** (control commands) and **port 20** (data transfer).
- **Out-of-band control** — commands are sent on a separate channel from data.
- Supports authentication (USER, PASS).
- Modes: ASCII / Binary; Active / Passive.
- Commands: USER, PASS, LIST, RETR, STOR, QUIT.

### 3. SMTP (Simple Mail Transfer Protocol)

- Used to **send** email between mail servers (MTAs).
- Push protocol over TCP port **25** (587 for submission).
- Sequence of commands: HELO/EHLO, MAIL FROM, RCPT TO, DATA, QUIT.
- Receiving mail uses POP3 (110) or IMAP (143).

### 4. DNS (Domain Name System)

- Translates domain names → IP addresses.
- Hierarchical, distributed database.
- Uses **UDP port 53** (TCP for zone transfers).
- Hierarchy: Root → TLD → Authoritative.
- Common record types: A, AAAA, MX, CNAME, NS, PTR.

**Conclusion:** These four protocols handle the bulk of internet activities — browsing, file transfer, email, and name resolution. Together they form the user-visible face of the internet.

---

## Q10. Explain Congestion Control Mechanisms (TCP Slow Start, Congestion Avoidance, Leaky and Token Bucket).

**Answer:**

**Congestion** occurs when the load on a network exceeds its capacity, causing **packet loss, delays, and reduced throughput**. **Congestion control** algorithms regulate traffic to prevent or recover from congestion.

There are two broad approaches: **closed-loop (TCP-based, end-to-end)** and **open-loop (router-based, traffic shaping)**.

### A. TCP Closed-Loop Algorithms

**1. Slow Start (Exponential Growth)**
- Start with cwnd = 1 MSS.
- For every ACK received, cwnd *doubles* per RTT.
- Continues until cwnd reaches **ssthresh**.
- Goal: probe network capacity quickly.

**2. Congestion Avoidance (Linear Growth)**
- After cwnd ≥ ssthresh, increase cwnd by 1 MSS per RTT.
- Continues until packet loss is detected.

**3. Fast Retransmit**
- If 3 duplicate ACKs arrive, sender retransmits the lost segment immediately (without waiting for timeout).

**4. Fast Recovery**
- After fast retransmit: ssthresh = cwnd/2; cwnd = ssthresh.
- Skip slow start; resume from congestion avoidance.

**Diagram — TCP Window Behavior:**

```
cwnd
 |                                (timeout: cwnd → 1)
 |                  /\           /
 |              ___/  \  /------/   (linear: congestion avoidance)
 |             /       \/
 |            / ssthresh
 |           /     /
 |          /     /
 |         /(exp)/
 |        / Slow/
 |       / Start
 |      /
 |     /
 +----+----------+--------------+----> Time (RTT)
                (loss)
```

### B. Open-Loop Traffic Shaping

**1. Leaky Bucket**
- Buffer with a constant output rate.
- Bursty input → smooth output.
- Overflow → drop packets.
- Strict — does not allow bursts.

**2. Token Bucket**
- Tokens generated at a constant rate, stored in a bucket of size B.
- Each packet consumes one token.
- If tokens are available → send; else wait.
- Allows **bursts up to B tokens** as long as average rate is maintained.

**Comparison:**

| Feature | Leaky Bucket | Token Bucket |
|---------|--------------|--------------|
| Output rate | Constant | Variable (bursts allowed) |
| Stores | Packets | Tokens |
| Burst | Not allowed | Allowed |
| Use | Strict shaping | Flexible shaping |

**Conclusion:** TCP's combination of slow start, congestion avoidance, fast retransmit, and fast recovery prevents Internet meltdowns. Open-loop algorithms like Leaky/Token Bucket complement these by shaping traffic at the network's edge to maintain QoS.

---

# 🟡 TOP 15 MOST LIKELY 2-MARK / SHORT ANSWER QUESTIONS

---

### Q1. What is a Protocol?

A **protocol** is a set of rules and conventions that govern data communication between two or more devices. Every protocol has three key elements: **syntax** (data format), **semantics** (meaning of each field), and **timing** (when to send). Examples: TCP, HTTP, IP.

---

### Q2. Define Bandwidth.

**Bandwidth** has two meanings:
1. The **range of frequencies** a transmission medium can carry, measured in **Hertz (Hz)**.
2. The **maximum data transfer rate** of a digital channel, measured in **bits per second (bps)**.

For example, a typical home broadband line has a bandwidth of 100 Mbps.

---

### Q3. What is the difference between Hub and Switch?

A **Hub** operates at the **Physical Layer (L1)** and **broadcasts** any incoming signal to all its ports — wasting bandwidth. A **Switch** operates at the **Data Link Layer (L2)**, learns MAC addresses, and **forwards frames only to the destination port** — improving efficiency and reducing collisions.

---

### Q4. What is a MAC Address?

A **MAC (Media Access Control) address** is a **48-bit physical address** burned into the Network Interface Card (NIC). It uniquely identifies a device on a local network and is used for **hop-by-hop frame delivery** at the Data Link Layer. Format: six pairs of hexadecimal digits, e.g., `00:1A:2B:3C:4D:5E`.

---

### Q5. Define Throughput vs Bandwidth.

**Bandwidth** is the *maximum theoretical capacity* of a channel (e.g., 1 Gbps). **Throughput** is the *actual amount of data delivered per second* (e.g., 800 Mbps). Throughput is always **less than or equal to** bandwidth due to overhead, errors, and congestion.

---

### Q6. What is a Port Number?

A **port number** is a **16-bit numerical identifier** (0–65535) used at the transport layer to distinguish among multiple processes/services running on the same host. Well-known ports range from 0 to 1023, e.g., **HTTP = 80, FTP = 21, SMTP = 25, DNS = 53**.

---

### Q7. What is Subnet Mask?

A **subnet mask** is a **32-bit number** that divides an IP address into **network** and **host** portions. Bits set to 1 represent the network part; bits set to 0 represent the host part. Example: **255.255.255.0** (or /24) means the first 24 bits are the network part.

---

### Q8. What is Encapsulation?

**Encapsulation** is the process by which each layer of the OSI / TCP/IP stack **adds its own header (and sometimes a trailer)** to data received from the upper layer before passing it down. As data moves down the stack, it grows in size — Application Data → Segment → Packet → Frame → Bits.

---

### Q9. Define Hamming Distance.

**Hamming distance** is the number of bit positions in which two equal-length binary strings differ. It is found by XORing the two strings and counting the number of 1's. Example: Hamming distance between `10101` and `10000` is **2**, since they differ in bits 3 and 5.

---

### Q10. What is ARP?

**ARP (Address Resolution Protocol)** is a network-layer protocol used to **map an IP address to its corresponding MAC address** within a local network. The host **broadcasts** an ARP request asking "Who has IP X?" and the host with that IP **unicasts** back its MAC address.

---

### Q11. What is DNS used for?

**DNS (Domain Name System)** is used to translate **human-friendly domain names** (like google.com) to **numeric IP addresses** (like 142.250.190.46). It runs over **UDP port 53** and uses a hierarchical, distributed database (Root → TLD → Authoritative).

---

### Q12. What are the two types of Transmission Modes?

There are **three** transmission modes:
1. **Simplex** — communication in one direction only (e.g., keyboard).
2. **Half-Duplex** — both directions, but not simultaneously (e.g., walkie-talkie).
3. **Full-Duplex** — both directions simultaneously (e.g., telephone, modern Ethernet).

---

### Q13. What is a Firewall?

A **Firewall** is a hardware/software security system that **monitors and filters** network traffic based on predefined rules, separating trusted (internal) networks from untrusted (external) networks. Types: **packet filter, stateful inspection, application/proxy gateway**, and **next-generation firewall (NGFW)**.

---

### Q14. What is Piggybacking?

**Piggybacking** is a technique where the **acknowledgement (ACK) is attached to an outgoing data frame** instead of being sent as a separate frame. This reduces the number of small packets in the network and improves bandwidth efficiency. It's used in protocols like TCP and HDLC.

---

### Q15. What is Multiplexing?

**Multiplexing** is the technique of combining **multiple signals onto a single transmission medium** to improve bandwidth utilization. Major types are:
- **FDM** — Frequency Division Multiplexing (radio/TV)
- **TDM** — Time Division Multiplexing (digital telephone)
- **WDM** — Wavelength Division Multiplexing (optical fiber)
- **CDM** — Code Division Multiplexing (3G mobile)

---

# 🟢 TOP 5 NUMERICAL PROBLEMS EXPECTED

---

## Numerical 1 — Propagation and Transmission Time

**Problem:** Calculate the propagation time and transmission time for a 2.5 KB message over a 1 Gbps link if distance = 12,000 km and speed = 2.4 × 10⁸ m/s.

**Solution:**

**Step 1 — Convert units:**
- Message = 2.5 × 1000 × 8 = **20,000 bits**
- Distance = 12,000 km = 1.2 × 10⁷ m
- Bandwidth = 10⁹ bps
- Speed = 2.4 × 10⁸ m/s

**Step 2 — Propagation Time:**
T_prop = Distance / Speed = (1.2 × 10⁷) / (2.4 × 10⁸) = **0.05 s = 50 ms**

**Step 3 — Transmission Time:**
T_trans = Message / Bandwidth = 20,000 / 10⁹ = 2 × 10⁻⁵ s = **20 μs**

**Conclusion:** T_prop (50 ms) >> T_trans (20 μs). For short messages over long distances, propagation delay dominates.

---

## Numerical 2 — Channel Capacity (Nyquist & Shannon)

**Problem:** Find the channel capacity for a noiseless channel with B = 4 kHz and L = 4 signal levels.

**Solution:**

Use **Nyquist's theorem** for noiseless channel:
> C = 2 × B × log₂(L)

Substituting:
- C = 2 × 4000 × log₂(4)
- C = 8000 × 2
- C = **16,000 bps = 16 kbps**

For noisy channel, use **Shannon's theorem**:
> C = B × log₂(1 + SNR)

**Conclusion:** Channel capacity = **16 kbps**. Choose Nyquist for noiseless, Shannon for noisy channels.

---

## Numerical 3 — CRC Computation

**Problem:** Generate CRC for the data 10011101 using generator polynomial x³ + 1.

**Solution:**

**Step 1 — Identify generator:** x³ + 1 = **1001** (4 bits, degree 3)

**Step 2 — Append 3 zeros to data:**
Augmented data: **10011101000**

**Step 3 — Perform XOR division:**

```
  10011101000
⊕ 10010000000   (XOR at position 0)
  -----------
  00001101000
⊕ 00001001000   (XOR at position 4)
  -----------
  00000100000
⊕ 00000100100   (XOR at position 5)
  -----------
  00000000100   ← Remainder = 100
```

**Step 4 — Transmitted bit string:**
Data + CRC = 10011101 + 100 = **10011101100**

**Step 5 — Verification at receiver:**
Receiver divides 10011101100 by 1001 → remainder = 0 → no error.

**Conclusion:** CRC bits = **100**, transmitted string = **10011101100**.

---

## Numerical 4 — Subnetting

**Problem:** Calculate the number of subnets and hosts when subnet mask = 255.255.255.224.

**Solution:**

**Step 1 — Convert to binary:**
255.255.255.224 = 11111111 . 11111111 . 11111111 . **111**00000

- Default Class C mask = /24
- New mask = /27
- Borrowed bits = 3
- Host bits = 5

**Step 2 — Apply formulas:**
- Number of subnets = 2³ = **8**
- Hosts per subnet = 2⁵ – 2 = **30**

**Step 3 — For 255.255.240.0 (alternative):**
Host bits = 12 → max hosts = 2¹² – 2 = **4094**

**Conclusion:** Mask 255.255.255.224 yields **8 subnets × 30 hosts each = 240 usable hosts**.

---

## Numerical 5 — RSA Encryption

**Problem:** Encrypt the character F using N = 119, E = 5, D = 77.

**Solution:**

**Step 1 — Convert character:**
F = 6 (alphabet position)

**Step 2 — Encrypt:**
C = M^E mod N = 6⁵ mod 119

Calculation:
- 6² = 36
- 6⁴ = 36² = 1296 mod 119 = 1296 – (10 × 119) = 1296 – 1190 = **106**
- 6⁵ = 106 × 6 = 636 mod 119 = 636 – (5 × 119) = 636 – 595 = **41**

**Cipher Text C = 41**

**Step 3 — Decrypt verification:**
M = C^D mod N = 41⁷⁷ mod 119 → recovers **6** (= F) ✓

**Conclusion:** Cipher of F = **41**.

---

# ⭐ TOP 10 REPEATED / CLASSIC EXAM QUESTIONS

These questions are asked **almost every year** — master them for guaranteed marks.

---

### Classic Q1. Explain the OSI Reference Model.
*(See detailed answer above in 10-mark Q1.)*
**Strategy:** Always begin by drawing the 7-layer stack diagram. Then tabulate functions and devices.

---

### Classic Q2. Compare OSI and TCP/IP Models.
*(See detailed answer above in 5-mark Q1.)*
**Strategy:** Show side-by-side stack mapping + at least 6 differences in a table.

---

### Classic Q3. Explain CSMA/CD vs CSMA/CA with Flowcharts.
*(See detailed answers above in 5-mark Q2 and Comparison Table.)*
**Strategy:** Two flowcharts + comparison table = full marks.

---

### Classic Q4. Compare TCP and UDP.
*(See detailed answer above in 5-mark Q3.)*
**Strategy:** Header diagrams + 8-row comparison + named applications.

---

### Classic Q5. Explain Three-Way Handshake.
*(See detailed answer above in 5-mark Q8.)*
**Strategy:** Always draw the 3-arrow timeline with seq/ack numbers, then state the problem solved.

---

### Classic Q6. Construct Hamming Code for 4-bit Data.
*(See detailed answer above in 5-mark Q5.)*
**Strategy:** Position table → parity bit calculation → final codeword → syndrome-based correction.

---

### Classic Q7. Explain CRC with Example.
*(See Numerical 3 above.)*
**Strategy:** Show step-by-step XOR division clearly. End by verifying that transmitted string gives 0 remainder.

---

### Classic Q8. Explain DNS with Hierarchy.
*(See detailed answer above in 5-mark Q10.)*
**Strategy:** Inverted tree diagram + resolution flow + record types.

---

### Classic Q9. Compare FTP and TFTP.

**Answer:**

**FTP (File Transfer Protocol)** is a robust, full-featured protocol for transferring files over **TCP**, while **TFTP (Trivial File Transfer Protocol)** is a simple, lightweight version over **UDP**.

| Feature | FTP | TFTP |
|---------|-----|------|
| Full form | File Transfer Protocol | Trivial File Transfer Protocol |
| Transport | TCP | UDP |
| Port | 20 (data), 21 (control) | 69 |
| Connections | Two | One |
| Reliability | Reliable | Limited (UDP) |
| Authentication | Yes (USER, PASS) | No |
| Speed | Slower | Faster |
| Complexity | Complex (many commands) | Simple (5 messages) |
| Resume support | Yes | No |
| Use case | General file transfer | Bootstrap, firmware upload |

**Conclusion:** FTP is feature-rich but heavyweight; TFTP is minimalist and fast, ideal for embedded devices.

---

### Classic Q10. Explain RSA with Numerical Example.
*(See detailed answer above in 10-mark Q7 and Numerical 5.)*
**Strategy:** State algorithm steps → show modular exponentiation → conclude with cipher value.

---

# ✍️ EXAM WRITING TIPS (Read before going to exam)

1. **Always start with a definition** — examiner sees you understand the topic.
2. **Draw at least one diagram per long answer** — visualization gets marks.
3. **Use tables for comparisons** — much cleaner than paragraphs.
4. **Show formulas first**, then plug in values, then compute step-by-step.
5. **Highlight final answers** — underline or box them.
6. **Number your steps** — Step 1, Step 2, …
7. **End every long answer with a conclusion** — even one sentence helps.
8. **Don't leave anything blank** — partial credit is better than zero.
9. **Manage time:** 2-mark = 3 min, 5-mark = 12 min, 10-mark = 22 min.
10. **Re-read your paper** for at least 5 minutes at the end.

---

# 🎓 ALL THE BEST!

> Read this file once tonight, glance through diagrams and tables tomorrow morning, and walk into your exam with confidence. You've prepared well — now just write what you know clearly. 🚀
