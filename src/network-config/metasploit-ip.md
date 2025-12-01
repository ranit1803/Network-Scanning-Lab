# Metasploitable2 Network Configuration
This file documents the IP configuration of the Metasploitable2 VM. 

---

## IP Information
Metasploitable2 received an IP in the same Host-Only network: <target-ip>/24

---

## 📌 Why This Matters
Both Kali and Metasploitable2 must be in the **same broadcast domain** for ARP scanning.  
This also ensures successful ICMP reachability during testing.

