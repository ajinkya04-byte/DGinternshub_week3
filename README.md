# 🔐 DG Interns Hub – Cybersecurity Internship
# Week 3: Network Scanning, Traffic Analysis & Vulnerability Assessment

---

## Project Title

### Network Scanning, Traffic Analysis & Vulnerability Assessment

This repository contains the practical work completed during **Week 3 of the DG Interns Hub Cybersecurity Internship**.

The practical focused on network scanning, packet-level traffic analysis, network protocol investigation, correlation of Nmap results with Wireshark traffic, and basic vulnerability assessment.

The major tools used during the practical were:

- Nmap
- Wireshark
- Kali Linux
- VirtualBox
- Linux Terminal

The practical was performed within an authorized laboratory environment.

---

# 1. Objective

The main objective of this practical was to understand how network scanning and security assessment work at both a high level and a packet level.

The specific objectives were:

- Perform network scanning using Nmap.
- Observe scanning activity using Wireshark.
- Understand general TCP traffic.
- Perform and analyze TCP SYN scanning.
- Understand TCP SYN and RST/ACK responses.
- Identify DNS traffic.
- Analyze ICMP traffic.
- Analyze ARP traffic.
- Correlate Nmap scan results with packet-level evidence.
- Perform a basic vulnerability and exposure assessment.
- Document security observations and recommendations.

---

# 2. Lab Environment

The practical work was performed in an authorized private laboratory environment.

## Environment Details

| Parameter | Value |
|---|---|
| Scanner | Kali Linux |
| Target | `172.19.21.31` |
| Packet Capture Interface | `eth0` |
| Network | Private Laboratory Network |
| Scanner Tool | Nmap |
| Packet Analysis Tool | Wireshark |
| Virtualization | VirtualBox |

## Laboratory Topology

