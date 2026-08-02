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

### Q1: What is the attacker's IP address?

First I opened the PCAP file using Wireshark. Saw a long list of packets captured during the incident. Then applied the http filter to sort http request only over the browser. As web request to server are in http, filtering will give us the packets we need to analyze for the behavior. 

[http filter]

Discovered that, in the ***[Statistics -> Endpoints]*** tab in Wireshark we can easily list all endpoints on the http requests. Endpoints are the devices that are have been involved during the packet capturing. Here is a list of all endpoints found. It gives all unique IPs that sent the request to server. One of these is our desired IP, which is attackers endpoints.

[endpoints]

As our payload was uploaded to the site, to find the requests in http which used upload we want to list those specific http requests. I used an advance search filter ***[http and http contains "upload"]***, which resulted in only the IP address which was using an upload request. 

[filter picture]

So our desired IP is: ***23.158.56.196***

Further to see all the request captured in the packets, I discovered that we can create a follow of all the packets. 
***[Right Click -> Follow -> Http follow].***
It join the contents the packets into a proper request and response form. This request and response in http can be analyzed for further analysis of each request.
