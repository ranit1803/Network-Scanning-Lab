# Network Scanning & Packet Analysis Lab

ARP Scan (Netdiscover) + ICMP Ping + Wireshark Analysis

---

## Lab Description

Performed ARP-based host discovery and ICMP reachability testing in a virtual LAN using Kali Linux and Metasploitable2. Used Netdiscover and Wireshark to examine ARP broadcasts/replies and ICMP echo packets, learning how host discovery works at Layer-2 and Layer-3. All IP and MAC details are masked for security.

---

## Folder Structure

```
src/
│
├── netdiscover/
│   ├── netdiscover-output.txt
│   ├── arp-analysis.md
│
├── icmp/
│   ├── ping-output.txt
│   ├── icmp-analysis.md
│
└── network-config/
    ├── kali-ip.md
    ├── metasploit-ip.md
    └── virtualbox-settings.md

screenshots/
```

---

## Tools Used

* Kali Linux (Attacker VM)
* Metasploitable2 (Target VM)
* Oracle VirtualBox Host-Only Network
* Netdiscover
* Ping (ICMP)
* Wireshark

---

## Network Setup

Both VMs were configured on a Host-Only Adapter to ensure they remained inside the same LAN. This is required because ARP works only within a single broadcast domain.

* Kali IP: `<kali-ip>/24`
* Metasploitable2 IP: `<target-ip>/24`

All IPs and MACs are masked for privacy.

---

## Part 1 — ARP Scan (Netdiscover)

### What Was Done

An ARP scan was performed using:

```
sudo netdiscover -r <network-range>/24
```

### What ARP Revealed

ARP requests were broadcast to all hosts in the subnet, and ARP replies confirmed:

* The VirtualBox host-only gateway
* The target VM
* The Kali VM

MAC and IP values are masked in this repo.

### Wireshark View

Captured packets included:

* ARP Request: "Who has `<target-ip>`? Tell `<kali-ip>`"
* ARP Reply: "`<target-ip>` is at `<target-mac-hidden>`"

This confirmed correct Layer-2 communication.

---

## Part 2 — ICMP Ping Scan

### Command Used

```
ping -c 4 <target-ip>
```

### What ICMP Showed

* Host responded to all echo requests
* 0% packet loss
* TTL ≈ 64 (Linux-based target)
* Matching sequence numbers

### Wireshark View

Captured:

* ICMP Echo Request
* ICMP Echo Reply
* ID, sequence numbers, and TTL (masked)

---

## ARP Scan vs ICMP Ping

| Feature                 | ARP Scan       | ICMP Ping         |
| ----------------------- | -------------- | ----------------- |
| Layer                   | Layer-2        | Layer-3           |
| Protocol                | ARP            | ICMP              |
| Discovers all LAN hosts | Yes            | No                |
| Works if ICMP blocked   | Yes            | No                |
| Works across networks   | No             | Yes               |
| Purpose                 | Host discovery | Host reachability |

---

## Key Learnings

* ARP is essential for discovering devices inside a LAN
* ICMP confirms host availability at the network layer
* Wireshark helps visualize protocol behavior
* NAT + Bridged setups break ARP scanning; Host-Only is required
* VirtualBox NIC vendor is PCS Systemtechnik GmbH (normal for VMs)

---

## Security Disclaimer

All IP addresses, MAC addresses, and sensitive identifiers in this repo are masked or blurred to prevent exposure of real device information.

---

