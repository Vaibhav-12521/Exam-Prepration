# DCCN COMPLETE SYLLABUS NOTES — UNITS 1 TO 5
**Course:** BCA / B.Sc(IT) | **Subject Code:** US6001 | **Sem VI**

---

# 🟦 UNIT – I: INTRODUCTION TO NETWORKS

## 📌 1.1 Computer Network – Definition
├── **Definition:** A computer network is a collection of two or more autonomous devices (computers, printers, servers) interconnected through a transmission medium to share resources and information.
├── **Key Points:**
- Allows resource sharing (files, printers, internet)
- Provides communication (email, chat, video)
- Improves reliability through redundancy
- Saves cost via shared resources
- Enables centralized management
- Types: LAN, MAN, WAN
├── **Important Terms:**
   - **Node:** Any device on the network
   - **Link:** Connection between two nodes
   - **Protocol:** Set of rules for communication
├── **One-line Exam Answer:** A computer network is an interconnected collection of autonomous computing devices that share resources and exchange data.

---

## 📌 1.2 Network Topologies
├── **Definition:** A topology is the physical or logical arrangement of nodes (computers) and links in a network.
├── **Key Points:**
- **Mesh:** Every device connected to every other; n(n-1)/2 links; high reliability, expensive
- **Star:** All devices connected to a central hub/switch; easy to manage; hub failure = total failure
- **Bus:** All devices share single backbone cable; cheap; backbone failure = total failure
- **Ring:** Each device connected to next forming a ring; data travels in one direction
- **Tree:** Hierarchical combination of bus and star
- **Hybrid:** Combination of two or more topologies

├── **Diagrams:**
```
MESH:                STAR:           BUS:
A----B-----C         A   B   C       A--+--B--+--C
|\  /|\   /|          \  |  /           |     |
| \/ | \ / |           \ | /             D     E
| /\ | / \ |            HUB
|/  \|/   \|           / | \
D----E-----F          D  E  F

RING:                TREE:
   A                    HUB
  / \                   / \
 D   B                Sub  Sub
  \ /                 /\    /\
   C                 A  B  C  D
```

├── **One-line Exam Answer:** Topology is the geometric arrangement of computers (nodes) and links in a network.

---

## 📌 1.3 Protocols and Standards
├── **Definition:** A protocol is a set of rules governing data communication. Standards are documented agreements ensuring interoperability across vendors.
├── **Key Points:**
- Three key elements of protocol: **Syntax** (format), **Semantics** (meaning), **Timing** (when to send)
- Standards bodies: **IEEE, ISO, ITU-T, ANSI, IETF**
- De facto standards: not formally approved (e.g., Bluetooth originally)
- De jure standards: legally formal (e.g., OSI model)
├── **Important Terms:**
   - **IEEE 802.3** – Ethernet
   - **IEEE 802.11** – Wi-Fi
   - **TCP/IP** – Internet protocol suite
├── **One-line Exam Answer:** A protocol is a set of rules and conventions for data exchange; standards ensure these rules are universally followed.

---

## 📌 1.4 OSI Reference Model (7 Layers)
├── **Definition:** The OSI (Open Systems Interconnection) model is a 7-layer conceptual framework for understanding network communication, developed by ISO in 1984.
├── **Key Points (Mnemonic – "All People Seem To Need Data Processing"):**

| Layer | Name | Function | PDU | Devices |
|-------|------|----------|-----|---------|
| 7 | **Application** | User interface (HTTP, SMTP, FTP) | Message | Gateway |
| 6 | **Presentation** | Translation, encryption, compression | Message | Gateway |
| 5 | **Session** | Dialog control, synchronization | Message | Gateway |
| 4 | **Transport** | End-to-end delivery (TCP, UDP) | Segment | – |
| 3 | **Network** | Routing, logical addressing (IP) | Packet | Router |
| 2 | **Data Link** | Framing, MAC addressing, error control | Frame | Switch, Bridge |
| 1 | **Physical** | Bits over medium (signals) | Bit | Hub, Repeater |

├── **Diagram:**
```
+---------------------+
|  7. Application     |  ← HTTP, FTP, SMTP
+---------------------+
|  6. Presentation    |  ← Encryption, Compression
+---------------------+
|  5. Session         |  ← Dialog Control
+---------------------+
|  4. Transport       |  ← TCP, UDP
+---------------------+
|  3. Network         |  ← IP, Routers
+---------------------+
|  2. Data Link       |  ← Switches, MAC
+---------------------+
|  1. Physical        |  ← Cables, Hubs
+---------------------+
```

