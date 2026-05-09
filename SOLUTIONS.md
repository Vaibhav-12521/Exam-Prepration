# DATA COMMUNICATION & COMPUTER NETWORKS – PROBLEM SET SOLUTIONS
**Course:** BCA / B.Sc(IT) | **Subject Code:** US6001 | **Semester:** VI

---

## ====== UNIT – I (Problem Set I) – Introduction to Networks ======

### Q1. Consequences of connection failure (5 devices each)

**a) Mesh Topology**
- Total links = n(n-1)/2 = 5(4)/2 = **10 links**
- If ONE link fails → traffic is rerouted through other paths
- **No service disruption** (high fault tolerance)

**b) Star Topology** (5 devices + hub)
- If a device-to-hub link fails → only that device disconnects, rest works
- If hub fails → **entire network down**

**c) Bus Topology**
- If a tap (drop line) fails → only that one device disconnects
- If main backbone breaks → network splits into two non-functional halves

**d) Ring Topology**
- One link/device failure → **entire unidirectional ring fails**
- Dual-ring can self-heal

**Exam Tip:** Always mention number of links, single point of failure, and fault tolerance level for each topology.

---

### Q2. Propagation Time & Transmission Time

**Given:** Message = 2.5 KB, Bandwidth = 1 Gbps, Distance = 12,000 km, Speed = 2.4 × 10⁸ m/s

**Step 1 – Convert units:**
- Message = 2.5 × 1024 × 8 = 20,480 bits ≈ **20,000 bits** (using 2.5 KB ≈ 2500 B)
- Distance = 12,000 km = 1.2 × 10⁷ m
- Bandwidth = 10⁹ bps

**Step 2 – Propagation Time:**
T_prop = Distance / Speed = (1.2 × 10⁷) / (2.4 × 10⁸) = **0.05 s = 50 ms**

**Step 3 – Transmission Time:**
T_trans = Message size / Bandwidth = 20,000 / 10⁹ = **2 × 10⁻⁵ s = 20 μs**

**Conclusion:** Propagation time (50 ms) >> Transmission time (20 μs). For short messages over long distances, propagation delay dominates.

**Exam Tip:** Always convert KB → bits (×8 ×1000 or ×1024) and km → m before plugging in.

---

### Q3. Channel Capacity (Noiseless Channel, B=4 kHz, L=4)

**Formula (Nyquist):** C = 2 × B × log₂(L)

**Substituting:**
C = 2 × 4000 × log₂(4)
C = 8000 × 2
C = **16,000 bps = 16 kbps**

**Exam Tip:** For noiseless → use Nyquist; for noisy → use Shannon (C = B × log₂(1+SNR)).

---

### Q4. Twisted Pair vs Coaxial vs Optical Fiber

| Feature | Twisted Pair | Coaxial Cable | Optical Fiber |
|---------|--------------|---------------|---------------|
| **Cost** | Cheapest | Moderate | Most expensive |
| **Bandwidth** | Up to 100 Mbps | Up to 1 Gbps | THz (very high) |
| **Distance** | ~100 m | ~500 m | Up to 100 km |
| **EMI** | Highly susceptible | Moderate | Immune |
| **Signal** | Electrical | Electrical | Light |
| **Installation** | Easy | Moderate | Difficult |
| **Use** | LAN, Telephone | TV, older LAN | Backbone, Internet |

**Exam Tip:** Tabulate cost, bandwidth, distance, EMI immunity. Mention an example use of each.

---

### Q5. Packet/Frame Contents at each Hop

