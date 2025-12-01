# Kali Linux Network Configuration
This file documents the network configuration of the Kali Linux VM used in this lab.  

---

## IP Information
The Kali machine was assigned an IP in the Host-Only network:
<kali-ip>/24

---

## Why This Matters
Kali must be in the same LAN as Metasploitable2 for ARP scanning and ICMP communication to work.
This confirms Layer-2 and Layer-3 connectivity required for the lab.