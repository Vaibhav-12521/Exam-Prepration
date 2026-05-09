# DCCN — COMPLETE EXAM PREPARATION (Problem Set + Previous Year Paper)
**Course:** BCA / B.Sc(IT) | **Subject Code:** US6001 / UCS6001 | **Sem VI**

---

# PART A — PROBLEM SET 1-5 (EXPLAINED & SOLVED)

---

## 🟦 PROBLEM SET I — UNIT 1: INTRODUCTION TO NETWORKS

### Q1. Consequences of Connection Failure (5 devices in each topology)
**What it tests:** Understanding fault tolerance of network topologies.

**a) Mesh Topology**
- Total dedicated links = n(n-1)/2 = **10 links** (each device connected to all others)
- If one link fails → traffic reroutes through alternate paths
- **Conclusion: No service disruption** — high reliability

**b) Star Topology** (5 devices + central hub)
- If a device-to-hub link fails → only that one device disconnects
- If the **central hub fails → entire network goes down** (single point of failure)

**c) Bus Topology**
- All devices share a single backbone cable
- If a tap (drop line) fails → only that device disconnects
- If backbone breaks → network splits into two non-functional halves

**d) Ring Topology**
- Each device connected to exactly two neighbors
- One break in unidirectional ring → **entire network fails**
- Dual-ring (e.g., FDDI) provides self-healing capability

---

### Q2. Propagation & Transmission Time
**What it tests:** Difference between propagation delay (signal travel time) and transmission delay (time to push bits onto wire).

**Given:** Message = 2.5 KB, Bandwidth = 1 Gbps, Distance = 12,000 km, Speed = 2.4 × 10⁸ m/s

**Step 1 — Convert units:**
- Message size = 2.5 × 1000 × 8 = **20,000 bits**
- Distance = 12,000 km = 1.2 × 10⁷ m

**Step 2 — Propagation time:**
T_prop = Distance / Speed = (1.2 × 10⁷) / (2.4 × 10⁸) = **0.05 s = 50 ms**

**Step 3 — Transmission time:**
T_trans = Size / Bandwidth = 20,000 / 10⁹ = **20 μs**

**Insight:** For short messages over long distances, propagation delay dominates.

---

### Q3. Channel Capacity (B=4 kHz, L=4, Noiseless)
**What it tests:** Nyquist's theorem for noiseless channel.

**Formula:** C = 2 × B × log₂(L)
**Calculation:** C = 2 × 4000 × log₂(4) = 8000 × 2 = **16,000 bps = 16 kbps**

---

### Q4. Twisted Pair vs Coaxial vs Optical Fiber
**What it tests:** Knowledge of guided transmission media.

| Feature | Twisted Pair | Coaxial Cable | Optical Fiber |
|---------|--------------|---------------|---------------|
| **Cost** | Cheapest | Moderate | Most expensive |
| **Bandwidth** | Up to 100 Mbps | Up to 1 Gbps | THz (very high) |
| **Distance** | ~100 m | ~500 m | 100+ km |
| **EMI Resistance** | Susceptible | Moderate | Immune |
| **Signal Type** | Electrical | Electrical | Light |
| **Use** | LAN, telephone | Cable TV | Internet backbone |

---

### Q5. Packet/Frame at Each Hop (A → R1 → D)
**What it tests:** Difference between logical (IP) and physical (MAC) addresses across hops.

**Setup:** A(40) — LAN1 — R1(B/42, C/82) — LAN2 — D(80)

**HOP 1 (A → R1 across LAN1):**
- Network layer (Packet): SrcIP = A, DstIP = D
- Data link (Frame): SrcMAC = 40, DstMAC = 42

**HOP 2 (R1 → D across LAN2):**
- Network layer (Packet): SrcIP = A, DstIP = D *(unchanged)*
- Data link (Frame): SrcMAC = 82, DstMAC = 80

**Key insight:** IP addresses remain constant end-to-end; MAC addresses change at every hop.

---

### Q6. Presentation Layer in Internet Model
**What it tests:** Differences between OSI and TCP/IP layer mappings.

**Answer:** In the **TCP/IP model**, there is no separate Presentation Layer. The duties of **translation, encryption, and compression** are handled by the **Application Layer**.

**Reason:** TCP/IP collapses OSI's Application + Presentation + Session into one Application Layer. Programs use protocols like SSL/TLS (encryption), MIME (translation), and gzip (compression).

---

### Q7. Corrupted Logical Destination Address
**What it tests:** Understanding of error handling at network layer.

**What happens:**
1. Routers use the corrupted IP for routing table lookup
2. If no matching route → packet dropped, ICMP Destination Unreachable sent to source
3. If accidentally valid → packet reaches wrong host (likely dropped silently)
4. If wandering with no destination → TTL expires → ICMP Time Exceeded

**Source notification:** Through **ICMP error messages** sent back to source IP.

---

### Q8. Two Computers + Ethernet Hub at Home
**What it tests:** Classification of networks by geographic scope.

**Answer:** This is a **LAN (Local Area Network)**.

**Reasons:**
- Limited to a single home (small geographic area)
- Owned/operated by one user
- Uses Ethernet — a LAN technology
- LAN < 1 km; MAN = city; WAN = country/global

---

### Q9. Two Acknowledgement Strategies
**What it tests:** Trade-offs in protocol design.

**Strategy 1 — Per-packet ACK (no whole-file ACK):**
- ✅ Quick error detection, retransmit only lost packet
- ❌ ACK overhead, last ACK may be lost (sender thinks complete)

**Strategy 2 — Single whole-file ACK:**
- ✅ Less ACK overhead, simpler
- ❌ One bit error → retransmit entire file

**Best practice:** Combine both (TCP + application layer).

---