├── **One-line Exam Answer:** The OSI model is a 7-layer reference architecture (Physical, Data Link, Network, Transport, Session, Presentation, Application) standardizing network functions.

---

## 📌 1.5 TCP/IP Protocol Suite (Internet Model)
├── **Definition:** The TCP/IP model is a practical 4-layer (or sometimes 5-layer) protocol stack used in the Internet, developed before OSI.
├── **Key Points:**

| TCP/IP Layer | OSI Equivalent | Protocols |
|--------------|----------------|-----------|
| **Application** | Application + Presentation + Session | HTTP, FTP, SMTP, DNS |
| **Transport** | Transport | TCP, UDP |
| **Internet** | Network | IP, ICMP, ARP |
| **Network Access (Link)** | Data Link + Physical | Ethernet, Wi-Fi |

├── **Diagram:**
```
TCP/IP                OSI
+-----------+        +-------------+
|Application|        |Application  |
|           |        +-------------+
|           |        |Presentation |
|           |        +-------------+
|           |        |Session      |
+-----------+        +-------------+
| Transport |        |Transport    |
+-----------+        +-------------+
| Internet  |        |Network      |
+-----------+        +-------------+
| Network   |        |Data Link    |
| Access    |        +-------------+
|           |        |Physical     |
+-----------+        +-------------+
```

├── **One-line Exam Answer:** The TCP/IP model is a 4-layer protocol stack (Network Access, Internet, Transport, Application) that is the basis of the modern Internet.

---

## 📌 1.6 Transmission Media
├── **Definition:** Physical paths through which data travels between nodes; either guided (cables) or unguided (wireless).

### A. Guided Media:
| Type | Bandwidth | Distance | Use |
|------|-----------|----------|-----|
| **Twisted Pair (UTP/STP)** | Up to 100 Mbps | ~100 m | LAN, Telephone |
| **Coaxial Cable** | Up to 1 Gbps | ~500 m | Cable TV, older LAN |
| **Optical Fiber** | THz | 100+ km | Internet backbone |

### B. Unguided Media (Wireless):
- **Radio waves** – broadcast, AM/FM
- **Microwaves** – cellular, satellite
- **Infrared** – TV remote, short range
- **Bluetooth, Wi-Fi** – personal/local wireless

├── **One-line Exam Answer:** Transmission media are physical/wireless paths used for data signal travel; categorized into guided (wired) and unguided (wireless).

---

## 📌 1.7 Addressing in Networks
├── **Definition:** Addressing is the mechanism to uniquely identify devices and processes on a network.
├── **Types of Addresses:**

| Layer | Address Type | Example | Length |
|-------|--------------|---------|--------|
| Application | Specific (URL, Email) | www.google.com | Variable |
| Transport | Port number | 80, 443 | 16 bits |
| Network | IP address (logical) | 192.168.1.5 | 32 bits (IPv4) / 128 bits (IPv6) |
| Data Link | MAC address (physical) | 00:1A:2B:3C:4D:5E | 48 bits |

├── **One-line Exam Answer:** Addressing schemes (MAC, IP, Port) at different OSI layers uniquely identify hosts, networks, and processes for end-to-end communication.

---

## 📌 1.8 Networking Devices

| Device | Layer | Function |
|--------|-------|----------|
| **Repeater** | Physical | Regenerates weak signals |
| **Hub** | Physical | Connects multiple devices (broadcasts to all) |
| **Bridge** | Data Link | Connects two LAN segments |
| **Switch** | Data Link | Multi-port bridge with MAC table (forwards selectively) |
| **Router** | Network | Connects different networks, routes packets |
| **Gateway** | All | Connects networks of different protocols |
| **Modem** | Physical | Modulates/demodulates analog ↔ digital |
| **NIC** | Data Link | Network Interface Card – connects host to network |

├── **One-line Exam Answer:** Networking devices (hub, switch, router, etc.) operate at different OSI layers to connect, segment, and route traffic in a network.

---

## 📌 1.9 LAN, MAN, WAN
├── **Definition:** Networks are classified by geographic scope.

| Type | Range | Speed | Example |
|------|-------|-------|---------|
| **LAN** (Local Area) | <1 km (room/building) | High (1 Gbps+) | Office Ethernet |
| **MAN** (Metropolitan) | City-wide (10-50 km) | Medium | Cable TV network |
| **WAN** (Wide Area) | Country/global (>100 km) | Lower | Internet |
| **PAN** (Personal) | <10 m | Bluetooth | Wireless earbuds |

├── **One-line Exam Answer:** Networks are categorized by geographic scope: PAN (<10m), LAN (<1km), MAN (city), WAN (country/global).

---