**Setup:** A(40) — LAN1 — R1(B/42, C/82) — LAN2 — D(80)
- Logical (IP) addresses: A and D (don't change)
- Physical (MAC) addresses: 40, 42, 82, 80

**HOP 1 (A → R1 across LAN1):**
- **Network layer (Packet):** Source = A, Destination = D
- **Data link (Frame):** Source MAC = 40, Destination MAC = 42

**HOP 2 (R1 → D across LAN2):**
- **Network layer (Packet):** Source = A, Destination = D *(unchanged)*
- **Data link (Frame):** Source MAC = 82, Destination MAC = 80

**Key insight:** IP addresses remain constant end-to-end; MAC addresses change at every hop.

**Exam Tip:** Draw a 2-row table for each hop. Examiner looks for unchanged IPs vs changing MACs.

---

### Q6. Presentation Layer Duties in Internet Model

In the **TCP/IP (Internet) model**, there is no separate Presentation Layer.
The duties of **translation, encryption, and compression** are handled by the **Application Layer**.

**Reason:** The Internet model collapses OSI's session, presentation, and application layers into one Application Layer. Programs (browsers, email clients) handle these duties internally using protocols like SSL/TLS (encryption), MIME (translation), and gzip (compression).

**Exam Tip:** Mention that TCP/IP has only 4/5 layers and clearly state Application Layer handles these.

---

### Q7. Corrupted Logical Destination Address

**What happens:**
1. The router uses the corrupted IP to look up the routing table.
2. If no matching route → router drops packet, may send **ICMP Destination Unreachable** to source.
3. If wrong but valid IP → packet reaches the wrong host (silently dropped if port not listening).
4. If corrupted IP doesn't exist anywhere → packet wanders till **TTL = 0** → router sends **ICMP Time Exceeded**.

**How source is informed:** Through **ICMP error messages** sent back to source's IP. However, if source IP is also corrupted, source cannot be informed.

**Exam Tip:** Mention ICMP types: Destination Unreachable, Time Exceeded.

---

### Q8. Two Computers + Ethernet Hub at Home → LAN/MAN/WAN?

**Answer:** It is a **LAN (Local Area Network)**.

**Reasons:**
- Geographic scope = single home (limited distance)
- Owned by one organization/person
- Uses Ethernet technology (a LAN technology)
- High data rate, low cost
- LAN covers a building/room; MAN covers a city; WAN covers countries

**Exam Tip:** Always justify by mentioning geographical scope and ownership.

---

### Q9. Two Acknowledgement Strategies

**Strategy 1 – Per-packet ACK (no whole-file ACK):**
- ✅ **Pros:** Quick error detection, retransmit only lost packet, good for unreliable channels
- ❌ **Cons:** High ACK overhead, lots of small messages
- ⚠️ **Risk:** Last packet's ACK may be lost; sender thinks complete but file may be incomplete

**Strategy 2 – Single whole-file ACK:**
- ✅ **Pros:** Less ACK overhead, simpler control
- ❌ **Cons:** If single bit error → must retransmit entire file (wasteful for big files)
- ⚠️ **Risk:** Bad on unreliable network (huge retransmissions)

**Best Practice:** Combine both — packet-level ACKs for reliability + final ACK for completion confirmation (this is what TCP+application does).

**Exam Tip:** Discuss bandwidth efficiency, error handling, and reliability for each.

---

### Q10. Image Transmission Time

**Given:** 1920 × 1280 pixels, 5 bytes/pixel, 56 kbps modem

**Step 1 – Calculate image size:**
Total pixels = 1920 × 1280 = 2,457,600 pixels
Total bytes = 2,457,600 × 5 = **12,288,000 bytes**
Total bits = 12,288,000 × 8 = **98,304,000 bits**

**Step 2 – Calculate transmission time:**
Time = Total bits / Bandwidth = 98,304,000 / 56,000
Time = **1755.4 seconds ≈ 29.26 minutes ≈ 29 min 15 sec**

**Exam Tip:** Be careful – "5 bytes/pixel" not bits. Convert bytes → bits before dividing by bps.

---

## ====== UNIT – II (Problem Set II) – Data Link Layer ======

### Q1. Services Provided by Data Link Layer

1. **Framing** – divides bit stream into frames
2. **Physical (MAC) Addressing** – adds source/destination MAC
3. **Flow Control** – prevents fast sender from overwhelming slow receiver
4. **Error Control** – detects/corrects errors using CRC, checksums, ARQ
5. **Access Control** – decides which device can use shared channel (CSMA, polling)
6. **Reliable Delivery** – ensures frames arrive (Stop-and-Wait, Go-Back-N)

**Exam Tip:** Memorize these 6 services as a list. Mention examples.

---

### Q2. Hamming Distance

**Definition:** Number of bit positions in which two equal-length binary strings differ.

| Code Words | Comparison | Hamming Distance |
|-----------|------------|------------------|
| a) d(10000, 00000) | Position 1 differs | **1** |
| b) d(10101, 10000) | Positions 3,5 differ | **2** |
| c) d(11111, 11111) | None differ | **0** |
| d) d(000, 000) | None differ | **0** |

**Exam Tip:** Use XOR, then count number of 1's in result.

---

### Q3. Even Parity Bits

**Rule:** Even parity bit = 0 if number of 1's is already even; 1 if odd.

| Data | Count of 1's | Parity Bit |
|------|--------------|------------|
| a) 1001011 | 4 (even) | **0** |
| b) 0001100 | 2 (even) | **0** |
| c) 1000000 | 1 (odd) | **1** |
| d) 1110111 | 6 (even) | **0** |

**Exam Tip:** State the rule first, then count carefully.

---

### Q4. 7-bit Hamming Code for 1011 (Even Parity)

**Bit positions:** P1 P2 D1 P4 D2 D3 D4 → 1 2 3 4 5 6 7
**Data 1011:** D1=1, D2=0, D3=1, D4=1

**Parity bit calculations:**
- **P1** covers positions 1,3,5,7 → P1 ⊕ 1 ⊕ 0 ⊕ 1 = 0 → **P1 = 0**
- **P2** covers positions 2,3,6,7 → P2 ⊕ 1 ⊕ 1 ⊕ 1 = 0 → **P2 = 1**
- **P4** covers positions 4,5,6,7 → P4 ⊕ 0 ⊕ 1 ⊕ 1 = 0 → **P4 = 0**

**Hamming codeword = 0 1 1 0 0 1 1 = 0110011**

**Now correct received codeword 1011011:**

| Position | 1 | 2 | 3 | 4 | 5 | 6 | 7 |
|---------|---|---|---|---|---|---|---|
| Received bit | 1 | 0 | 1 | 1 | 0 | 1 | 1 |

- **C1** (1,3,5,7) = 1⊕1⊕0⊕1 = **1**
- **C2** (2,3,6,7) = 0⊕1⊕1⊕1 = **1**
- **C4** (4,5,6,7) = 1⊕0⊕1⊕1 = **1**

**Syndrome = C4C2C1 = 111 = 7** → Error in **bit 7**

**Corrected codeword:** Flip bit 7 → **1011010**

**Exam Tip:** Always show parity check matrix and syndrome calculation.

---

### Q5. Packet Switching vs Circuit Switching

| Feature | Circuit Switching | Packet Switching |
|---------|-------------------|------------------|
| **Path** | Dedicated end-to-end | No dedicated path |
| **Setup** | Required (3 phases) | Not required |
| **Phases** | Setup, Transfer, Teardown | Just Transfer |
| **Delay** | High setup, then minimal | Variable per packet |
| **Bandwidth** | Reserved (wasted if idle) | Shared (efficient) |
| **Reliability** | More reliable | Less reliable |
| **Example** | Telephone network | Internet |

**Delay comparison:**
- **Circuit:** Total = setup delay + (msg/B) + propagation
- **Packet:** Total = N × (queuing + processing + transmission + propagation)

**Diagram (Circuit):** Sender ---[fixed dedicated path]--- Receiver
**Diagram (Packet):** Each packet may take different routes through routers

**Exam Tip:** Draw two diagrams. Mention circuit switching wastes bandwidth.

---

### Q6. CRC for 10011101 with Generator x³+1 (= 1001)

**Step 1 – Append 3 zeros (degree of generator):**
Augmented data: **10011101000**

