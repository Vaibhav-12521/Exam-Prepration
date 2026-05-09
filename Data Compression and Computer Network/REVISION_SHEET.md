# 🚀 DCCN — LAST-MINUTE REVISION SHEET (1-Hour Read)
**Course:** BCA / B.Sc(IT) | **Subject Code:** US6001 | **Sem VI**

> Read this entire file in the **last hour before exam**. Everything important is condensed here.

---

## 📋 1. PROTOCOLS & PORT NUMBERS (Memorize Cold)

| Protocol | Port | Transport | Use |
|----------|------|-----------|-----|
| **HTTP** | 80 | TCP | Web pages |
| **HTTPS** | 443 | TCP | Secure web |
| **FTP** | 20 (data), 21 (control) | TCP | File transfer |
| **TFTP** | 69 | UDP | Trivial file transfer |
| **SMTP** | 25 (587 submission) | TCP | Email send |
| **POP3** | 110 | TCP | Email retrieve |
| **IMAP** | 143 | TCP | Email server access |
| **DNS** | 53 | UDP (TCP for zone) | Name resolution |
| **DHCP** | 67 (server), 68 (client) | UDP | IP auto-config |
| **Telnet** | 23 | TCP | Remote login |
| **SSH** | 22 | TCP | Secure remote login |
| **SNMP** | 161, 162 | UDP | Network management |
| **NTP** | 123 | UDP | Time synchronization |
| **LDAP** | 389 | TCP/UDP | Directory service |

**Memory trick:**
- 20/21 (FTP), 22 (SSH), 23 (Telnet), 25 (SMTP) → "20s for transfer/login/mail"
- 53 (DNS), 80 (HTTP), 110 (POP3), 443 (HTTPS) → core internet

---

## 📐 2. ALL FORMULAS USED IN THIS SUBJECT

### Capacity & Bandwidth:
- **Nyquist (noiseless):** C = 2B × log₂(L) bps
- **Shannon (noisy):** C = B × log₂(1 + SNR) bps
- **SNR(dB) = 10 × log₁₀(SNR)**
- **Bandwidth-Delay Product** = Bandwidth × RTT

### Time & Speed:
- **Propagation Time** = Distance / Speed
- **Transmission Time** = Message size / Bandwidth
- **Round-Trip Time (RTT)** = 2 × Propagation Time

### Hamming Code:
- **2ᵖ ≥ m + p + 1** (where p = parity bits, m = data bits)
- **Hamming distance** for d-error detection: dmin ≥ d+1
- **Hamming distance** for d-error correction: dmin ≥ 2d+1

### Network Topology:
- **Mesh links** = n(n-1)/2
- **Mesh I/O ports** = n-1 per device

### Subnetting:
- **Number of subnets** = 2ⁿ (n = borrowed bits)
- **Hosts per subnet** = 2ʰ – 2 (h = host bits)
- **Total addresses in subnet** = 2ʰ

### ARQ Efficiency:
- **Stop-and-Wait:** η = 1 / (1 + 2a) where a = T_prop / T_trans
- **Go-Back-N:** η = N / (1 + 2a)
- **Selective Repeat:** η = N / (1 + 2a)

### ALOHA:
- **Pure ALOHA max efficiency** = 1/(2e) ≈ **18.4%**
- **Slotted ALOHA max efficiency** = 1/e ≈ **36.8%**

### IP Address:
- **IPv4** = 32 bits (4 octets)
- **IPv6** = 128 bits (8 groups of 4 hex digits)
- **MAC** = 48 bits (6 bytes hex)

### Cryptography (RSA):
- **n = p × q**, **φ(n) = (p-1)(q-1)**
- **e × d ≡ 1 mod φ(n)**
- **Encryption:** C = M^e mod n
- **Decryption:** M = C^d mod n

### Checksum (Internet):
- **1's complement sum of all 16-bit words → take 1's complement**

---

## 📚 3. UNIT-WISE TOP 5 IMPORTANT POINTS

### 🟦 UNIT 1: Introduction
1. **OSI: 7 layers**, TCP/IP: **4 layers** (Network Access, Internet, Transport, Application)
2. **Topologies:** Mesh (most reliable, expensive), Star (hub failure = total fail), Bus (backbone fail = total fail), Ring (ring breaks = total fail)
3. **Transmission media:** Twisted pair < Coaxial < Optical fiber (in cost, bandwidth, distance)
4. **LAN < MAN < WAN** (geographic scope)
5. **Networking devices' layers:** Repeater/Hub (L1), Bridge/Switch (L2), Router (L3), Gateway (all)