# 🟩 UNIT – II: PHYSICAL LAYER & DATA LINK LAYER

## 📌 2.1 Data and Signals
├── **Definition:** Data is the information to be communicated; signal is the electric/electromagnetic representation of data.
├── **Key Points:**
- **Analog signal:** continuous waveform (sine wave)
- **Digital signal:** discrete values (0s and 1s)
- Analog signal: amplitude, frequency, phase
- Digital signal: bit rate, bit length
- **Bandwidth** = range of frequencies (Hz)
- **Bit rate** = bits per second (bps)
├── **One-line Exam Answer:** Data is information; signals are analog or digital electromagnetic representations of that data over a medium.

---

## 📌 2.2 Transmission Impairments
├── **Definition:** Imperfections that degrade signal quality during transmission.
├── **Three main types:**

1. **Attenuation** – loss of signal energy with distance (use amplifiers/repeaters)
2. **Distortion** – signal shape changes (different frequencies travel differently)
3. **Noise** – unwanted signals interfering with the original
   - **Thermal noise** (random electron motion)
   - **Induced noise** (motors, appliances)
   - **Crosstalk** (between adjacent wires)
   - **Impulse noise** (lightning, power surges)

├── **One-line Exam Answer:** Transmission impairments (attenuation, distortion, noise) are signal degradations that reduce data communication quality.

---

## 📌 2.3 Data Rate Limits — Nyquist & Shannon
├── **Definition:** Maximum theoretical bit rate possible over a channel.
├── **Two Formulas:**

**1. Nyquist (Noiseless Channel):**
> **C = 2 × B × log₂(L)**
- B = bandwidth (Hz)
- L = number of signal levels
- C = maximum bit rate (bps)

**2. Shannon (Noisy Channel):**
> **C = B × log₂(1 + SNR)**
- SNR = Signal-to-Noise Ratio (linear)
- SNR(dB) = 10 × log₁₀(SNR)

├── **Example:** B=4kHz, L=4 → Nyquist: C = 2×4000×log₂4 = **16 kbps**
├── **One-line Exam Answer:** Nyquist gives max bit rate for noiseless (2B log₂L); Shannon gives max for noisy channel (B log₂(1+SNR)).

---

## 📌 2.4 Performance Metrics
| Metric | Definition |
|--------|-----------|
| **Bandwidth** | Range of frequencies / data rate of channel |
| **Throughput** | Actual data delivered per second (≤ Bandwidth) |
| **Latency (Delay)** | Time from sender → receiver |
| **Jitter** | Variation in delay |
| **Bandwidth-Delay Product** | Capacity = Bandwidth × RTT (bits in flight) |

**Total Latency = Propagation + Transmission + Queuing + Processing delays**

├── **One-line Exam Answer:** Performance is measured by bandwidth, throughput, latency, jitter, and bandwidth-delay product.

---

## 📌 2.5 Switching
├── **Definition:** Mechanism by which data is transferred between nodes through intermediate devices.

### Three types:
1. **Circuit Switching** – dedicated path (telephone)
2. **Packet Switching** – packets routed independently (Internet)
   - **Datagram approach** – each packet treated separately
   - **Virtual Circuit approach** – logical path established
3. **Message Switching** – store-and-forward of complete messages (obsolete)

├── **One-line Exam Answer:** Switching is the technique by which data is moved between nodes — circuit, packet, or message switching.

---

## 📌 2.6 Multiplexing
├── **Definition:** Technique to share a single transmission medium among multiple signals/users simultaneously.

### Types:
1. **FDM** (Frequency Division Multiplexing) – different frequencies (radio)
2. **TDM** (Time Division Multiplexing) – different time slots (digital phone)
3. **WDM** (Wavelength Division) – different wavelengths in fiber (optical)
4. **CDM** (Code Division) – different codes (3G mobile)

├── **Diagram:**
```
FDM:  [Signal A][Signal B][Signal C]   (different frequency bands)
TDM:  [A1][B1][C1][A2][B2][C2]...      (time slots rotated)
```
├── **One-line Exam Answer:** Multiplexing combines multiple signals onto one channel via FDM (frequency), TDM (time), WDM (wavelength), or CDM (code).

---

## 📌 2.7 Data Link Layer Services
├── **Definition:** Layer 2 of OSI; provides reliable transfer of frames between adjacent nodes.
├── **Services:**
1. **Framing** – divides bits into frames
2. **Physical Addressing** – adds source/destination MAC
3. **Flow Control** – prevents overwhelming receiver
4. **Error Control** – detect and correct errors
5. **Access Control** – manages shared medium
6. **Reliable Delivery** – through ACKs and retransmissions