**Step 2 – Divide by 1001 using XOR:**
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

**Step 3 – Transmitted bit string:**
**10011101 + 100 = 10011101100**

**Step 4 – Suppose 3rd bit is inverted → received: 10111101100**

**Receiver divides 10111101100 by 1001:**
```
  10111101100
⊕ 10010000000
  -----------
  00101101100
⊕ 00100100000   (XOR at position 2)
  -----------
  00001001100
⊕ 00001001000   (XOR at position 4)
  -----------
  00000000100   ← Remainder = 100 ≠ 0
```

**Conclusion:** Remainder is non-zero ⇒ **error detected** ✓

**Exam Tip:** Always show append-zeros, division, and remainder check separately.

---

### Q7. CSMA/CD vs CSMA/CA (with Flowchart)

| Feature | CSMA/CD | CSMA/CA |
|---------|---------|---------|
| **Full Form** | Carrier Sense Multiple Access / Collision Detection | Carrier Sense Multiple Access / Collision Avoidance |
| **Used in** | Wired (Ethernet 802.3) | Wireless (Wi-Fi 802.11) |
| **Approach** | Detect collision after it happens | Avoid collision before it happens |
| **Mechanism** | Listen → Transmit → Detect → Abort → Backoff | Listen → IFS Wait → Backoff → RTS/CTS → Transmit → ACK |
| **Efficiency** | Higher (in wired) | Lower (overhead from RTS/CTS) |
| **Why different?** | Wired can detect collisions easily | Wireless cannot detect collisions (hidden node) |

**CSMA/CD Flowchart:**
```
START → Sense Channel → Idle?
  No → Wait → Sense again
  Yes → Transmit → Collision detected?
    Yes → Send Jam Signal → Backoff (exponential) → Retry
    No → Transmission Successful
```

**CSMA/CA Flowchart:**
```
START → Sense Channel → Idle for IFS time?
  No → Wait
  Yes → Random Backoff → Send RTS → Receive CTS?
    Yes → Send Data → Wait ACK → Successful
    No → Backoff and Retry
```

**Exam Tip:** Draw both flowcharts. Mention "wireless can't detect collisions" reason.

---

### Q8. Checksum (32-bit data: 10011001 11100010 00100100 10000100)

**Step 1 – Split into 8-bit segments:**
- A = 10011001 (153)
- B = 11100010 (226)
- C = 00100100 (36)
- D = 10000100 (132)

**Step 2 – 1's complement addition (Sender side):**
```
A + B = 10011001 + 11100010 = 1 01111011
  carry 1 → 01111011 + 1 = 01111100  (124)

(A+B) + C = 01111100 + 00100100 = 10100000  (no carry)

(A+B+C) + D = 10100000 + 10000100 = 1 00100100
  carry 1 → 00100100 + 1 = 00100101  (37)

Sum = 00100101
Checksum = 1's complement = 11011010   ← SENDER sends this
```

**Step 3 – Receiver side:**
Receiver adds all segments + checksum.
00100101 + 11011010 = **11111111**
1's complement of 11111111 = **00000000** → All zeros = **No error** ✓

**Exam Tip:** Show wrap-around carry addition step clearly.

---

### Q9. Go-Back-N ARQ Working Mechanism

**Concept:** Sliding window protocol where sender can send up to N unacknowledged frames. If a frame is lost or NACKed, sender retransmits that frame and ALL subsequent frames.

**Rules:**
- Sender window size = N (e.g., 4)
- Receiver window size = 1 (only accepts in-order frames)
- Cumulative ACK (ACKn means all frames up to n-1 received correctly)
- On timeout → resend all N pending frames

**Diagram:**
```
Sender:    F0  F1  F2  F3  F4  F5  ...
              ↓   ↓   X   ↓   ↓
Receiver:  F0✓ F1✓     F3✗ F4✗     ← discards out-of-order
              ACK1 ACK2     (still ACK2)
                        TIMEOUT
Sender:    F2  F3  F4  F5  (retransmit all)
```

**Drawback:** Wastes bandwidth on retransmitting already-received frames.

**Exam Tip:** Draw timeline diagram with frames, ACKs, timeout, and retransmission clearly.

---

### Q10. Framing & its Methods

**Definition:** Framing is the process of packaging the bit stream from network layer into discrete units called **frames** at the data link layer, with clear start/end markers.

**Methods:**

1. **Character (Byte) Count:** First field tells number of characters in frame.
   - Issue: If count corrupted, framing is lost permanently.

2. **Flag Bytes with Byte Stuffing:** Each frame starts/ends with special flag byte (e.g., 01111110). If flag appears in data, an escape character (ESC) is stuffed before it.

3. **Flag Bits with Bit Stuffing:** Frame delimited by bit pattern 01111110. After every 5 consecutive 1's in data, a 0 is stuffed.

4. **Physical Layer Coding Violations:** Use invalid signal patterns (e.g., HHH, LLL) as frame boundaries — works only when codes have unused bit combinations.

**Exam Tip:** Give 1-line example for each method. Examiner loves bit-stuffing example.

---

## ====== UNIT – III (Problem Set III) – LLC / MAC ======

### Q1. "Go-Back-N ARQ is more popular than Stop-and-Wait ARQ" – Comment

**Yes, this is true** because:

| Stop-and-Wait | Go-Back-N |
|--------------|-----------|
| Only 1 unacknowledged frame at a time | Up to N frames in transit |
| Very low channel utilization on long links | High channel utilization |
| Bandwidth-delay product wastage | Pipelined transmission |
| Simple but slow | More complex but faster |

**Reason for popularity:** On modern high-speed networks with high bandwidth-delay product, Stop-and-Wait wastes bandwidth waiting for ACKs. Go-Back-N pipelines transmission, achieving much higher throughput. It's also simpler than Selective Repeat (no buffering at receiver).

**Exam Tip:** Quote efficiency formula: η = N / (1+2a) where a = T_prop/T_trans.