### 🟩 UNIT 2: Physical & Data Link
1. **Nyquist** (noiseless), **Shannon** (noisy) for capacity
2. **Data Link Layer services:** Framing, Addressing, Flow Control, Error Control, Access Control
3. **Error Detection:** Parity, Checksum, CRC. **Error Correction:** Hamming Code
4. **Switching:** Circuit (telephone), Packet (Internet, Datagram/Virtual Circuit)
5. **ARQ Protocols:** Stop-and-Wait, Go-Back-N, Selective Repeat

### 🟨 UNIT 3: LLC / MAC
1. **Multiple Access:** Random (ALOHA, CSMA), Controlled (Polling, Token), Channelization (FDMA, TDMA, CDMA)
2. **CSMA/CD** for wired (Ethernet), **CSMA/CA** for wireless (Wi-Fi)
3. **Pure ALOHA** = 18.4% efficient; **Slotted ALOHA** = 36.8% efficient
4. **IP Classes:** A (0-127), B (128-191), C (192-223), D (multicast), E (reserved)
5. **CIDR** uses /n notation, supports VLSM, replaces classful addressing

### 🟧 UNIT 4: Network/Transport
1. **TCP:** reliable, connection-oriented, 20-byte header, 3-way handshake. **UDP:** unreliable, 8-byte header
2. **TCP Flags:** URG, ACK, PSH, RST, SYN, FIN
3. **Congestion Control:** Slow Start (exponential), Congestion Avoidance (linear), Fast Retransmit, Fast Recovery
4. **Cryptography:** Symmetric (DES, AES) vs Asymmetric (RSA, ECC)
5. **QoS parameters:** Reliability, Delay, Jitter, Bandwidth

### 🟪 UNIT 5: Application
1. **DNS** translates name → IP, hierarchical, port 53/UDP
2. **HTTP:** stateless, request-response, port 80
3. **SMTP:** push, port 25, commands HELO/MAIL FROM/RCPT TO/DATA/QUIT
4. **FTP:** two connections (control 21, data 20), out-of-band control
5. **HTTP methods:** GET, POST, PUT, DELETE, HEAD; status codes 1xx/2xx/3xx/4xx/5xx

---

## 📖 4. 20 KEY DEFINITIONS (One Line Each)

1. **Network:** Interconnected collection of autonomous devices that share resources and exchange data.
2. **Topology:** Physical/logical arrangement of nodes and links in a network.
3. **Protocol:** Set of rules governing data exchange (syntax, semantics, timing).
4. **OSI Model:** 7-layer reference architecture for network communication standardized by ISO.
5. **TCP/IP Model:** 4-layer practical protocol stack used in the Internet.
6. **Bandwidth:** Range of frequencies a channel can transmit (Hz) or its data rate (bps).
7. **Throughput:** Actual data delivery rate (≤ bandwidth).
8. **Latency:** Total delay from sender to receiver (transmission + propagation + processing + queuing).
9. **Encapsulation:** Each layer adding its header to upper-layer data before transmission.
10. **Framing:** Dividing bit stream into discrete frames at data link layer.
11. **CRC:** Cyclic Redundancy Check — error detection using polynomial division.
12. **Hamming Code:** Error-correcting code that detects/corrects single-bit errors using parity bits.
13. **MAC Address:** 48-bit physical address assigned to NIC (e.g., 00:1A:2B:3C:4D:5E).
14. **IP Address:** 32-bit logical address (IPv4) used for routing across networks.
15. **Subnet Mask:** 32-bit number dividing IP into network and host portions.
16. **ARP:** Address Resolution Protocol — maps IP to MAC.
17. **ICMP:** Internet Control Message Protocol — error reporting and diagnostics.
18. **DNS:** Domain Name System — translates names to IPs (UDP port 53).
19. **Socket:** Endpoint of network communication (IP + port).
20. **Firewall:** Hardware/software that filters traffic between trusted and untrusted networks.

---

## 🆚 5. CRUCIAL DIFFERENCE TABLES

### 5.1 OSI vs TCP/IP

| Feature | OSI | TCP/IP |
|---------|-----|--------|
| Layers | 7 | 4 (or 5) |
| Origin | ISO (1984) | DARPA (1970s) |
| Approach | Theoretical | Practical |
| Combines | – | App+Pres+Sess into App; DL+Phy into Net Access |
| Adoption | Reference only | Implemented (Internet) |
| Layer dependence | Strict | Loose |

---

### 5.2 TCP vs UDP