### Q10. Image Transmission Time (1920×1280, 5 bytes/pixel, 56 kbps)
**What it tests:** Real-world calculation of transmission time.

**Step 1 — Image size:**
Total pixels = 1920 × 1280 = 2,457,600
Total bytes = 2,457,600 × 5 = **12,288,000 bytes**
Total bits = 12,288,000 × 8 = **98,304,000 bits**

**Step 2 — Time:**
Time = 98,304,000 / 56,000 = **1755.4 sec ≈ 29 min 15 sec**

---

## 🟩 PROBLEM SET II — UNIT 2: PHYSICAL & DATA LINK LAYER

### Q1. Services of Data Link Layer
**What it tests:** Core functions of layer 2.

1. **Framing** — divides bit stream into frames
2. **Physical (MAC) addressing** — adds source/destination MAC
3. **Flow control** — prevents overwhelming slow receiver
4. **Error control** — CRC, ARQ for detection/correction
5. **Access control** — manages shared medium (CSMA, polling)
6. **Reliable delivery** — ACK and retransmission

---

### Q2. Hamming Distance Calculations
**What it tests:** Understanding of bit-level differences.

**Definition:** Number of bit positions where two strings differ. Use XOR + count 1's.

| Code Words | Comparison | Hamming Distance |
|-----------|------------|------------------|
| d(10000, 00000) | Position 1 differs | **1** |
| d(10101, 10000) | Positions 3,5 differ | **2** |
| d(11111, 11111) | None differ | **0** |
| d(000, 000) | None differ | **0** |

---

### Q3. Even Parity Bit Calculation
**What it tests:** Single-bit error detection technique.

**Rule:** Even parity bit = 0 if number of 1's is already even; 1 if odd.

| Data | Count of 1's | Parity Bit |
|------|--------------|------------|
| 1001011 | 4 (even) | **0** |
| 0001100 | 2 (even) | **0** |
| 1000000 | 1 (odd) | **1** |
| 1110111 | 6 (even) | **0** |

---

### Q4. 7-bit Hamming Code for 1011 + Correction of 1011011
**What it tests:** Construction and correction of Hamming code.

**Position layout:** P1 P2 D1 P4 D2 D3 D4 → 1 2 3 4 5 6 7
**Data 1011:** D1=1, D2=0, D3=1, D4=1

**Parity bit calculations (even parity):**
- **P1** (positions 1,3,5,7) → P1 ⊕ 1 ⊕ 0 ⊕ 1 = 0 → **P1 = 0**
- **P2** (positions 2,3,6,7) → P2 ⊕ 1 ⊕ 1 ⊕ 1 = 0 → **P2 = 1**
- **P4** (positions 4,5,6,7) → P4 ⊕ 0 ⊕ 1 ⊕ 1 = 0 → **P4 = 0**

**Hamming codeword: 0110011**

**Now correct the received codeword 1011011:**

| Position | 1 | 2 | 3 | 4 | 5 | 6 | 7 |
|---------|---|---|---|---|---|---|---|
| Bit | 1 | 0 | 1 | 1 | 0 | 1 | 1 |

- **C1** = 1⊕1⊕0⊕1 = **1**
- **C2** = 0⊕1⊕1⊕1 = **1**
- **C4** = 1⊕0⊕1⊕1 = **1**

**Syndrome = C4C2C1 = 111 = 7** → Error at bit 7 → Flip bit 7 → **Corrected: 1011010**

---

### Q5. Packet Switching vs Circuit Switching
**What it tests:** Switching paradigms and delay characteristics.

| Feature | Circuit Switching | Packet Switching |
|---------|-------------------|------------------|
| **Path** | Dedicated end-to-end | No dedicated path |
| **Phases** | Setup, Transfer, Teardown | Just Transfer |
| **Bandwidth** | Reserved | Shared |
| **Delay** | High setup, then minimal | Variable per packet |
| **Reliability** | More reliable | Less reliable |
| **Example** | Telephone | Internet |

**Delay analysis:**
- **Circuit:** Total = setup + transmission + propagation
- **Packet:** Total = N × (queuing + processing + transmission + propagation)

---

### Q6. CRC for 10011101 with Generator x³+1 (= 1001)
**What it tests:** Error detection using polynomial division.

**Step 1 — Append 3 zeros:** 10011101000

**Step 2 — XOR division:**
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

**Step 3 — Transmitted: 10011101 + 100 = 10011101100**

**Step 4 — If 3rd bit inverted: 10111101100**

Receiver divides by 1001:
```
  10111101100
⊕ 10010000000
  -----------
  00101101100
⊕ 00100100000  (at position 2)
  -----------
  00001001100
⊕ 00001001000  (at position 4)
  -----------
  00000000100   ← Remainder = 100 ≠ 0
```

**Conclusion:** Non-zero remainder ⇒ **error detected** ✓

---

### Q7. CSMA/CD vs CSMA/CA
**What it tests:** Wired vs wireless medium access protocols.

| Feature | CSMA/CD | CSMA/CA |
|---------|---------|---------|
| **Used in** | Wired (Ethernet 802.3) | Wireless (Wi-Fi 802.11) |
| **Approach** | Detect collision after | Avoid collision before |
| **Mechanism** | Listen → Send → Detect → Backoff | Listen → IFS → Backoff → RTS/CTS → Send → ACK |
| **Why different** | Wired can detect collisions | Wireless cannot (hidden node) |

**CSMA/CD Flow:** Sense → if idle send → if collision detected, send jam → exponential backoff → retry
**CSMA/CA Flow:** Sense → wait IFS → random backoff → RTS → wait CTS → send data → wait ACK

---