---

### Q2. Pure ALOHA vs Slotted ALOHA at Low Load

**Answer:** **Pure ALOHA has LESS delay at low load.**

**Reason:**
- In **slotted ALOHA**, even if channel is idle, a station must wait until the next time slot boundary to start transmitting.
- In **pure ALOHA**, a station can transmit immediately when it has data.
- At low load, collisions are rare in both, so pure ALOHA's immediate-send advantage dominates.

**Trade-off:** At HIGH load, slotted ALOHA performs better (max efficiency 36.8% vs 18.4% for pure).

**Exam Tip:** Mention efficiency: pure 18.4%, slotted 36.8%. State immediate vs slot-aligned transmission.

---

### Q3. Unicast vs Multicast vs Broadcast

| Type | Meaning | Example | Address |
|------|---------|---------|---------|
| **Unicast** | One sender → One receiver | Browsing a website | Class A/B/C IP (e.g., 192.168.1.10) |
| **Multicast** | One sender → Group of receivers | Live video streaming | Class D IP (224.0.0.0 – 239.255.255.255) |
| **Broadcast** | One sender → All receivers in network | ARP request | 255.255.255.255 (limited) or subnet broadcast |

**Exam Tip:** Memorize Class D for multicast and 255.255.255.255 for broadcast.

---

### Q4. Networks and Hosts in IP Address Classes

| Class | Range | Default Mask | # Networks | # Hosts/Network |
|-------|-------|--------------|------------|-----------------|
| **A** | 0.0.0.0 – 127.255.255.255 | /8 (255.0.0.0) | 2⁷ = **128** (126 usable) | 2²⁴ – 2 = **16,777,214** |
| **B** | 128.0.0.0 – 191.255.255.255 | /16 (255.255.0.0) | 2¹⁴ = **16,384** | 2¹⁶ – 2 = **65,534** |
| **C** | 192.0.0.0 – 223.255.255.255 | /24 (255.255.255.0) | 2²¹ = **2,097,152** | 2⁸ – 2 = **254** |
| **D** | 224.0.0.0 – 239.255.255.255 | – | Multicast | – |
| **E** | 240.0.0.0 – 255.255.255.255 | – | Reserved | – |

**Note:** -2 because network address (all 0s) and broadcast address (all 1s) cannot be assigned to hosts.

**Exam Tip:** Memorize first octet ranges and the formula 2ⁿ − 2.

---

### Q5. ICMP and its Types

**ICMP = Internet Control Message Protocol**
- Network-layer protocol used for **error reporting and diagnostics** in IP networks
- Encapsulated within IP datagrams (Protocol number 1)

**Types of ICMP messages:**

**A. Error-reporting messages:**
1. **Destination Unreachable** (Type 3) – host/network unreachable
2. **Source Quench** (Type 4) – congestion (deprecated)
3. **Time Exceeded** (Type 11) – TTL expired
4. **Parameter Problem** (Type 12) – bad header
5. **Redirection** (Type 5) – better route available

**B. Query messages:**
6. **Echo Request/Reply** (Type 8/0) – used by **ping**
7. **Timestamp Request/Reply** (Type 13/14)
8. **Address Mask Request/Reply** (Type 17/18)
9. **Router Solicitation/Advertisement** (Type 10/9)

**Exam Tip:** Always group into "Error" and "Query" with examples (ping is Echo; traceroute uses Time Exceeded).

---

### Q6. Subnets/Hosts for Mask 255.255.255.224

**Mask in binary:** 11111111.11111111.11111111.**111**00000

- Subnet bits = **3** (the borrowed bits in last octet)
- Host bits = **5**

**Number of subnets** = 2³ = **8**
**Number of usable hosts per subnet** = 2⁵ – 2 = **30**

**Subnet ranges (Class C example):**
- 192.168.1.0/27, 192.168.1.32/27, 192.168.1.64/27, ..., 192.168.1.224/27

**Exam Tip:** Remember the formula: hosts = 2^h - 2 (always subtract 2).

---

### Q7. CSMA/CD vs CSMA/CA (Same as Unit II, Q7)

Refer to Unit II, Q7 for detailed comparison and flowcharts.

---

### Q8. Maximum Hosts for 255.255.240.0 + CIDR Explanation

**Mask in binary:** 11111111.11111111.**1111**0000.00000000

- Network bits = 16 + 4 = **20**
- Host bits = **12**

**Maximum hosts** = 2¹² – 2 = **4094 hosts**

---

**CIDR (Classless Inter-Domain Routing):**

- Replaces the rigid Class A/B/C system
- Uses **prefix length notation:** IP_address/n, where n = number of network bits (e.g., 192.168.1.0/24)
- Allows **VLSM (Variable-Length Subnet Mask)** – different subnets can have different sizes
- Enables **route aggregation (supernetting)** – multiple networks combined into one route
- Solves IPv4 address exhaustion by efficient allocation
- Mask 255.255.240.0 in CIDR = **/20**

**Exam Tip:** Mention "/n" notation, VLSM, and supernetting clearly.

---

### Q9. Selective Repeat ARQ

**Concept:** Sender can send N unacknowledged frames. Receiver buffers out-of-order frames and only the LOST frame is retransmitted (not all subsequent ones).

**Rules:**
- Sender window size = N
- Receiver window size = N (same as sender)
- Each frame independently acknowledged
- Receiver can accept frames out of order
- Only the missing frame is retransmitted on timeout/NACK

**Diagram:**
```
Sender:    F0  F1  F2  F3  F4
              ↓   ↓   X   ↓   ↓
Receiver:  F0✓ F1✓     F3 buf F4 buf
              ACK0 ACK1   ACK3  ACK4
                       TIMEOUT for F2
Sender:    F2  (only F2 retransmitted)
Receiver: F2✓ → delivers F2,F3,F4 in order
```

**Advantage:** Bandwidth efficient (only lost frame retransmitted)
**Disadvantage:** Receiver needs buffer, more complex logic