| Feature | TCP | UDP |
|---------|-----|-----|
| Connection | Connection-oriented | Connectionless |
| Reliability | Reliable | Unreliable |
| Order | Ordered delivery | No order |
| Speed | Slower | Faster |
| Header | 20-60 bytes | 8 bytes |
| Flow control | Yes (sliding window) | No |
| Congestion control | Yes | No |
| Use case | HTTP, FTP, SMTP | DNS, DHCP, video, gaming |
| Handshake | 3-way handshake | None |

---

### 5.3 IPv4 vs IPv6

| Feature | IPv4 | IPv6 |
|---------|------|------|
| Address size | 32 bits | 128 bits |
| Notation | Dotted decimal (192.168.1.1) | Hexadecimal colon (2001:db8::1) |
| Header size | 20-60 bytes | 40 bytes (fixed) |
| Address space | ~4.3 × 10⁹ | ~3.4 × 10³⁸ |
| Broadcast | Yes | No (multicast/anycast) |
| Auto-config | DHCP | Built-in (SLAAC) |
| Security | Optional (IPSec) | Built-in IPSec |
| NAT needed | Yes | No |
| Fragmentation | At sender + routers | Only at sender |

---

### 5.4 CSMA/CD vs CSMA/CA

| Feature | CSMA/CD | CSMA/CA |
|---------|---------|---------|
| Used in | Wired (Ethernet) | Wireless (Wi-Fi) |
| Approach | Detect collision after | Avoid collision before |
| Mechanism | Listen → Send → Detect → Backoff | Listen → IFS → Backoff → RTS/CTS → Send → ACK |
| Efficiency | Higher | Lower (RTS/CTS overhead) |
| Why? | Wired can detect collisions | Wireless can't (hidden node) |

---

### 5.5 Stop-and-Wait vs Go-Back-N vs Selective Repeat

| Feature | Stop-and-Wait | Go-Back-N | Selective Repeat |
|---------|---------------|-----------|------------------|
| Sender window | 1 | N | N |
| Receiver window | 1 | 1 | N |
| Retransmission | One frame | All from lost onward | Only the lost frame |
| Receiver buffer | None | None | N frames |
| ACK type | Individual | Cumulative | Individual |
| Complexity | Low | Medium | High |
| Bandwidth use | Poor | Better | Best |

---

### 5.6 Pure ALOHA vs Slotted ALOHA

| Feature | Pure ALOHA | Slotted ALOHA |
|---------|-----------|---------------|
| Timing | Send anytime | Send at slot boundary |
| Vulnerable period | 2 × frame time | 1 × frame time |
| Max efficiency | 18.4% | 36.8% |
| Synchronization | Not needed | Required |

---

### 5.7 Circuit vs Packet Switching

| Feature | Circuit | Packet |
|---------|---------|--------|
| Path | Dedicated | None |
| Setup phase | Required | Not required |
| Bandwidth | Reserved | Shared |
| Delay | Setup + minimal | Variable (queuing) |
| Reliability | High | Lower |
| Example | Telephone | Internet |

---

### 5.8 FTP vs TFTP

| Feature | FTP | TFTP |
|---------|-----|------|
| Transport | TCP | UDP |
| Port | 20, 21 | 69 |
| Connections | Two | One |
| Authentication | Yes | No |
| Reliability | Reliable | Limited |
| Use | General | Bootstrap, firmware |

---

### 5.9 Hub vs Switch vs Router

| Feature | Hub | Switch | Router |
|---------|-----|--------|--------|
| Layer | Physical (L1) | Data Link (L2) | Network (L3) |
| Forwarding | Broadcast all | MAC-based | IP-based |
| Collision domain | One | Per port | Per port |
| Speed | Slowest | Fast | Slower than switch |
| Intelligence | None | MAC table | Routing table |

---

### 5.10 Symmetric vs Asymmetric Cryptography

| Feature | Symmetric | Asymmetric |
|---------|-----------|------------|
| Keys | One shared | Two (public + private) |
| Speed | Fast | Slow |
| Distribution | Hard | Easy |
| Algorithms | DES, AES, 3DES | RSA, ECC, DSA |
| Key length | 56-256 bits | 1024-4096 bits |
| Use | Bulk data | Key exchange, signatures |

---

### 5.11 Twisted Pair vs Coaxial vs Optical Fiber

