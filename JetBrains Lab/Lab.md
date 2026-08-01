# Lab: Jetbrains Lab
![Course](https://img.shields.io/badge/Course%201-Foundations%20of%20Cybersecurity-4EEB2A)
![Status](https://img.shields.io/badge/Status-Completed-4EEB2A)

**Category:** Network Forensics <br/>
**Tactics:** Initial Access, Execution, Command and Control <br/>
**Tools:** Wireshark, NetworkMiner, Brim

---

## Analyze network traffic using Wireshark to identify web server exploitation, extract attacker IOCs and persistence mechanisms, and map attack techniques to MITRE ATT&CK.

### Snario:
During a recent security incident, an attacker successfully exploited a vulnerability in our web server, allowing them to upload webshells and gain full control over the system. The attacker utilized the compromised web server as a launch point for further malicious activities, including data manipulation. 

As part of the investigation, You are provided with a packet capture (PCAP) of the network traffic during the attack to piece together the attack timeline and identify the methods used by the attacker. The goal is to determine the initial entry point, the attacker's tools and techniques, and the compromise's extent.

---

### Q1: Identifying the attacker's IP address helps trace the source and stop further attacks. What is the attacker's IP address?

1. Opened the PCAP file using Wireshark. Saw a long list of packets captured during the incident.
2. Applied the http filter to sort http request only over the browser. As web request to server are in http, filtering will give us the packets we need to analyze for the behaviur.
3. Using the [Statistics -> Endpoints] tab in Wireshark we can easily list all endpoints on the http requests.
4. Now using an advance search filter [