**Exam Tip:** Compare with Go-Back-N — only the lost frame is retransmitted in SR.

---

### Q10. IPv4 Header Format

**Total header size:** 20–60 bytes (variable due to Options)

```
0       4       8              16                            31
+-------+-------+---------------+-----------------------------+
|Version| IHL   | Type of Service|       Total Length         |
+-------+-------+---------------+-----------------------------+
|       Identification          |Flags|   Fragment Offset     |
+---------------+---------------+-----------------------------+
|     TTL       |   Protocol    |       Header Checksum       |
+---------------+---------------+-----------------------------+
|                       Source IP Address                      |
+--------------------------------------------------------------+
|                    Destination IP Address                    |
+--------------------------------------------------------------+
|                  Options (if any) + Padding                  |
+--------------------------------------------------------------+
```

| Field | Size | Role |
|-------|------|------|
| **Version** | 4 bits | IP version (4 for IPv4) |
| **IHL** | 4 bits | Header length in 32-bit words (5–15) |
| **TOS / DSCP** | 8 bits | Type of service / QoS priority |
| **Total Length** | 16 bits | Datagram total size (max 65535) |
| **Identification** | 16 bits | Unique ID for fragmentation |
| **Flags** | 3 bits | DF (Don't Fragment), MF (More Fragments) |
| **Fragment Offset** | 13 bits | Position of fragment in original |
| **TTL** | 8 bits | Hops remaining (decremented by router) |
| **Protocol** | 8 bits | Upper layer (TCP=6, UDP=17, ICMP=1) |
| **Header Checksum** | 16 bits | Header error detection |
| **Source IP** | 32 bits | Sender's IP |
| **Destination IP** | 32 bits | Receiver's IP |
| **Options** | 0–40 bytes | Source routing, timestamp, etc. |

**Exam Tip:** Draw the full diagram with bit positions. Memorize protocol numbers.

---

## ====== UNIT – IV (Problem Set IV) – Network/Transport Layer ======

### Q1. TCP Header vs UDP Header

**TCP Header (20–60 bytes):**
```
0           16            31
+-----------+-------------+
| Source    | Destination |
| Port      | Port        |
+-------------------------+
|     Sequence Number     |
+-------------------------+
|  Acknowledgment Number  |
+-----+----+--------+-----+
|HLen |Res |Flags   |Window|
+-----+----+--------+-----+
| Checksum  | Urgent Ptr  |
+-----------+-------------+
|     Options + Padding   |
+-------------------------+
```

**UDP Header (8 bytes):**
```
0        16        31
+--------+----------+
|Source  |Dest Port |
|Port    |          |
+--------+----------+
|Length  |Checksum  |
+--------+----------+
```

| Field | TCP | UDP | Reason TCP needs it |
|-------|-----|-----|---------------------|
| Source/Dest Port | ✓ | ✓ | Process identification |
| Sequence Number | ✓ | ✗ | Ordered delivery |
| ACK Number | ✓ | ✗ | Reliable delivery |
| HLen | ✓ | ✗ | Variable header due to options |
| Flags (URG/ACK/PSH/RST/SYN/FIN) | ✓ | ✗ | Connection control |
| Window Size | ✓ | ✗ | Flow control |
| Urgent Pointer | ✓ | ✗ | Out-of-band data |
| Options | ✓ | ✗ | MSS, scaling, SACK |

**Conclusion:** TCP has extra fields because it provides **reliable, ordered, flow-controlled, connection-oriented service**, while UDP is **unreliable, connectionless**.

**Exam Tip:** Always draw both headers side-by-side and explain "why TCP needs each missing field."

---

### Q2. Cryptography in Presentation Layer

**Need:** Cryptography ensures secure data transmission across networks. It provides:
1. **Confidentiality** – data hidden from unauthorized parties
2. **Integrity** – data not altered in transit
3. **Authentication** – verifying identity of sender
4. **Non-repudiation** – sender cannot deny sending

**Symmetric vs Asymmetric Key Cryptography:**

| Feature | Symmetric Key | Asymmetric Key |
|---------|---------------|----------------|
| **Keys** | Single shared secret key | Public + Private key pair |
| **Speed** | Fast | Slow |
| **Key Distribution** | Difficult (must share securely) | Easy (publish public key) |
| **Use Case** | Bulk data encryption | Digital signatures, key exchange |
| **Algorithms** | DES, 3DES, AES, Blowfish | RSA, DSA, ECC, Diffie-Hellman |
| **Key Length** | 56–256 bits | 1024–4096 bits |
| **Computational Cost** | Low | High |

**Exam Tip:** Mention example algorithms in each. State that real systems often combine both (TLS uses asymmetric for key exchange + symmetric for data).

---

### Q3. Digital Signature & Security Attacks

**Digital Signature:**
- Cryptographic technique providing **authentication, integrity, and non-repudiation**
- **Process:**
  1. Sender computes hash of message (e.g., SHA-256)
  2. Encrypts hash with **sender's private key** → digital signature
  3. Sends message + signature to receiver
  4. Receiver decrypts signature with **sender's public key** → recovers hash
  5. Receiver computes hash of message and compares
  6. If hashes match → signature valid

**Diagram:**
```
SENDER                              RECEIVER
Message → Hash → Sign(Private Key)  Signature → Verify(Public Key) → Hash
                                    Message → Hash → Compare
```

**Security Attacks:**

**Passive attacks** (only observation):
- **Eavesdropping** – reading packets in transit
- **Traffic analysis** – inferring info from patterns

**Active attacks** (modify/inject data):
- **Masquerade** – pretending to be someone else
- **Replay** – capturing and resending old valid messages
- **Modification** – altering messages
- **Denial of Service (DoS)** – overwhelming server

**Exam Tip:** Always classify attacks as passive vs active.

---

### Q4. RSA: N=119, E=5, D=77, Send Character F

**Step 1 – Convert character to number:**
F = 6 (assuming A=1, B=2,...,F=6)

**Step 2 – Encrypt: C = M^E mod N = 6⁵ mod 119**

Calculation:
- 6² = 36
- 6⁴ = 36² = 1296 mod 119 = 1296 − (10×119) = 1296 − 1190 = **106**
- 6⁵ = 6⁴ × 6 = 106 × 6 = 636 mod 119 = 636 − (5×119) = 636 − 595 = **41**

**Cipher text C = 41**

**Step 3 – Decrypt verification: M = C^D mod N = 41⁷⁷ mod 119**

Should give back **6** (Plain text).

**Exam Tip:** Show modular exponentiation clearly. State that public key (E,N) encrypts; private key (D,N) decrypts.

---

### Q5. Sockets and Socket Types

**Socket:** An endpoint of a two-way communication link between two processes over a network. Identified by **IP address + Port number**.

Format: `(IP, Port)` e.g., `(192.168.1.5, 8080)`

**Socket Types:**

1. **Stream Socket (SOCK_STREAM)** – uses TCP
   - Reliable, ordered, connection-oriented
   - Used by HTTP, FTP, SMTP, SSH

2. **Datagram Socket (SOCK_DGRAM)** – uses UDP
   - Unreliable, no order guarantee, connectionless
   - Used by DNS, DHCP, SNMP, video streaming

3. **Raw Socket (SOCK_RAW)** – direct access to network layer
   - Used to construct custom packets (e.g., ping, traceroute)

4. **Sequenced Packet Socket (SOCK_SEQPACKET)** – reliable + record boundaries (SCTP)

**Exam Tip:** Mention "IP+Port" as socket identifier. Pair each socket type with example application.

---

### Q6. Transport Service Primitives & Three-Way Handshake

**Transport Service Primitives:**
- **LISTEN** – server waits for incoming connection
- **CONNECT** – client initiates connection to server
- **SEND** – send data on established connection
- **RECEIVE** – receive data
- **DISCONNECT** – terminate connection

**Three-Way Handshake (TCP connection setup):**

```
Client                          Server
  |                               |
  |---- SYN, seq=x -------------->|     1. Client sends SYN
  |                               |
  |<--- SYN+ACK, seq=y, ack=x+1 --|     2. Server replies SYN-ACK
  |                               |
  |---- ACK, ack=y+1 ------------>|     3. Client sends ACK
  |                               |
  |<====== Established ==========>|
```

**Problem solved by 3-way handshake:**
- **Synchronization of sequence numbers** between client and server
- Prevents **old duplicate connection requests** from creating false connections
- Ensures both parties are **alive and ready** before data transfer

**Exam Tip:** Always draw the 3-way handshake with seq/ack numbers. State "synchronization of sequence numbers" as the main problem solved.

---

### Q7. QoS (Quality of Service) Parameters

**QoS** is a set of techniques to manage network resources to provide guaranteed performance.

**Four key parameters:**

1. **Reliability** – packets delivered without errors/loss
   - Measured by error rate, packet loss percentage
   - Important for: file transfer, email

2. **Delay (Latency)** – time taken to deliver packet
   - End-to-end delay = transmission + propagation + processing + queuing
   - Important for: VoIP, video calls (low delay required)

3. **Jitter** – variation in packet delay
   - Important for: real-time streaming, online gaming

4. **Bandwidth** – data transfer rate (bps)
   - Important for: HD video streaming, downloads

**Exam Tip:** Memorize 4 parameters: Reliability, Delay, Jitter, Bandwidth. Give 1 application requiring each.

---

### Q8. Firewall: Packet Filtering vs Proxy Server

**Firewall:** Hardware/software that monitors and controls incoming/outgoing network traffic based on security rules. It separates trusted internal network from untrusted external (Internet).

| Feature | Packet Filter Firewall | Proxy Server (Application Gateway) |
|---------|------------------------|-----------------------------------|
| **OSI Layer** | Network layer (Layer 3) | Application layer (Layer 7) |
| **Inspects** | Packet headers (IP, port, protocol) | Full message content (HTTP, FTP commands) |
| **Speed** | Very fast | Slower |
| **Security Level** | Basic | High |
| **Logging** | Minimal | Detailed |
| **Caching** | No | Yes (improves performance) |
| **User Authentication** | No | Yes |
| **Cost** | Low | High |
| **Stateful** | Stateless or stateful | Always stateful |
| **Example** | Cisco ACL, iptables | Squid, BlueCoat |

**Exam Tip:** Mention layer of operation, depth of inspection, and speed difference.

---

### Q9. Leaky Bucket Algorithm

**Purpose:** Traffic shaping algorithm that controls/smooths bursty traffic into a steady flow.

**Concept:**
- Imagine a **bucket with a small hole at the bottom**.
- Packets are **poured into the bucket** by the host.
- Water (data) **leaks out at a constant rate** through the hole.
- If the bucket **overflows** (full), incoming packets are **discarded**.

**Diagram:**
```
       Host (bursty input)
            ↓ ↓ ↓
         ┌─────────┐
         │ packets │  ← Bucket (FIFO queue)
         │         │
         │_________│
              |
              ↓ (constant rate)
        Network (smooth output)
```

**Working:**
- Input: bursty traffic at variable rate
- Bucket queue: holds packets up to its capacity
- Output: constant rate (e.g., 10 packets/sec)
- If bucket full → drop packet
- Output is smooth regardless of input burst

**Advantage:** Controls average rate and burst size, prevents network congestion.
**Disadvantage:** No flexibility for occasional bursts (Token Bucket allows this).

**Exam Tip:** Draw the bucket diagram. Mention output is **constant rate** regardless of input.

---

### Q10. ICMP & Types (Same as Unit III, Q5)

Refer to Unit III, Q5 for detailed ICMP message types.

---

## ====== UNIT – V (Problem Set V) – Application Layer ======

### Q1. Proxy Servers and Web Servers

**Web Server:**
- A server that hosts and delivers **web pages and resources** to clients via HTTP/HTTPS
- Stores HTML, CSS, JS, images, videos
- Listens on **Port 80 (HTTP)** or **Port 443 (HTTPS)**
- Examples: Apache, Nginx, IIS, LiteSpeed

**Proxy Server:**
- An intermediate server between client and the actual web server
- **Functions:**
  - **Caching** – stores frequently accessed pages locally
  - **Filtering** – blocks unwanted content (e.g., schools/offices)
  - **Anonymity** – hides client's IP from origin server
  - **Logging** – tracks user activity
  - **Load balancing** – distributes traffic
- **Forward proxy:** for clients (used by users to access internet)
- **Reverse proxy:** for servers (used by web servers to handle requests)

**Difference:**
| Web Server | Proxy Server |
|-----------|--------------|
| Origin of content | Intermediate |
| Hosts web pages | Forwards requests |
| Direct interaction | Indirect (via proxy) |

**Exam Tip:** Define each in 2 lines. Mention forward vs reverse proxy briefly.

---

### Q2. DNS – What if all DNS servers crashed?

**DNS (Domain Name System):**
- A hierarchical, distributed database that translates human-friendly **domain names** (e.g., google.com) to **IP addresses** (e.g., 142.250.190.46)
- Uses **UDP port 53** (TCP for zone transfers)

**Used for:**
- Resolving website URLs to IPs
- Email routing (MX records)
- Service discovery (SRV records)
- Reverse lookup (IP → name)

**If all DNS servers crashed:**
1. **No domain name resolution** – users typing URLs would get "Server not found" errors
2. **Only direct IP access works** – e.g., http://142.250.190.46 might still load Google
3. **Cached entries** continue working until **TTL expires** (minutes to hours)
4. **Email delivery fails** – SMTP needs MX record lookups
5. **Web apps using API hostnames break** – almost all modern apps depend on DNS
6. **Nearly the entire Internet becomes unusable** for end users

**Exam Tip:** State that DNS is the "phonebook of internet." List concrete consequences (websites, email, cached entries).

---

### Q3. HTTP vs SMTP

| Feature | HTTP | SMTP |
|---------|------|------|
| **Full Form** | HyperText Transfer Protocol | Simple Mail Transfer Protocol |
| **Purpose** | Transfer web pages | Transfer email between servers |
| **Type** | Pull protocol (client requests) | Push protocol (server pushes) |
| **Port** | 80 (HTTP), 443 (HTTPS) | 25, 465 (SMTPS), 587 (submission) |
| **Connection** | Request-Response over TCP | Persistent TCP connection |
| **Stateless?** | Stateless (each request independent) | Stateful (sequence of commands) |
| **Encoding** | Allows binary content | Originally 7-bit ASCII (uses MIME for binary) |
| **Direction** | Client ↔ Server | Server ↔ Server (mostly) |
| **Message format** | Headers + body | Headers + body |

**Similarity:** Both use TCP, both use ASCII command/response messages, both have headers + body structure.

**Exam Tip:** Use comparison table. Highlight pull vs push and port numbers.

---

### Q4. Hyperlinks and Hypermedia

**Hyperlinks:**
- Clickable references in a document that take user to another document/resource
- Implemented in HTML using `<a href="url">` tags
- Can point to: web pages, files, sections within a page, email addresses
- Example: `<a href="https://google.com">Click here</a>`

**Hypermedia:**
- Extension of hypertext that includes **multiple media types** linked together
- Combines: text, images, audio, video, animations, interactive elements
- The Web is a hypermedia system
- Example: A web page with embedded YouTube video, clickable images, and audio

**Difference:**
- **Hypertext** = text with hyperlinks (early web)
- **Hypermedia** = hypertext + images, audio, video, etc.
- Hypermedia ⊃ Hypertext (hypermedia is a superset)

**Exam Tip:** Define each in 2 lines. State "hypermedia is hypertext + multimedia."

---

### Q5. Hierarchy of Name Servers

DNS uses a **hierarchical, distributed structure** organized in tree-like form:

```
                    [Root DNS Servers]
                          |
        ┌────────────┬────┴────┬────────────┐
       [.com]      [.org]    [.edu]      [.in]    ← TLD servers
        |             |         |            |
   [google.com] [wikipedia]  [mit.edu]   [iitb.ac.in]  ← Authoritative servers
        |
   [www, mail, ...]   ← Hosts
```

**Levels:**
1. **Root DNS Servers** – 13 root servers (A through M) globally; handle TLD queries
2. **Top-Level Domain (TLD) Servers** – manage .com, .org, .net, country codes (.in, .uk, .jp)
3. **Authoritative DNS Servers** – contain actual IP records for specific domains
4. **Local (Recursive) DNS Servers** – run by ISPs/organizations; cache and resolve queries for users

**Resolution Process (Recursive query):**
```
Client → Local DNS → Root → TLD → Authoritative → returns IP
        (caches result for next time)
```

**Exam Tip:** Draw the inverted tree diagram. Mention 13 root servers and resolution sequence.

---

### Q6. Why FTP sends Control Information Out-of-Band?

**FTP uses TWO separate TCP connections:**
1. **Control connection** – Port 21 (commands like USER, PASS, GET, PUT)
2. **Data connection** – Port 20 (actual file transfer)

**"Out-of-band" means** control commands travel on a **different channel** than data, not multiplexed in the same stream.

**Reasons for this design:**

1. **Continuous control during transfer:** User can issue commands (e.g., ABORT) even while a file is being downloaded — data connection is busy with file, but control connection is free.

2. **Cleaner protocol design:** No need for special escape sequences to separate commands from data within a single channel.

3. **Multiple data transfers possible:** While file is being transferred, control connection can prepare the next transfer.

4. **Better error handling:** Control errors don't corrupt data and vice versa.

5. **Independent connection lifecycle:** Control connection persists for entire session; data connection opens/closes per transfer.

**Contrast:** HTTP and SMTP send commands and data on the **same connection** (in-band).

**Exam Tip:** Mention ports 20 and 21 and the ability to send ABORT during transfer.

---

### Q7. Types of HTTP Messages

HTTP messages are of **two types**: Request (client → server) and Response (server → client).

**A. HTTP Request Message:**
```
GET /index.html HTTP/1.1               ← Request line
Host: www.example.com                  ← Headers
User-Agent: Mozilla/5.0
Accept: text/html
                                       ← Blank line
[optional body for POST/PUT]           ← Body
```

**Common Request Methods:**
- **GET** – retrieve resource
- **POST** – submit data
- **PUT** – upload/update resource
- **DELETE** – remove resource
- **HEAD** – like GET but only headers (no body)
- **OPTIONS** – ask server what methods are allowed
- **TRACE** – diagnostic loopback
- **CONNECT** – tunnel (used for HTTPS through proxy)

**B. HTTP Response Message:**
```
HTTP/1.1 200 OK                        ← Status line
Content-Type: text/html                ← Headers
Content-Length: 1234
Date: Mon, 08 May 2026 ...
                                       ← Blank line
<html>...</html>                       ← Body (web content)
```

**HTTP Status Codes (Response):**
- **1xx** – Informational (e.g., 100 Continue)
- **2xx** – Success (200 OK, 201 Created)
- **3xx** – Redirection (301 Moved, 304 Not Modified)
- **4xx** – Client Error (400 Bad Request, 404 Not Found, 401 Unauthorized)
- **5xx** – Server Error (500 Internal Error, 503 Service Unavailable)

**Exam Tip:** Show both Request and Response formats with example. Memorize 200, 301, 404, 500.

---

### Q8. SMTP Commands

**SMTP** (Simple Mail Transfer Protocol) uses simple text-based commands. Each command is followed by a 3-digit response code.

| Command | Purpose |
|---------|---------|
| **HELO / EHLO** | Identify client to server (EHLO for extended SMTP) |
| **MAIL FROM:** | Specify sender's email address |
| **RCPT TO:** | Specify recipient's email address |
| **DATA** | Begin message body (terminated by `.` on its own line) |
| **RSET** | Reset/abort current transaction |
| **VRFY** | Verify if email user exists |
| **EXPN** | Expand mailing list |
| **NOOP** | No operation (keep connection alive) |
| **QUIT** | End SMTP session |
| **HELP** | Get command help |

**Sample SMTP session:**
```
S: 220 mail.example.com SMTP Ready
C: HELO client.com
S: 250 Hello client.com
C: MAIL FROM:<alice@a.com>
S: 250 OK
C: RCPT TO:<bob@b.com>
S: 250 OK
C: DATA
S: 354 End data with <CR><LF>.<CR><LF>
C: Subject: Hello
C: 
C: Hi Bob!
C: .
S: 250 Message accepted
C: QUIT
S: 221 Bye
```

**Exam Tip:** Memorize order: HELO → MAIL FROM → RCPT TO → DATA → QUIT. Show example session.

---

### Q9. Active vs Dynamic Web Pages

| Feature | Active Web Page | Dynamic Web Page |
|---------|-----------------|-------------------|
| **Where executed** | At **client side** (browser) | At **server side** |
| **Technology** | JavaScript, ActiveX, applets | PHP, ASP.NET, JSP, Python (Django/Flask) |
| **Content generation** | Code runs in browser to update DOM | HTML generated freshly per request |
| **Server load** | Low (client does work) | High (server processes every request) |
| **User interaction** | Real-time (no reload needed) | Refresh required (unless AJAX) |
| **Example** | Form validation, animations | News site, e-commerce product pages |

**Static page** (for contrast): pre-built HTML file, same content for all users, no scripting.

**Web page interfacing with database:**
```
[User Browser]
      |  HTTP Request (e.g., search query)
      ↓
[Web Server (Apache/Nginx)]
      |
      ↓
[Application Server (PHP/Python/Java)]
      |  SQL query
      ↓
[Database (MySQL/PostgreSQL/Oracle)]
      |  Result set
      ↓
[Application Server – formats result into HTML]
      |
      ↓
[Web Server – sends HTTP Response]
      |
      ↓
[User Browser displays HTML]
```

**Steps:**
1. User submits form → browser sends HTTP request to server
2. Server-side script parses parameters
3. Script connects to database via connector (JDBC/ODBC/PDO)
4. Executes SQL query (SELECT/INSERT/UPDATE/DELETE)
5. Database returns result set
6. Script formats result into HTML
7. Server sends HTML response to browser

**Exam Tip:** Draw the architecture diagram with arrows. Mention SQL, server-side scripting, and connector.

---

### Q10. FTP vs TFTP

| Feature | FTP | TFTP |
|---------|-----|------|
| **Full Form** | File Transfer Protocol | Trivial File Transfer Protocol |
| **Transport Protocol** | TCP | UDP |
| **Port** | 20 (data), 21 (control) | 69 |
| **Connections used** | Two (control + data) | One |
| **Reliability** | Reliable | Unreliable (UDP) but uses simple ACK |
| **Authentication** | Required (username/password) | None |
| **Speed** | Slower (more overhead) | Faster (less overhead) |
| **Complexity** | Complex (many commands) | Simple (5 messages: RRQ, WRQ, DATA, ACK, ERROR) |
| **Use case** | General file transfer | Bootstrapping, firmware loading, embedded devices |
| **Directory listing** | Yes (LIST, DIR) | No |
| **Resume support** | Yes | No |
| **Security** | Plain text (FTPS for secure) | None |

**Exam Tip:** Tabulate. Highlight TCP vs UDP, port numbers, authentication, and use cases.

---

# END OF PROBLEM SET SOLUTIONS

> **Total questions solved: 50** (10 from each Unit I to V)
> Use this file to revise solutions; refer to syllabus notes (next file) for theory.