| Feature | Twisted Pair | Coaxial | Optical Fiber |
|---------|--------------|---------|---------------|
| Cost | Low | Medium | High |
| Bandwidth | 100 Mbps | 1 Gbps | THz |
| Distance | ~100 m | ~500 m | 100+ km |
| EMI | Susceptible | Moderate | Immune |
| Signal | Electrical | Electrical | Light |
| Use | LAN | TV | Backbone |

---

### 5.12 LAN vs MAN vs WAN

| Feature | LAN | MAN | WAN |
|---------|-----|-----|-----|
| Range | <1 km | 10-50 km | >100 km |
| Speed | High | Medium | Lower |
| Cost | Low | Medium | High |
| Ownership | Single org | Single org/consortium | Multiple |
| Example | Office | City cable TV | Internet |

---

## 🎯 6. EXAM DAY STRATEGY

### Time Management (3-hour exam, 100 marks):
- **5-mark questions:** ~10-12 mins each
- **10-mark questions:** ~20-25 mins each
- **2-mark questions:** ~3-5 mins each

### Order of attempt:
1. Start with **2-mark short-answers** (build confidence)
2. Then **5-mark questions** you know best
3. Then **numericals** (clean working = full marks)
4. Finally **10-mark theory** with diagrams (most time-consuming)

### Diagram strategy:
- **OSI/TCP-IP stacks** → easy quick marks
- **3-way handshake** → always draw with seq/ack
- **Hamming code/CRC** → show calculation steps
- **Topologies** → simple ASCII-style sketches

### Power phrases that boost marks:
- "Layer N of OSI model is responsible for..."
- "The key difference between X and Y is..."
- "This solves the problem of..."
- "The formula for this is..."
- "An example of this is..."

---

## 🔥 7. ULTRA-CONDENSED MEMORY MAP

```
╔══════════════════════════════════════════════════╗
║   OSI: All People Seem To Need Data Processing   ║
║         App-Pres-Sess-Trans-Net-DataLink-Phys    ║
║                                                   ║
║   TCP/IP: App | Trans | Internet | Net Access    ║
║                                                   ║
║   Topology: Mesh > Star > Bus > Ring (reliability)║
║                                                   ║
║   Devices Layer-wise:                             ║
║   L1: Hub, Repeater                               ║
║   L2: Bridge, Switch                              ║
║   L3: Router                                      ║
║   All: Gateway                                    ║
║                                                   ║
║   Capacity:                                       ║
║   Nyquist (noiseless): C = 2B × log₂L            ║
║   Shannon (noisy):     C = B × log₂(1+SNR)       ║
║                                                   ║
║   ALOHA Efficiency:                               ║
║   Pure: 18.4%   |   Slotted: 36.8%                ║
║                                                   ║
║   ARQ:                                            ║
║   Stop-Wait (1) → Go-Back-N (cumulative ACK) →    ║
║   Selective Repeat (individual ACK + buffer)      ║
║                                                   ║
║   IP Classes:                                     ║
║   A: 0-127 (/8)    B: 128-191 (/16)               ║
║   C: 192-223 (/24) D: 224-239 (multicast)         ║
║                                                   ║
║   TCP Flags: URG ACK PSH RST SYN FIN              ║
║                                                   ║
║   3-Way Handshake: SYN → SYN+ACK → ACK            ║
║                                                   ║
║   Famous Ports:                                   ║
║   20/21=FTP, 22=SSH, 23=Telnet, 25=SMTP,          ║
║   53=DNS, 67/68=DHCP, 69=TFTP, 80=HTTP,           ║
║   110=POP3, 143=IMAP, 443=HTTPS                   ║
║                                                   ║
║   RSA: C = M^e mod n  |  M = C^d mod n            ║
║                                                   ║
║   Hamming: parity bits at positions 1, 2, 4, 8... ║
║   Syndrome = error position                       ║
╚══════════════════════════════════════════════════╝
```

---

## 🎓 FINAL TIPS

1. **Always draw diagrams** — Examiners reward visualization. Even simple ASCII art works.
2. **Tabulate comparisons** — much cleaner than paragraphs.
3. **Show formulas first**, then plug in values, then compute.
4. **State assumptions** in numericals (e.g., "Assuming 1 KB = 1000 bytes").
5. **Don't skip units** — bps, bytes, ms — wrong units = wrong answer.
6. **Number your steps** — helps the examiner follow.
7. **Highlight final answer** with a box or underline.
8. **Don't leave anything blank** — partial credit is better than zero.

---

# 🎯 GOOD LUCK — YOU'VE GOT THIS! 🚀

> Read this revision sheet 2-3 times, glance at the comparison tables, and confidence will follow. All the best!