```text
┌─────────────────────────┐
│       Kali Linux        │
│         Scanner         │
│                         │
│    Nmap + Wireshark     │
└────────────┬────────────┘
             │
             │
             ▼
┌─────────────────────────┐
│    Virtual Network      │
│         Switch           │
└────────────┬────────────┘
             │
             │
             ▼
┌─────────────────────────┐
│       Target VM         │
│                         │
│     172.19.21.31        │
└─────────────────────────┘

The target IP used during the assessment was:

172.19.21.31

The Wireshark packet capture interface was:

eth0
3. Tools Used
### Nmap

Nmap was used for network discovery, TCP scanning, service detection, OS detection, and basic vulnerability assessment.

Main Nmap commands used:

`nmap 172.19.21.31`
`sudo nmap -sS 172.19.21.31`
`nmap -sV 172.19.21.31`
`sudo nmap -O 172.19.21.31`
`sudo nmap --script vuln 172.19.21.31`
### Wireshark

Wireshark was used for packet capture and network traffic analysis.

It was used to analyze:

TCP traffic
TCP SYN packets
TCP RST/RST-ACK packets
DNS traffic
ICMP traffic
ARP traffic
### Kali Linux

Kali Linux was used as the primary cybersecurity testing and analysis platform.

### VirtualBox

VirtualBox was used to provide the virtual laboratory environment.

### Linux Terminal

The Linux terminal was used to execute Nmap, ping, and other network-related commands.

4. Tasks Completed
### Task 10 – Nmap and Wireshark Investigation
Objective

The objective of Task 10 was to understand how network scanning appears at the packet level.

Nmap was used to perform a TCP SYN scan while Wireshark was used to capture and analyze the resulting network packets.

Task 10.1 – Nmap SYN Scan

The following command was used:

`sudo nmap -sS 172.19.21.31`

A TCP SYN scan sends SYN packets to selected destination ports and analyzes the responses to determine the state of those ports.

The scan was performed against the authorized laboratory target.

Purpose

The purpose of the scan was to:

Determine TCP port states.
Identify reachable services.
Understand TCP SYN scanning.
Generate traffic that could be observed in Wireshark.
Task 10.2 – Nmap Scan Observations

The observed Nmap assessment showed:

| Parameter | Observation |
|---|---|
| Target | `172.19.21.31` |
| Host Status | Host was reachable |
| TCP Ports Scanned | 1000 |
| Open TCP Ports | None observed |
| Closed TCP Ports | 1000 |
| OS Detection | Inconclusive |
| NSE Vulnerability Result | No specific vulnerability identified |

The scan provided a high-level view of the network state of the target.

Task 10.3 – Wireshark Capture

Wireshark was started on the eth0 interface before performing the Nmap scan.

The captured traffic was then analyzed using Wireshark display filters.

The first filter used for general TCP traffic was:

tcp
Task 10.4 – General TCP Traffic
Wireshark Filter
tcp

The tcp filter displays TCP packets from the capture.

This provides a general overview of TCP communication before applying more specific filters.

TCP packet information that can be examined includes:

Source IP address
Destination IP address
Source port
Destination port
Sequence number
Acknowledgment number
TCP flags
TCP header information
Analysis

The general TCP filter helped provide an overall view of TCP activity generated during the investigation.

Task 10.5 – TCP SYN Packet Analysis

The following Wireshark display filter was used:

`tcp.flags.syn == 1`

This filter isolates packets containing the TCP SYN flag.

SYN packets are used to initiate TCP connection attempts.

During a TCP SYN scan, Nmap sends SYN packets to different destination ports and analyzes the responses.

Important TCP SYN Fields

The following fields can be examined in a TCP SYN packet:

Source IP address
Destination IP address
Source port
Destination port
Sequence number
TCP flags
Window size
TCP options
Observation

The packet capture demonstrated that an Nmap scan generates actual TCP packets that can be observed and analyzed using Wireshark.

This provides packet-level visibility into the scanning process.

Task 10.6 – TCP RST/ACK Response Analysis

For closed TCP ports, the target can respond with a TCP RST/ACK packet.

The following Wireshark filter was used:

`tcp.flags.reset == 1`

This filter isolates TCP packets containing the RST flag.

Observation

RST/ACK responses can indicate that a TCP connection attempt was rejected.

During TCP scanning, these responses can provide useful information about the state of a probed port.

The RST filter therefore helped correlate Nmap port-state results with the underlying packet traffic.

Task 10.7 – Nmap and Wireshark Correlation

The Nmap results and Wireshark packet captures can be correlated as follows:

| Nmap Observation | Wireshark Evidence | Interpretation |
|---|---|---|
| Host is reachable | Network/TCP packets observed | Network connectivity exists |
| Closed TCP port | SYN followed by RST/ACK | Connection attempt was rejected |
| TCP SYN scan | Multiple SYN packets | TCP services were being probed |
| No open service identified | RST responses observed | No listening TCP service detected on those ports |
Task 10 Result

Task 10 demonstrated how an Nmap scan can be observed directly through packet capture.

Nmap provides a high-level interpretation of the target, while Wireshark provides low-level visibility into the actual network packets.

This correlation improved understanding of how network scanning activity appears on the network.

### Task 11 – Advanced Traffic Investigation
Objective

The objective of Task 11 was to analyze network packets and identify important network events using Wireshark display filters.

The captured traffic was examined for DNS, ICMP, and ARP communication.

Task 11.1 – DNS Traffic Analysis

DNS is used to translate domain names into IP addresses.

The following Wireshark filter was used:

dns
Purpose

The dns filter was used to isolate:

DNS queries
DNS responses
Requested domain information
Resolved IP addresses
Observation

A DNS request generally contains the domain being queried, while the corresponding response can contain the resolved IP address.

DNS analysis can therefore provide visibility into domain-resolution activity occurring on a network.

Task 11.2 – ICMP Traffic Analysis

ICMP traffic was generated using the ping command.

The following command was used:

`ping 172.19.21.31`

The following Wireshark filter was then used:

icmp
Purpose

The filter was used to isolate ICMP packets such as:

Echo Requests
Echo Replies
Observation

The ICMP Echo Request is sent by the source host.

An ICMP Echo Reply indicates that the destination responded to the request.

This provides a basic method of observing host reachability at the packet level.

Task 11.3 – ARP Traffic Analysis

ARP, or Address Resolution Protocol, is used on IPv4 local networks to determine the MAC address associated with an IP address.

The following Wireshark filter was used:

arp

Typical ARP communication contains messages such as:

Who has <IP address>?
Tell <IP address>
Observation

ARP packets provide visibility into local IP-to-MAC address resolution.

The arp filter allowed ARP requests and responses to be isolated from other traffic in the packet capture.

Task 11.4 – Important Network Events

The major network events observed during the investigation can be summarized as follows:

| # | Source | Destination | Protocol | Observation |
|---:|---|---|---|---|
| 1 | Scanner | Target | TCP | SYN connection attempt |
| 2 | Target | Scanner | TCP | RST/ACK response |
| 3 | Local Host | DNS Server | DNS | DNS query |
| 4 | Local Host | Target | ICMP | Echo request |
| 5 | Target | Local Host | ICMP | Echo reply |
| 6 | Local Host | Broadcast | ARP | ARP request |
Task 11.5 – Security Observations

The traffic investigation demonstrated several important security concepts:

Repeated TCP SYN packets can indicate port scanning activity.
RST responses provide information about closed TCP ports.
DNS traffic reveals domain-resolution activity.
ICMP packets can be used to determine host reachability.
ARP traffic is important for understanding local network behavior.
Task 11 Result

Task 11 improved understanding of normal and security-relevant network traffic.

Using Wireshark display filters made it possible to isolate specific protocols from a larger packet capture and analyze them individually.

### Task 12 – Vulnerability Assessment
Objective

The objective of Task 12 was to perform a basic vulnerability and exposure assessment of the authorized laboratory target.

Nmap was used to inspect the target for exposed services and potential security issues.

Task 12.1 – Nmap Vulnerability Script Scan

The following command was used:

`sudo nmap --script vuln 172.19.21.31`

Nmap's NSE vulnerability scripts were used to check for specific vulnerability-related conditions based on the responses obtained from the target.

Task 12.2 – Assessment Results

The observed assessment showed:

The target was reachable.
The scanned TCP ports were reported as closed.
No specific vulnerability was identified by the observed NSE scan.
OS detection was inconclusive.
No exposed TCP service was identified in the observed scan.

Therefore, the assessment should not claim the presence of a vulnerability that was not detected.

Important Security Principle

The absence of a detected vulnerability should not be interpreted as proof that a system is completely secure.

A complete security assessment should also consider additional factors such as:

UDP services
Applications listening on non-standard ports
Local privilege configuration
Authentication mechanisms
Software versions
Firewall configuration
Network segmentation
Host-based security controls
Task 12.3 – Security Recommendations

Based on the assessment methodology, the following security practices are recommended:

1. Disable Unnecessary Services

Unnecessary network services should be disabled to reduce the exposed attack surface.

2. Use Firewalls

Host-based and network firewalls should be configured to restrict unauthorized access.

3. Restrict Administrative Services

Administrative services should only be accessible from authorized systems and networks.

4. Keep Systems Updated

Operating systems and applications should be regularly patched and updated.

5. Monitor Network Traffic

Network monitoring should be used to identify unusual scanning activity and repeated connection attempts.

6. Perform Periodic Vulnerability Assessments

Regular assessments should be performed to identify newly introduced security issues.

7. Implement Network Segmentation

Sensitive systems should be separated using appropriate network segmentation.

8. Maintain Security Logging

Important network and security events should be logged and monitored.

# 5. Key Findings

The overall findings from Tasks 10, 11, and 12 are summarized below.

Network Scanning

Nmap successfully communicated with the authorized laboratory target and provided information about the state of the scanned TCP ports.

TCP Analysis

TCP SYN packets were observed during the scanning activity.

RST/RST-ACK responses were observed in relation to rejected TCP connection attempts.

Protocol Analysis

Wireshark filters successfully isolated:

tcp
`tcp.flags.syn == 1`
`tcp.flags.reset == 1`
dns
icmp
arp

These filters made it easier to analyze specific network protocols and events.

Vulnerability Assessment

The observed vulnerability assessment did not identify a specific vulnerability.

The observed TCP ports were reported as closed, and OS detection was inconclusive.

Security Improvements

Based on the practical, the following security improvements are recommended:

Disable unnecessary network services.
Keep operating systems and applications updated.
Use host-based and network firewalls.
Restrict administrative access.
Monitor network traffic for unusual scanning activity.
Perform periodic vulnerability assessments.
Implement network segmentation for sensitive systems.
Maintain appropriate security logging and monitoring.
# 6. Before / After Results
### Before

Before applying detailed packet analysis, the primary information available was the high-level Nmap scan output.

The packet capture also contained a large number of packets, making it difficult to immediately identify the relevant network events.

The main information available was:

Target Reachability
       ↓
Nmap Scan
       ↓
Port State
### After

After using Wireshark display filters, individual types of network traffic could be isolated and examined.

For example:

tcp

provided a general view of TCP traffic.

`tcp.flags.syn == 1`

isolated TCP SYN packets.

`tcp.flags.reset == 1`

isolated TCP RST packets.

dns

isolated DNS traffic.

icmp

isolated ICMP traffic.

arp

isolated ARP traffic.

The investigation therefore moved from high-level scan results to detailed packet-level analysis.

### Before vs After Comparison
| Before | After |
|---|---|
| Network activity mainly viewed through Nmap | Network activity also analyzed using Wireshark |
| TCP port states viewed from scan output | TCP SYN and RST packets examined directly |
| Large packet capture was difficult to interpret | Display filters isolated relevant packets |
| DNS traffic mixed with other traffic | DNS traffic isolated using `dns` |
| ICMP traffic not isolated | ICMP requests and replies identified |
| ARP traffic mixed with other traffic | ARP communication isolated |
| Vulnerability assessment based on scan output | Scan results interpreted with packet-level observations |
### Overall Investigation Workflow
                 Network Activity
                        │
                        ▼
                      Nmap
                        │
                        ▼
                 Scan Results
                        │
                        ▼
                   Wireshark
                        │
                        ▼
              Packet-Level Analysis
                        │
                        ▼
               Display Filtering
                        │
          ┌─────────────┼─────────────┐
          │             │             │
          ▼             ▼             ▼
         TCP           DNS           ICMP
          │                           │
          ▼                           ▼
       SYN / RST                     ARP
          │                           │
          └─────────────┬─────────────┘
                        ▼
                Security Analysis
                        │
                        ▼
             Vulnerability Assessment
# 7. Conclusion

Week 3 provided hands-on experience with network scanning, packet-level traffic analysis, protocol investigation, and basic vulnerability assessment.

Nmap was used for:

Network scanning
TCP SYN scanning
Service detection
OS detection
Vulnerability assessment

Wireshark was used for:

General TCP analysis
TCP SYN analysis
TCP RST analysis
DNS analysis
ICMP analysis
ARP analysis

The analysis demonstrated how a high-level Nmap scan can be correlated with actual packets observed on the network.

The TCP SYN and RST/RST-ACK analysis helped demonstrate how network scanning activity can be identified through packet-level evidence.

The DNS, ICMP, and ARP investigations improved understanding of normal network communication and the role of different protocols.

The vulnerability assessment did not identify a specific vulnerability in the observed scan results. However, the result should not be interpreted as proof that the target is completely secure.

The practical reinforced the importance of:

Service minimization
Firewalls
Patch management
Network monitoring
Network segmentation
Periodic vulnerability assessment
Security logging

Overall, this practical strengthened my understanding of network security tools and improved my ability to interpret network traffic from a cybersecurity perspective.