├── **One-line Exam Answer:** Data link layer provides framing, addressing, error control, flow control, and access control services for hop-by-hop reliable delivery.

---

## 📌 2.8 Framing
├── **Definition:** Process of dividing the bit stream from network layer into discrete units (frames) at the data link layer.
├── **Methods:**
1. **Character Count** – first byte indicates frame length
2. **Byte Stuffing (Flag bytes)** – escape character before flag in data
3. **Bit Stuffing (Flag bits)** – insert 0 after every 5 ones in data
4. **Physical Layer Coding Violations** – use illegal bit patterns

├── **Bit Stuffing Example:**
Data: `01111110` → after stuffing: `011111**0**10` (extra 0 inserted after 5 ones)

├── **One-line Exam Answer:** Framing is the data link layer technique to break the bit stream into manageable frames using count, byte/bit stuffing, or physical layer methods.

---

## 📌 2.9 Error Detection & Correction

### Detection methods:
1. **Parity check** (single bit – even/odd)
2. **Two-dimensional parity** (rows + columns)
3. **Checksum** (sum of segments + 1's complement)
4. **CRC (Cyclic Redundancy Check)** – uses polynomial division

### Correction methods:
- **Hamming Code** – inserts parity bits at positions 1, 2, 4, 8...
- **Hamming Distance** = number of differing bits between two codewords
- For correction of d errors → minimum distance = 2d+1

├── **One-line Exam Answer:** Errors are detected via parity, checksum, CRC; corrected via Hamming code, requiring redundant bits in the message.

---

## 📌 2.10 ARQ Protocols (Automatic Repeat reQuest)

| Protocol | Window | Receiver Buffer | Retransmission |
|----------|--------|-----------------|----------------|
| **Stop-and-Wait** | 1 | None | Single frame |
| **Go-Back-N** | N | None | All from lost frame onward |
| **Selective Repeat** | N | N | Only the lost frame |

├── **Efficiency:** η = N / (1+2a), where a = T_prop/T_trans
├── **One-line Exam Answer:** ARQ protocols (Stop-and-Wait, Go-Back-N, Selective Repeat) provide reliable delivery via acknowledgments and retransmission.

---

# 🟨 UNIT – III: LLC / MAC SUB-LAYER

## 📌 3.1 LLC (Logical Link Control) Sub-Layer
├── **Definition:** Upper sub-layer of data link layer (IEEE 802.2); handles flow control, error control, framing.
├── **Key Points:**
- Provides interface to network layer
- Independent of physical medium
- Three service types: unacknowledged connectionless, connection-oriented, acknowledged connectionless
├── **One-line Exam Answer:** LLC is the upper data link sublayer providing flow/error control and a uniform interface to upper layers regardless of MAC.

---

## 📌 3.2 MAC (Medium Access Control) Sub-Layer
├── **Definition:** Lower sub-layer of data link layer; controls how devices access the shared communication medium.
├── **Key Points:**
- Solves "channel allocation problem" in shared media
- Provides MAC addresses
- Implements multiple access protocols
├── **One-line Exam Answer:** MAC sub-layer manages access to shared transmission medium and provides physical addressing.

---

## 📌 3.3 Channel Allocation Problem
├── **Definition:** Problem of allocating a shared channel to multiple competing users.
├── **Two approaches:**
1. **Static allocation** – FDM, TDM (wasteful for bursty traffic)
2. **Dynamic allocation** – allocated as needed (more efficient)

├── **One-line Exam Answer:** Channel allocation is deciding which station can transmit on a shared medium; can be static (FDM/TDM) or dynamic (random/controlled access).

---

## 📌 3.4 Multiple Access Protocols
├── **Categories:**
- **Random Access:** ALOHA, CSMA, CSMA/CD, CSMA/CA
- **Controlled Access:** Polling, Reservation, Token Passing
- **Channelization:** FDMA, TDMA, CDMA

---

## 📌 3.5 ALOHA & Slotted ALOHA
├── **Definition:** Earliest random access protocols developed at the University of Hawaii.

| Feature | Pure ALOHA | Slotted ALOHA |
|---------|-----------|---------------|
| **Timing** | Send anytime | Send only at slot boundaries |
| **Vulnerable period** | 2 × frame time | 1 × frame time |
| **Max efficiency** | 18.4% | 36.8% |
| **Collisions** | More | Fewer |

├── **Diagrams:**
```
Pure ALOHA:    A--+    Frame from A
             B--+      Frame from B (collision possible anytime)
                |
Slotted ALOHA: |slot|slot|slot|slot|
               A    B    C
               (collisions only within slot)
```
├── **One-line Exam Answer:** ALOHA is a random access protocol where stations transmit anytime (pure) or at slot boundaries (slotted, doubling efficiency).

---

## 📌 3.6 CSMA (Carrier Sense Multiple Access)
├── **Definition:** Stations listen ("sense") to the channel before transmitting to avoid collisions.
├── **Variations:**
- **1-persistent:** if idle, send immediately (high collision risk)
- **Non-persistent:** if busy, wait random time
- **p-persistent:** if idle, transmit with probability p
├── **One-line Exam Answer:** CSMA reduces collisions by sensing the channel before transmitting; variations differ in waiting strategy.

---

## 📌 3.7 CSMA/CD vs CSMA/CA
| CSMA/CD | CSMA/CA |
|---------|---------|
| Used in **Ethernet** (wired) | Used in **Wi-Fi** (wireless) |
| Detect collision after | Avoid collision before |
| Sense → Send → Detect → Backoff | Sense → Wait IFS → Backoff → RTS/CTS → Send → ACK |

├── **One-line Exam Answer:** CSMA/CD detects collisions in wired networks; CSMA/CA avoids them in wireless via RTS/CTS handshake.

---

## 📌 3.8 IPv4 Addressing
├── **Definition:** 32-bit address used to uniquely identify a host on the Internet, written in dotted decimal (e.g., 192.168.1.1).
├── **Classes:**

| Class | First Octet | Default Mask | # Networks | # Hosts |
|-------|-------------|--------------|------------|---------|
| A | 0-127 | /8 | 128 | 16,777,214 |
| B | 128-191 | /16 | 16,384 | 65,534 |
| C | 192-223 | /24 | 2,097,152 | 254 |
| D | 224-239 | – | (multicast) | – |
| E | 240-255 | – | (reserved) | – |

├── **Special Addresses:**
- **127.0.0.1** – loopback (localhost)
- **0.0.0.0** – default route
- **255.255.255.255** – limited broadcast
- **169.254.x.x** – APIPA

├── **One-line Exam Answer:** IPv4 is a 32-bit logical address divided into 5 classes (A-E) for unicast, multicast, and reserved use.

---

## 📌 3.9 Subnetting & CIDR
├── **Definition:** Subnetting divides a large network into smaller subnetworks; CIDR replaces classful addressing with prefix notation.
├── **Formulas:**
- Number of subnets = 2ⁿ (n = borrowed bits)
- Number of usable hosts = 2ʰ – 2 (h = host bits)

├── **Example:** 255.255.255.224 → mask /27
- Subnet bits = 3 → 8 subnets
- Host bits = 5 → 30 hosts/subnet

├── **CIDR notation:** 192.168.1.0/24 (instead of 192.168.1.0 + 255.255.255.0)
├── **VLSM:** Variable-Length Subnet Mask – different subnets, different sizes
├── **One-line Exam Answer:** Subnetting divides a network into smaller logical networks; CIDR uses /n prefix notation enabling efficient and flexible IP allocation.

---

## 📌 3.10 IPv6 Addressing
├── **Definition:** 128-bit address scheme to replace IPv4, written in hexadecimal (8 groups of 4 hex digits).
├── **Example:** 2001:0DB8:85A3:0000:0000:8A2E:0370:7334
├── **Key Features:**
- 128-bit (≈ 3.4 × 10³⁸ addresses)
- No NAT needed (huge address space)
- Built-in IPSec security
- No broadcast (uses multicast/anycast)
- Simplified header
- Auto-configuration

├── **One-line Exam Answer:** IPv6 is a 128-bit address scheme designed to replace IPv4, providing vast address space, security, and auto-configuration.

---

## 📌 3.11 ICMP (Internet Control Message Protocol)
├── **Definition:** Network-layer protocol for error reporting and diagnostics in IP networks.
├── **Types of messages:**
- **Error-reporting:** Destination Unreachable, Time Exceeded, Source Quench, Redirect, Parameter Problem
- **Query:** Echo Request/Reply (ping), Timestamp, Address Mask, Router Solicitation
├── **One-line Exam Answer:** ICMP is an IP-layer helper protocol used for error reporting and diagnostic queries (ping, traceroute).

---

## 📌 3.12 ARP & RARP
├── **ARP (Address Resolution Protocol):** Maps IP → MAC address.
├── **RARP (Reverse ARP):** Maps MAC → IP address (used by diskless workstations; mostly replaced by DHCP).
├── **Working of ARP:**
1. Host A wants to send to IP X
2. A broadcasts: "Who has IP X?"
3. Host with IP X replies: "I am at MAC YY:YY:YY:YY:YY:YY"
4. A caches the IP-to-MAC mapping

├── **One-line Exam Answer:** ARP resolves IP to MAC; RARP resolves MAC to IP — both used in IPv4 networks.

---

## 📌 3.13 Routing Protocols

### A. Unicast Routing (one-to-one)
- **Distance Vector** (RIP) – Bellman-Ford algorithm; uses hop count
- **Link State** (OSPF) – Dijkstra's algorithm; full topology view
- **Path Vector** (BGP) – inter-AS routing

### B. Multicast Routing (one-to-many)
- **DVMRP** – Distance Vector Multicast
- **MOSPF** – OSPF for multicast
- **PIM** – Protocol Independent Multicast (Sparse/Dense modes)

├── **One-line Exam Answer:** Routing protocols (RIP, OSPF, BGP for unicast; DVMRP, PIM for multicast) determine the best path for IP packets.

---

# 🟧 UNIT – IV: NETWORK & TRANSPORT LAYER

## 📌 4.1 Transport Layer Overview
├── **Definition:** Layer 4 of OSI; provides end-to-end (process-to-process) communication via ports.
├── **Functions:**
- Process-to-process delivery (using ports)
- Connection establishment and termination
- Flow control and error control
- Congestion control
- Reliable (TCP) or unreliable (UDP) delivery

├── **One-line Exam Answer:** Transport layer provides end-to-end process-to-process delivery, connection management, and flow/error/congestion control.

---

## 📌 4.2 TCP (Transmission Control Protocol)
├── **Definition:** Connection-oriented, reliable, ordered, byte-stream transport protocol.
├── **Features:**
- Connection-oriented (3-way handshake)
- Reliable (sequence numbers, ACKs, retransmission)
- Ordered delivery
- Flow control (sliding window)
- Congestion control (slow start, congestion avoidance)
- Full-duplex

├── **TCP Header Fields (20-60 bytes):**
- Source/Dest Port (16 bits each)
- Sequence Number (32 bits)
- ACK Number (32 bits)
- Data Offset (4 bits) + Reserved (6 bits) + Flags (URG, ACK, PSH, RST, SYN, FIN)
- Window Size (16 bits)
- Checksum (16 bits)
- Urgent Pointer (16 bits)
- Options (variable)

├── **One-line Exam Answer:** TCP is a reliable, connection-oriented transport protocol providing ordered byte-stream delivery with flow/congestion control.

---

## 📌 4.3 UDP (User Datagram Protocol)
├── **Definition:** Connectionless, unreliable, lightweight transport protocol.
├── **Features:**
- No connection setup (faster)
- No reliability/ordering
- No congestion control
- Low overhead (8-byte header)
- Used for: DNS, DHCP, streaming, VoIP, online gaming

├── **UDP Header (8 bytes):**
- Source Port (16 bits)
- Dest Port (16 bits)
- Length (16 bits)
- Checksum (16 bits)

├── **One-line Exam Answer:** UDP is a connectionless, unreliable transport protocol with minimal overhead used for time-sensitive applications.

---

## 📌 4.4 Three-Way Handshake (TCP)
├── **Diagram:**
```
Client                    Server
  |--- SYN, seq=x -------->|
  |<-- SYN+ACK, y, ack=x+1 |
  |--- ACK, ack=y+1 ------>|
  |==== Connected =========|
```
├── **One-line Exam Answer:** TCP three-way handshake (SYN, SYN-ACK, ACK) synchronizes sequence numbers and establishes a reliable connection.

---

## 📌 4.5 Congestion Control
├── **Definition:** Mechanism to prevent network overloading by controlling sender's transmission rate.
├── **TCP Algorithms:**
1. **Slow Start** – cwnd starts at 1, doubles every RTT until threshold
2. **Congestion Avoidance** – linear increase after threshold
3. **Fast Retransmit** – retransmit on 3 duplicate ACKs
4. **Fast Recovery** – halve cwnd on triple-dup ACK (instead of restart)

├── **Algorithms (Open-loop):**
- **Leaky Bucket** – output at constant rate
- **Token Bucket** – allows bursts up to bucket size

├── **One-line Exam Answer:** Congestion control regulates sender rate (slow start, congestion avoidance, fast retransmit/recovery) to prevent network overload.

---

## 📌 4.6 Leaky Bucket vs Token Bucket
| Feature | Leaky Bucket | Token Bucket |
|---------|--------------|--------------|
| **Output rate** | Constant | Variable (bursts allowed) |
| **Bucket holds** | Packets | Tokens |
| **Burst** | Not allowed | Allowed (up to bucket size) |
| **Use** | Strict shaping | Flexible shaping |

---

## 📌 4.7 Sockets
├── **Definition:** An endpoint of bidirectional communication identified by IP + Port.
├── **Types:**
- **Stream socket (SOCK_STREAM)** – TCP
- **Datagram socket (SOCK_DGRAM)** – UDP
- **Raw socket (SOCK_RAW)** – low-level protocol access
├── **One-line Exam Answer:** A socket is the (IP, Port) endpoint of network communication, available as stream (TCP), datagram (UDP), or raw types.

---

## 📌 4.8 QoS (Quality of Service)
├── **Parameters:**
- **Reliability** (error/loss rate)
- **Delay** (latency)
- **Jitter** (delay variation)
- **Bandwidth** (throughput)
├── **Techniques:** Scheduling (FIFO, Priority, Weighted Fair Queueing), Traffic shaping (Leaky/Token bucket), Resource reservation (RSVP), Admission control
├── **One-line Exam Answer:** QoS uses techniques like scheduling, traffic shaping, and admission control to guarantee parameters of reliability, delay, jitter, and bandwidth.

---

## 📌 4.9 Cryptography
├── **Definition:** Science of secure communication using mathematical algorithms.
├── **Types:**

| Type | Key | Speed | Algorithms |
|------|-----|-------|------------|
| **Symmetric** | Same key | Fast | DES, AES, 3DES |
| **Asymmetric** | Public/Private pair | Slow | RSA, ECC, DSA |

├── **Goals (CIA):** Confidentiality, Integrity, Authentication (also Non-repudiation)
├── **One-line Exam Answer:** Cryptography secures data via symmetric (single key) or asymmetric (public/private key pair) algorithms.

---

## 📌 4.10 RSA Algorithm
├── **Definition:** Asymmetric encryption based on the difficulty of factoring large primes.
├── **Steps:**
1. Choose two primes p, q
2. Compute n = p × q
3. Compute φ(n) = (p-1)(q-1)
4. Choose e such that gcd(e, φ(n)) = 1 (public key)
5. Find d such that e × d ≡ 1 mod φ(n) (private key)
6. Encryption: C = M^e mod n
7. Decryption: M = C^d mod n

├── **Example (N=119, E=5, D=77, M=6):**
- C = 6⁵ mod 119 = 41

├── **One-line Exam Answer:** RSA is an asymmetric encryption algorithm using public key (e,n) for encryption and private key (d,n) for decryption.

---

## 📌 4.11 Digital Signature
├── **Definition:** Cryptographic technique providing authentication, integrity, and non-repudiation.
├── **Process:**
1. Sender hashes message → encrypts hash with private key → digital signature
2. Receiver decrypts signature with sender's public key → recovers hash
3. Compares with computed hash; if match → valid
├── **One-line Exam Answer:** Digital signature is encrypted hash (using sender's private key) that authenticates origin and ensures integrity.

---

## 📌 4.12 Firewall
├── **Definition:** Hardware/software that filters network traffic between trusted and untrusted networks.
├── **Types:**
1. **Packet Filter** – inspects headers (IP/port/protocol) at L3
2. **Stateful Inspection** – tracks connection state
3. **Application/Proxy Gateway** – inspects content at L7
4. **Next-Gen Firewall** – combines all + IDS/IPS
├── **One-line Exam Answer:** A firewall is a network security device that filters traffic based on rules to protect internal networks from external threats.

---

# 🟪 UNIT – V: APPLICATION LAYER

## 📌 5.1 DNS (Domain Name System)
├── **Definition:** Hierarchical, distributed database that translates domain names (google.com) to IP addresses.
├── **Key Points:**
- Uses **UDP port 53** (TCP for zone transfers)
- Hierarchy: Root → TLD → Authoritative
- Types of records: **A** (IPv4), **AAAA** (IPv6), **MX** (mail), **CNAME** (alias), **NS** (name server), **PTR** (reverse)
- Resolution: Iterative or Recursive

├── **Hierarchy Diagram:**
```
        [Root]
        /  |  \
    .com  .org  .in
     |     |     |
  google  wiki  iitb
     |
    www
```
├── **One-line Exam Answer:** DNS is a hierarchical distributed naming system that translates domain names to IP addresses using UDP port 53.

---

## 📌 5.2 HTTP (HyperText Transfer Protocol)
├── **Definition:** Application-layer protocol for distributed, collaborative, hypermedia information systems (Web).
├── **Features:**
- **Port 80** (HTTP), **Port 443** (HTTPS)
- Stateless
- Request-Response based
- Uses TCP

├── **HTTP Methods:** GET, POST, PUT, DELETE, HEAD, OPTIONS, TRACE, CONNECT
├── **Status Codes:** 1xx (info), 2xx (success), 3xx (redirect), 4xx (client error), 5xx (server error)
├── **One-line Exam Answer:** HTTP is a stateless, request-response application-layer protocol on TCP port 80 used for transferring web resources.

---

## 📌 5.3 SMTP / Email
├── **Definition:** Push protocol used to send email between mail servers.
├── **Email Components:**
- **MUA** (Mail User Agent) – client (Outlook, Gmail)
- **MTA** (Mail Transfer Agent) – server (sendmail, postfix)
- **MDA** (Mail Delivery Agent) – delivers to user mailbox

├── **Protocols:**
- **SMTP** (port 25/587) – sending
- **POP3** (port 110) – downloading
- **IMAP** (port 143) – server-stored access

├── **SMTP Commands:** HELO/EHLO, MAIL FROM, RCPT TO, DATA, RSET, VRFY, NOOP, QUIT
├── **One-line Exam Answer:** SMTP is the email-sending protocol on TCP port 25 using text commands like HELO, MAIL FROM, RCPT TO, DATA, QUIT.

---

## 📌 5.4 FTP (File Transfer Protocol)
├── **Definition:** Application protocol for transferring files between hosts.
├── **Key Points:**
- Uses **two TCP connections**:
  - **Port 21** – Control (commands)
  - **Port 20** – Data (file transfer)
- **Out-of-band** control (commands separate from data)
- Two modes: ASCII / Binary
- Active vs Passive mode

├── **Common commands:** USER, PASS, LIST, RETR (download), STOR (upload), QUIT
├── **One-line Exam Answer:** FTP is a TCP-based file transfer protocol using two connections — control (port 21) and data (port 20).

---

## 📌 5.5 TFTP (Trivial FTP)
├── **Definition:** Simple, lightweight version of FTP using UDP.
├── **Features:**
- **UDP port 69**
- No authentication
- Used for: bootstrapping, firmware updates, embedded devices
- 5 message types: RRQ, WRQ, DATA, ACK, ERROR
├── **One-line Exam Answer:** TFTP is a simplified UDP-based file transfer protocol on port 69 with no authentication, used for bootstrapping.

---

## 📌 5.6 WWW (World Wide Web)
├── **Definition:** A global hypertext system of interlinked documents accessed via HTTP.
├── **Components:**
- **Web Browser** (Chrome, Firefox)
- **Web Server** (Apache, Nginx)
- **HTML/CSS/JS** – page languages
- **URL** – Uniform Resource Locator
- **HTTP/HTTPS** – transport
├── **One-line Exam Answer:** WWW is a hypertext system of linked web pages accessed via browsers using HTTP over the Internet.

---

## 📌 5.7 Hyperlinks & Hypermedia
├── **Hyperlink:** A clickable reference within a hypertext document, linking to another resource (`<a href="url">`)
├── **Hypermedia:** Hypertext + multimedia (images, audio, video, animations) — superset of hypertext
├── **One-line Exam Answer:** Hyperlinks are clickable references; hypermedia extends hypertext by including multimedia (images, audio, video).

---

## 📌 5.8 Proxy Server
├── **Definition:** Intermediate server between client and destination server.
├── **Functions:**
- Caching (improves speed)
- Filtering (blocks unwanted content)
- Anonymity (hides client IP)
- Logging
- Load balancing (reverse proxy)
├── **Types:** Forward proxy, Reverse proxy, Open proxy, Transparent proxy
├── **One-line Exam Answer:** A proxy server is an intermediate server providing caching, filtering, anonymity, and load-balancing services.

---

## 📌 5.9 Web Server
├── **Definition:** Server software/hardware that hosts and delivers web content (HTML, images) over HTTP/HTTPS.
├── **Examples:** Apache, Nginx, IIS, LiteSpeed
├── **Ports:** 80 (HTTP), 443 (HTTPS)
├── **One-line Exam Answer:** A web server hosts websites and serves content to clients via HTTP on port 80 / HTTPS on port 443.

---

## 📌 5.10 Active vs Dynamic Web Pages
| Feature | Active | Dynamic |
|---------|--------|---------|
| **Execution** | Client-side (browser) | Server-side |
| **Tools** | JavaScript, applets | PHP, ASP, JSP |
| **Server load** | Low | High |
| **Example** | Form validation | Product page from DB |

├── **One-line Exam Answer:** Active pages run scripts in the browser (JS); Dynamic pages are generated on-the-fly by server-side code accessing a database.

---

# END OF SYLLABUS NOTES (UNITS 1-5)