### Q8. Checksum (32-bit data: 10011001 11100010 00100100 10000100)
**What it tests:** Internet checksum (1's complement addition).

**Segments:** A=10011001, B=11100010, C=00100100, D=10000100

**Sender side:**
- A + B = 10011001 + 11100010 = 1 01111011 → wrap-around → 01111100 (124)
- (A+B) + C = 01111100 + 00100100 = 10100000 (160)
- (A+B+C) + D = 10100000 + 10000100 = 1 00100100 → wrap → 00100101 (37)

**Sum = 00100101 → Checksum = 1's complement = 11011010**

**Receiver side:** Adds all segments + checksum = **11111111** → 1's complement = 00000000 → No error ✓

---

### Q9. Go-Back-N ARQ Working
**What it tests:** Sliding window protocol for reliable delivery.

**Rules:**
- Sender window = N, Receiver window = 1
- Cumulative ACK
- Loss/timeout → retransmit lost frame and ALL after it
- Receiver discards out-of-order frames

**Diagram:**
```
Sender:    F0  F1  F2  F3  F4  F5
              ↓   ↓   X   ↓   ↓
Receiver:  F0✓ F1✓     F3✗ F4✗ (discarded)
              ACK1 ACK2
                       TIMEOUT
Sender:    F2  F3  F4  F5  (all retransmitted)
```

**Drawback:** Wastes bandwidth retransmitting already-received frames.

---

### Q10. Framing & its Methods
**What it tests:** Techniques to delimit frames at data link layer.

**Definition:** Process of dividing bit stream into frames with start/end markers.

**Methods:**
1. **Character (Byte) Count** — first byte = frame length
2. **Flag Bytes with Byte Stuffing** — escape character before flag in data
3. **Flag Bits with Bit Stuffing** — insert 0 after every 5 consecutive 1's
4. **Physical Layer Coding Violations** — illegal bit patterns mark boundaries

---

## 🟨 PROBLEM SET III — UNIT 3: LLC / MAC

### Q1. Why Go-Back-N is more popular than Stop-and-Wait
**Answer:** Go-Back-N pipelines transmission while Stop-and-Wait waits for each ACK individually, wasting bandwidth on long links. Modern high-speed networks have high bandwidth-delay product, where Stop-and-Wait achieves <5% utilization. Go-Back-N is also simpler than Selective Repeat (no buffer at receiver).

**Efficiency:** η_GBN = N / (1 + 2a) vs η_SW = 1 / (1 + 2a)

---

### Q2. Pure ALOHA vs Slotted ALOHA at Low Load
**Answer:** **Pure ALOHA has less delay at low load.**

**Reason:** In slotted ALOHA, even if channel is idle, station must wait for slot boundary. Pure ALOHA can transmit immediately. At low load, collisions are rare in both, so pure ALOHA's immediate-send wins.

**Trade-off:** At high load, slotted ALOHA performs better (36.8% vs 18.4% efficiency).

---

### Q3. Unicast vs Multicast vs Broadcast
| Type | Meaning | IP Range |
|------|---------|----------|
| **Unicast** | One-to-one | Class A/B/C |
| **Multicast** | One-to-group | 224.0.0.0 – 239.255.255.255 (Class D) |
| **Broadcast** | One-to-all | 255.255.255.255 (limited) |

---

### Q4. Networks and Hosts in IP Address Classes
| Class | Range | # Networks | # Hosts/Network |
|-------|-------|------------|-----------------|
| A | 0–127 | 128 (126 usable) | 16,777,214 |
| B | 128–191 | 16,384 | 65,534 |
| C | 192–223 | 2,097,152 | 254 |
| D | 224–239 | Multicast | – |
| E | 240–255 | Reserved | – |

---

### Q5. ICMP and its Types
**ICMP = Internet Control Message Protocol** — error reporting and diagnostic protocol at network layer.

**Error-reporting messages:**
- Destination Unreachable
- Source Quench (deprecated)
- Time Exceeded
- Parameter Problem
- Redirect

**Query messages:**
- Echo Request/Reply (ping)
- Timestamp Request/Reply
- Address Mask Request/Reply
- Router Solicitation/Advertisement

---

### Q6. Subnets and Hosts for 255.255.255.224
**Mask:** 11111111.11111111.11111111.**111**00000

- Subnet bits = 3 → Subnets = 2³ = **8**
- Host bits = 5 → Hosts/subnet = 2⁵ – 2 = **30**

---

### Q7. CSMA/CD vs CSMA/CA
*(Same as Unit 2 Q7 — refer above.)*

---

### Q8. Maximum Hosts for 255.255.240.0 + CIDR
**Mask:** 11111111.11111111.**1111**0000.00000000
- Host bits = 12 → Maximum hosts = 2¹² – 2 = **4094**

**CIDR (Classless Inter-Domain Routing):**
- Replaces classful addressing with prefix notation /n (e.g., 192.168.1.0/24)
- Supports VLSM (Variable-Length Subnet Mask)
- Enables route aggregation (supernetting)
- Mask 255.255.240.0 = **/20** in CIDR

---

### Q9. Selective Repeat ARQ
**Concept:** Sender sends N frames; receiver buffers out-of-order frames; only LOST frame retransmitted.

**Rules:**
- Sender window = N, Receiver window = N
- Each frame individually ACKed
- Receiver buffers out-of-order frames

**Diagram:**
```
Sender:    F0  F1  F2  F3  F4
              ↓   ↓   X   ↓   ↓
Receiver:  F0✓ F1✓     F3 buf F4 buf
                       TIMEOUT for F2
Sender:    F2 only
Receiver:  F2✓ → delivers F2,F3,F4 in order
```

**Advantage:** Bandwidth efficient. **Disadvantage:** Receiver buffer needed.

---

### Q10. IPv4 Header Format
**Total: 20–60 bytes**

| Field | Size | Role |
|-------|------|------|
| **Version** | 4 bits | IP version (4) |
| **IHL** | 4 bits | Header length in 32-bit words |
| **Type of Service** | 8 bits | Priority/QoS |
| **Total Length** | 16 bits | Datagram total size |
| **Identification** | 16 bits | Fragment grouping |
| **Flags** | 3 bits | DF, MF |
| **Fragment Offset** | 13 bits | Position of fragment |
| **TTL** | 8 bits | Time to live |
| **Protocol** | 8 bits | Upper-layer (TCP=6, UDP=17, ICMP=1) |
| **Header Checksum** | 16 bits | Error detection |
| **Source IP** | 32 bits | Sender IP |
| **Destination IP** | 32 bits | Receiver IP |
| **Options + Padding** | Variable | Optional |

---

## 🟧 PROBLEM SET IV — UNIT 4: NETWORK / TRANSPORT

### Q1. TCP vs UDP Headers
**TCP (20-60 bytes):** Source/Dest Port, Seq#, ACK#, HLen, Flags (URG/ACK/PSH/RST/SYN/FIN), Window, Checksum, Urgent Ptr, Options
**UDP (8 bytes):** Source/Dest Port, Length, Checksum

**Fields TCP has that UDP lacks:**
| Field | Purpose |
|-------|---------|
| Sequence # | Ordered delivery |
| ACK # | Reliable delivery |
| HLen | Variable header due to options |
| Flags | Connection control |
| Window Size | Flow control |
| Urgent Pointer | Out-of-band data |

**Reason:** TCP needs these for reliable, ordered, flow-controlled, connection-oriented service. UDP is unreliable and connectionless, so it doesn't need them.

---

### Q2. Cryptography in Presentation Layer
**Need:** Confidentiality, integrity, authentication, non-repudiation.

| Feature | Symmetric | Asymmetric |
|---------|-----------|------------|
| **Keys** | One shared | Public + Private |
| **Speed** | Fast | Slow |
| **Distribution** | Hard | Easy |
| **Algorithms** | DES, AES, 3DES | RSA, ECC, DSA |
| **Use** | Bulk data | Key exchange, signatures |

---

### Q3. Digital Signature & Security Attacks
**Digital Signature:**
1. Sender hashes message → encrypts with **private key** → signature
2. Sends message + signature
3. Receiver decrypts signature with **sender's public key** → recovers hash
4. Computes hash of message → compares
5. If match → valid (authentic + integrity + non-repudiation)

**Security Attacks:**
- **Passive:** Eavesdropping, Traffic analysis
- **Active:** Masquerade, Replay, Modification, Denial of Service (DoS)

---

### Q4. RSA: N=119, E=5, D=77, send 'F'
**Step 1:** F = 6 (alphabet position)

**Step 2:** Cipher = M^E mod N = 6⁵ mod 119
- 6² = 36
- 6⁴ = 36² = 1296 mod 119 = 1296 – 1190 = **106**
- 6⁵ = 106 × 6 = 636 mod 119 = 636 – 595 = **41**

**Cipher Text C = 41**

**Decryption:** M = 41⁷⁷ mod 119 = **6** ✓

---

### Q5. Sockets & Socket Types
**Socket:** Endpoint of bidirectional communication identified by (IP + Port).

**Types:**
1. **Stream socket (SOCK_STREAM)** — TCP, reliable, connection-oriented
2. **Datagram socket (SOCK_DGRAM)** — UDP, unreliable, connectionless
3. **Raw socket (SOCK_RAW)** — direct access to lower layers (used by ping, traceroute)
4. **Sequenced packet socket (SOCK_SEQPACKET)** — reliable + record-oriented

---

### Q6. Transport Service Primitives & Three-Way Handshake
**Primitives:** LISTEN, CONNECT, SEND, RECEIVE, DISCONNECT

**Three-Way Handshake (TCP setup):**
```
Client                          Server
  |---- SYN, seq=x ------------>|
  |<--- SYN+ACK, seq=y, ack=x+1 |
  |---- ACK, ack=y+1 ---------->|
  |==== Connection Established ==|
```

**Problem solved:** Synchronization of sequence numbers, prevents duplicate old connection requests, ensures both parties are alive and ready.

---

### Q7. QoS Parameters
1. **Reliability** — error rate, loss percentage
2. **Delay (Latency)** — end-to-end time
3. **Jitter** — variation in delay
4. **Bandwidth** — throughput (bps)

---

### Q8. Firewall: Packet Filter vs Proxy Server
| Feature | Packet Filter | Proxy Server |
|---------|---------------|--------------|
| **Layer** | Network (L3) | Application (L7) |
| **Inspects** | Headers (IP/port/protocol) | Full content |
| **Speed** | Very fast | Slower |
| **Security** | Basic | High |
| **Caching** | No | Yes |
| **User Auth** | No | Yes |
| **Example** | iptables, ACL | Squid |

---

### Q9. Leaky Bucket Algorithm
**Purpose:** Traffic shaping — smooths bursty traffic to constant output rate.

**Concept:**
```
   Bursty input
       ↓ ↓ ↓
   ┌─────────┐
   │ Bucket  │ ← FIFO queue
   │_________│
        |
        ↓ (constant rate)
   Smooth output
```

**Working:** Packets poured in; leak at constant rate; if bucket overflows, drop packets.

**Pros:** Controls average rate. **Cons:** No flexibility for bursts (Token Bucket allows this).

---

### Q10. ICMP & Types
*(Same as Unit 3 Q5 — refer above.)*

---

## 🟪 PROBLEM SET V — UNIT 5: APPLICATION LAYER

### Q1. Proxy Server vs Web Server
**Web Server:** Hosts and delivers web pages over HTTP/HTTPS (port 80/443). Examples: Apache, Nginx.
**Proxy Server:** Intermediate server between client and origin. Functions: caching, filtering, anonymity, load balancing.
**Types:** Forward proxy (for clients), Reverse proxy (for servers).

---

### Q2. DNS — What if all DNS servers crashed?
**DNS:** Hierarchical distributed database mapping domain names → IP addresses (UDP port 53).

**If all DNS crashed:**
1. Domain name resolution fails
2. Only direct IP access works (e.g., http://142.250.190.46)
3. Cached entries work until TTL expires
4. Email delivery fails (MX lookup)
5. Most internet apps break
6. Practically the entire internet becomes unusable

---

### Q3. HTTP vs SMTP
| Feature | HTTP | SMTP |
|---------|------|------|
| **Purpose** | Web pages | Email transfer |
| **Type** | Pull | Push |
| **Port** | 80 / 443 | 25 / 587 |
| **State** | Stateless | Stateful |
| **Direction** | Client ↔ Server | Server ↔ Server |

---

### Q4. Hyperlinks & Hypermedia
- **Hyperlink:** Clickable reference within hypertext that navigates to another resource (`<a href="url">`)
- **Hypermedia:** Hypertext + multimedia (images, audio, video, animations)

---

### Q5. Hierarchy of Name Servers
1. **Root DNS Servers** (13 globally, A–M)
2. **TLD Servers** (.com, .org, .in)
3. **Authoritative DNS Servers** (specific domains)
4. **Local DNS Servers** (ISP resolvers)

**Resolution flow:** Client → Local → Root → TLD → Authoritative → IP returned

---

### Q6. Why FTP sends Control Out-of-Band
**FTP uses 2 TCP connections:** Port 21 (control), Port 20 (data).

**Reasons:**
1. Allows ABORT/STAT during transfer (data busy, control free)
2. Cleaner protocol design (no escape sequences in stream)
3. Multiple data transfers possible
4. Better error handling
5. Independent connection lifecycle (control persists, data per-transfer)

---

### Q7. Types of HTTP Messages
**Request methods:** GET, POST, PUT, DELETE, HEAD, OPTIONS, TRACE, CONNECT
**Response status codes:**
- 1xx: Informational
- 2xx: Success (200 OK)
- 3xx: Redirection (301 Moved)
- 4xx: Client error (404 Not Found)
- 5xx: Server error (500)

**Format:** Request line / Status line + Headers + blank line + Body

---

### Q8. SMTP Commands
- **HELO/EHLO** — identify client
- **MAIL FROM:** — sender's address
- **RCPT TO:** — recipient's address
- **DATA** — begin message body (terminated by `.`)
- **RSET** — reset transaction
- **VRFY** — verify user exists
- **NOOP** — keep alive
- **QUIT** — end session

---

### Q9. Active vs Dynamic Web Page
| Feature | Active | Dynamic |
|---------|--------|---------|
| **Where executed** | Client (browser) | Server |
| **Tools** | JavaScript, Applets | PHP, ASP, JSP |
| **Server load** | Low | High |
| **Example** | Form validation | DB-driven product page |

**DB Interface flow:** Browser → Web server → App server (PHP) → SQL → Database → Result → HTML → Browser

---

### Q10. FTP vs TFTP
| Feature | FTP | TFTP |
|---------|-----|------|
| **Transport** | TCP | UDP |
| **Port** | 20, 21 | 69 |
| **Connections** | Two | One |
| **Authentication** | Yes | No |
| **Reliability** | Reliable | Limited |
| **Use** | General file transfer | Bootstrapping, firmware |

---

# PART B — PREVIOUS YEAR SOLVED (UCS6001 — End Sem 2024-25)

**Time: 3 hours | Max Marks: 60**

---

## SECTION A — Very Short Answer (10 × 1 = 10 marks)

### Q1. Why HTTP is called a stateless protocol?
**Answer:** HTTP is stateless because each request from client to server is **independent**. The server does not retain any information about previous requests — every transaction is treated as new. State (e.g., login session) is maintained externally using **cookies, sessions, tokens, or URL parameters**, not by HTTP itself.

---

### Q2. Number of IPs and First/Last IP in 167.199.170.82/27
**Step 1:** /27 → 32-27 = 5 host bits
**Step 2:** Number of IP addresses = 2⁵ = **32**
**Step 3:** Find subnet of 167.199.170.82
- Last octet 82 = 01010010
- Mask /27 → first 3 bits of last octet are network: **010**00000 = 64
- So subnet starts at 167.199.170.64

**First IP (Network):** 167.199.170.64
**Last IP (Broadcast):** 167.199.170.95
**Total IPs:** 32 (usable hosts: 30)

---

### Q3. TCP applications
**Suitable for:** HTTP, HTTPS, FTP, SMTP, SSH, Telnet, IMAP, POP3
**Why:** TCP provides **reliable, ordered, error-checked delivery**. Web pages, emails, file transfers must arrive complete and in order — TCP guarantees this via 3-way handshake, sequence numbers, ACKs, and retransmission.

---

### Q4. What is a Repeater?
**Repeater** is a **Layer 1 (Physical)** networking device that **regenerates and amplifies** weak signals to extend network range.
**Why used:** Compensates for **signal attenuation** over long cables, allowing signals to travel beyond physical media limits without degradation.

---

### Q5. Functions of Transport Layer (OSI)
1. **Process-to-process delivery** using ports
2. **Connection management** (setup, maintain, terminate)
3. **Segmentation and reassembly** of data
4. **Flow control** (sliding window)
5. **Error control** (checksum, retransmission)
6. **Congestion control**
7. **Multiplexing/demultiplexing**

Examples: TCP (reliable), UDP (unreliable).

---

### Q6. Propagation delay (Speed = 8 × 10⁸ m/s, Distance = 400 km)
**Calculation:**
- Distance = 400 km = 4 × 10⁵ m
- Speed = 8 × 10⁸ m/s
- Propagation delay = Distance / Speed = (4 × 10⁵) / (8 × 10⁸) = **5 × 10⁻⁴ s = 0.5 ms**

---

### Q7. Transmission delay (20,000 bits, 4 Mbps)
**Calculation:**
- Packet size = 20,000 bits
- Bandwidth = 4 Mbps = 4 × 10⁶ bps
- Transmission delay = 20,000 / (4 × 10⁶) = **5 × 10⁻³ s = 5 ms**

---

### Q8. Even Parity Bits
**A. 1001011:** Number of 1's = 4 (even) → Parity bit = **0**
**B. 1011101:** Number of 1's = 5 (odd) → Parity bit = **1**

---

### Q9. Simplex Mode
**Definition:** Communication occurs in **only one direction** (one-way only). The sender cannot become receiver, like a one-way street.

**Examples (input devices using simplex):**
1. **Keyboard** — sends data only to computer
2. **Mouse** — sends data only to computer
3. *(Other examples: TV broadcast, radio broadcast)*

---

### Q10. Download time (56 million bytes at 280 Mbps)
**Calculation:**
- File size = 56 × 10⁶ bytes = 56 × 10⁶ × 8 = 448 × 10⁶ bits = **448 Mb**
- Channel = 280 Mbps
- Time = 448 / 280 = **1.6 seconds**

---

## SECTION B — Short Answer (Attempt any 8 of 9 × 2.5 = 20 marks)

### Q1. Circuit Switching: Advantages & Disadvantages
**Working:** Dedicated path established between sender and receiver before data transfer (3 phases: setup, transfer, teardown). Used in PSTN telephone network.

**Advantages:**
- Guaranteed bandwidth (no congestion)
- Predictable performance, low jitter
- Suitable for real-time voice
- Simple sequential delivery

**Disadvantages:**
- Setup delay
- Bandwidth wasted when idle
- Inflexible for bursty data
- Single point of failure (circuit break = call drop)

---

### Q2. Ring Topology: Advantages & Disadvantages
**Working:** Each node connected to two neighbors forming a ring. Data flows in one direction (or both in dual-ring). Token-passing controls access.

**Advantages:**
- Equal access for all nodes (fair)
- No collisions (token-based)
- Performs well under heavy load
- Cheaper than mesh (no central hub needed)

**Disadvantages:**
- Single break disrupts entire ring (single ring)
- Adding/removing devices disrupts network
- Slower than star (data passes through nodes)
- Difficult to troubleshoot

---

### Q3. Internet Checksum for 1001 1100 1010 0011 (4-bit words)
**Words:** 1001 (9), 1100 (12), 1010 (10), 0011 (3)

**Step 1 — Sum with wrap-around (1's complement):**
- 1001 + 1100 = 10101 → wrap: 0101 + 1 = **0110** (6)
- 0110 + 1010 = 10000 → wrap: 0000 + 1 = **0001** (1)
- 0001 + 0011 = **0100** (4)

**Sum = 0100**
**Checksum = 1's complement = 1011**

**Verification:** Receiver sums all 5 (4 data + checksum) → should yield 1111. Indeed 0100 + 1011 = 1111 ✓

---

### Q4. ALOHA Protocol Working
**ALOHA** is the earliest random access protocol developed at U. Hawaii (1970s).

**Pure ALOHA:**
1. Station transmits whenever it has data
2. After transmission, waits for ACK
3. If no ACK (collision occurred) → wait random time → retransmit
4. **Vulnerable period:** 2 × frame time (collision possible if any transmission overlaps)
5. **Max efficiency:** 18.4% (1/2e)

**Slotted ALOHA:**
1. Time divided into discrete slots (size = frame time)
2. Station can only transmit at slot boundary
3. Reduces vulnerable period to 1 × frame time
4. **Max efficiency:** 36.8% (1/e)

```
Pure:    [  Frame from A  ]
            [ Frame from B ]   ← collision anywhere
Slotted: |slot|slot|slot|
         [ A ][ B ]            ← collisions only within slot
```

---

### Q5. Forwarding Tables for Nodes A and F → Smallest Network
**Given tables (cost = 1 per link):**

**Node A:** B→1→B, C→1→C, D→2→B, E→3→C, F→2→C
**Node F:** A→2→C, B→3→C, C→1→C, D→2→C, E→1→E

**Direct links from A:** A—B (cost 1), A—C (cost 1)
**Direct links from F:** F—C (cost 1), F—E (cost 1)

**Path analysis:**
- A→D via B (cost 2) → so **B—D** (cost 1)
- A→F via C (cost 2) → so **C—F** (cost 1) ✓
- A→E via C (cost 3) → A—C—F—E (1+1+1=3) ✓
- F→A via C (cost 2) → F—C—A (1+1=2) ✓
- F→D via C (cost 2) → so **C—D** (cost 1)
- F→B via C (cost 3) → F—C—A—B (1+1+1=3) ✓

**Smallest network has 6 nodes & 6 links:**
```
        A
       / \
      B   C
      |  /|\
      D-' | F
            \
             E
```
Links: A—B, A—C, B—D, C—D, C—F, F—E

---

### Q6. Aggregate /24 networks
**Networks:** 212.56.132.0/24, 212.56.133.0/24, 212.56.134.0/24, 212.56.135.0/24

**Third octet binary:**
- 132 = 10000**100**
- 133 = 10000**101**
- 134 = 10000**110**
- 135 = 10000**111**

**Common prefix:** 100001 (6 bits) — last 2 bits vary.

**Aggregate prefix length:** 8 + 8 + 6 = **/22**
**Aggregated network: 212.56.132.0/22**
*(Covers all addresses from 212.56.132.0 to 212.56.135.255)*

---

### Q7. Network Address Translation (NAT)
**NAT** is a technique that maps multiple **private IP addresses** to a single (or few) **public IP addresses**, conserving IPv4 space and adding security.

**Types:**
1. **Static NAT** — one-to-one fixed mapping
2. **Dynamic NAT** — one-to-many from a pool
3. **PAT/NAPT (Port Address Translation)** — many-to-one using port numbers

**How it works:**
```
[Internal: 192.168.1.5:5000] → [NAT Router] → [Public: 203.0.113.1:6001]
                                  Translation Table
                                  192.168.1.5:5000 ↔ 203.0.113.1:6001
```

**Reply path:** Public→NAT→Internal using table lookup.

**Benefits:**
- Conserves IPv4 addresses
- Hides internal addresses (security)
- Allows multiple devices to share one public IP

---

### Q8. Why UDP is Connectionless
**Reasons UDP is connectionless:**
1. **No 3-way handshake** — sender can transmit immediately
2. **No session state** — each datagram is independent
3. **No acknowledgments** — sender does not wait/track ACKs
4. **No retransmission** — lost packets are not resent
5. **No flow/congestion control** — sender transmits at its own rate
6. **Lower overhead** (8-byte header vs TCP's 20-byte minimum)

**Use cases:** DNS, DHCP, SNMP, video streaming, VoIP, online gaming — where speed matters more than reliability.

---

### Q9. FTP and its Applications
**FTP** = **File Transfer Protocol**, a TCP-based application-layer protocol (RFC 959) for transferring files between client and server.

**Features:**
- Uses **two TCP connections:** Port 21 (control) and Port 20 (data)
- **Out-of-band control** — commands separate from data
- Supports authentication (username/password)
- Two transfer modes: ASCII / Binary
- Two operation modes: Active / Passive

**Applications:**
1. **Uploading websites** to web hosting servers
2. **Downloading software** (open-source tools, drivers)
3. **Backup and restore** of files between servers
4. **File sharing** in offices/educational institutions
5. **Transferring large media files** (videos, datasets)
6. **Server maintenance** by sysadmins

---

## SECTION C — Long Answer (Attempt any 5 of 6 × 6 = 30 marks)

### Q1. Distance Vector Routing — Global DV Tables (3 stages)
**Network:** A—C(3), A—B(8), B—E(1), B—D(2), C—F(6), D—E(2)

**Stage I — Each node knows only direct-neighbor distances:**

| From\To | A | B | C | D | E | F |
|---------|---|---|---|---|---|---|
| **A** | 0 | 8 | 3 | ∞ | ∞ | ∞ |
| **B** | 8 | 0 | ∞ | 2 | 1 | ∞ |
| **C** | 3 | ∞ | 0 | ∞ | ∞ | 6 |
| **D** | ∞ | 2 | ∞ | 0 | 2 | ∞ |
| **E** | ∞ | 1 | ∞ | 2 | 0 | ∞ |
| **F** | ∞ | ∞ | 6 | ∞ | ∞ | 0 |

**Stage II — Each node receives and updates from neighbors:**

| From\To | A | B | C | D | E | F |
|---------|---|---|---|---|---|---|
| **A** | 0 | 8 | 3 | 10 | 9 | 9 |
| **B** | 8 | 0 | 11 | 2 | 1 | ∞ |
| **C** | 3 | 11 | 0 | ∞ | ∞ | 6 |
| **D** | 10 | 2 | ∞ | 0 | 2 | ∞ |
| **E** | 9 | 1 | ∞ | 2 | 0 | ∞ |
| **F** | 9 | ∞ | 6 | ∞ | ∞ | 0 |

**Stage III — After second exchange (converged or near-converged):**

| From\To | A | B | C | D | E | F |
|---------|---|---|---|---|---|---|
| **A** | 0 | 8 | 3 | 10 | 9 | 9 |
| **B** | 8 | 0 | 11 | 2 | 1 | 17 |
| **C** | 3 | 11 | 0 | 13 | 12 | 6 |
| **D** | 10 | 2 | 13 | 0 | 2 | 19 |
| **E** | 9 | 1 | 12 | 2 | 0 | 18 |
| **F** | 9 | 17 | 6 | 19 | 18 | 0 |

**Algorithm used:** Bellman-Ford. Each node updates: D(x,y) = min over neighbors n of [c(x,n) + D(n,y)]

---

### Q2. Routing Table Forwarding for 5 Destinations
**Routing table:**
| SubnetNumber | SubnetMask | NextHop |
|-------------|------------|---------|
| 128.96.39.0 | 255.255.255.128 | Interface 0 |
| 128.96.39.128 | 255.255.255.128 | Interface 1 |
| 128.96.40.0 | 255.255.255.128 | R2 |
| 192.4.153.0 | 255.255.255.192 | R3 |
| (default) | – | R4 |

**Process:** AND destination IP with each subnet mask; if result matches a SubnetNumber, forward to that NextHop. Otherwise default.

**i. 128.96.39.10:**
- AND with 255.255.255.128 → 128.96.39.0 → **Interface 0**

**ii. 128.96.40.12:**
- AND with 255.255.255.128 → 128.96.40.0 → **R2**

**iii. 128.96.40.151:**
- AND with 255.255.255.128 → 128.96.40.128 → not in table → **R4 (default)**

**iv. 192.4.153.17:**
- AND with 255.255.255.192 → 192.4.153.0 → **R3**

**v. 192.4.153.90:**
- 90 in binary = 01011010
- AND with 11000000 = 01000000 = 64
- Result: 192.4.153.64 → not in table → **R4 (default)**

---

### Q3. Framing Methods for "A B ESC FLAG"
**Given codes:**
- A = 01000111
- B = 11100011
- FLAG = 01111110
- ESC = 11100000

**I. Byte Count:**
First byte = total bytes including count = 5
**Transmitted:** `00000101 01000111 11100011 11100000 01111110`

---

**II. Flag Bytes with Byte Stuffing:**
Frame surrounded by FLAG bytes. Inside data, stuff ESC before any FLAG or ESC byte.

Data: A, B, ESC, FLAG
- A → A
- B → B
- ESC → **ESC** ESC (stuff ESC before ESC)
- FLAG → **ESC** FLAG (stuff ESC before FLAG)

**Transmitted:**
`FLAG | A | B | ESC ESC | ESC FLAG | FLAG`
= `01111110 01000111 11100011 11100000 11100000 11100000 01111110 01111110`

---

**III. Flag Bits with Bit Stuffing:**
Frame delimited by FLAG (01111110). After every 5 consecutive 1's in data, stuff a 0.

**Original data bits (32):**
`01000111 11100011 11100000 01111110`

**Scan for 5+ consecutive 1's:**
- Bits 6–11: six 1's → stuff 0 after 5th 1 (after bit 10)
- Bits 15–19: five 1's → stuff 0 after bit 19
- Bits 26–31: six 1's (FLAG) → stuff 0 after 5th 1 (after bit 30)

**Stuffed data:** `01000 11111 0 1 000 11111 0 000000 11111 0 10`

Concatenated stream:
`01111110 01000111110100011111000000011111010 01111110`

(8 + 35 + 8 = 51 bits)

---

### Q4. Cookies — Why used, How created and stored
**Cookie:** Small text file (typically <4 KB) stored on the client browser by a web server, containing data about the user's session/preferences.

**Why used:**
1. **Session management** — login state, shopping carts
2. **Personalization** — language, theme, preferences
3. **Tracking** — analytics, advertising
4. **Authentication tokens** — keep user logged in

**How created (Server-side):**
1. Client sends HTTP request: `GET /index.html`
2. Server responds with: `Set-Cookie: sessionID=abc123; Expires=...; Secure; HttpOnly`
3. Browser stores the cookie locally

**How stored (Client-side):**
- Stored in browser's cookie database (file or storage area)
- Each cookie has: name, value, domain, path, expiration, secure flag, HttpOnly flag

**On subsequent requests:**
- Browser sends `Cookie: sessionID=abc123` header automatically with every request to the same domain.

**Types:**
- **Session cookies** — deleted when browser closes
- **Persistent cookies** — have expiration date
- **Secure cookies** — sent only over HTTPS
- **HttpOnly cookies** — inaccessible to JavaScript (XSS protection)
- **Third-party cookies** — set by domains other than the visited site

---

### Q5. Go-Back-N Protocol (Transport Layer)
**Concept:** Pipelined sliding window protocol that allows sender to transmit up to **N** unacknowledged frames. On loss, retransmit the lost frame and ALL subsequent ones.

**Rules:**
- Sender window size = N (e.g., 4)
- Receiver window size = 1
- Cumulative ACK (ACKn means "received all up to n-1")
- Receiver discards out-of-order frames
- On timeout: sender retransmits all N pending frames

**Example with window size N=4:**

```
Time →
Sender:    F0 F1 F2 F3 (window full, wait for ACK)
              ↓  ↓  X  ↓
Receiver:  F0 F1    F3 (out of order — discard)
              ↑  ↑
              A1 A2 (cumulative ACK: A2 = "received up to F1")
              
              [Timeout for F2]
              
Sender:    F2 F3 F4 F5 (retransmit F2 and onwards)
              ↓  ↓  ↓  ↓
Receiver:  F2 F3 F4 F5 ✓
              ↑  ↑  ↑  ↑
              A3 A4 A5 A6
```

**Pros:** Simpler than Selective Repeat (no buffer at receiver), better than Stop-and-Wait.
**Cons:** Wastes bandwidth retransmitting frames already correctly received.

**Efficiency:** η = N / (1 + 2a) where a = T_prop/T_trans

---

### Q6. Slow Start (Exponential Increase) Algorithm
**Slow Start** is a TCP **congestion control** algorithm that **exponentially** increases the congestion window (cwnd) until either packet loss occurs or threshold (ssthresh) is reached.

**Algorithm:**
1. Initialize **cwnd = 1 MSS** (Maximum Segment Size)
2. For each ACK received → **cwnd = cwnd + 1 MSS** (effectively doubling per RTT)
3. Continue until cwnd ≥ **ssthresh** (slow start threshold)
4. Switch to **Congestion Avoidance** (linear increase)
5. On packet loss (timeout):
   - ssthresh = cwnd / 2
   - cwnd = 1 MSS
   - Restart slow start

**Why "slow"?** It starts slowly (cwnd = 1) but grows fast (exponential).

**Diagram:**
```
cwnd
  |                               (timeout)
  |              /\               /
  |             /  \-------------/   (linear: Congestion Avoidance)
  |            /     ssthresh new
  |           /       /
  |          /       /
  |         /  (exp)/
  |        / Slow  /
  |       /  Start/
  |      /       /
  |     /       /
  |    /       /
  |   /       /
  |  /       /
  | /       /
  +--------+----------+----------+----> Time (RTT)
                  (loss)         
```

**Window growth (RTT-by-RTT):**
- RTT 1: cwnd = 1
- RTT 2: cwnd = 2
- RTT 3: cwnd = 4
- RTT 4: cwnd = 8
- RTT 5: cwnd = 16 → if ≥ ssthresh, switch to linear
- ...

**Goal:** Probe network capacity quickly without overwhelming, then settle into stable operation.

---

# END OF EXAM PREPARATION DOCUMENT

> **Total content:** 50 problem-set questions explained + 25 previous-year questions solved (10 + 9 + 6 = 25 attempted)
> **Use this file** as your **complete final-prep** companion in the last 48 hours before exam.
