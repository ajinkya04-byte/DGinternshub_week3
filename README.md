# Cybersecurity Internship - Week 3

## Overview

This repository contains the practical work completed during Week 3
of my cybersecurity internship.

The practical focused on:

- Network scanning using Nmap
- TCP SYN scanning
- TCP packet analysis
- Wireshark traffic analysis
- DNS analysis
- ICMP analysis
- ARP analysis
- Basic vulnerability assessment

## Tools Used

- Kali Linux
- Nmap
- Wireshark
- VirtualBox

## Laboratory Target

Target: `172.19.21.31`

All testing was performed within an authorized laboratory environment.

## Nmap

Commands used:

```bash
nmap 172.19.21.31
nmap -sS 172.19.21.31
nmap -sV 172.19.21.31
sudo nmap -O 172.19.21.31
sudo nmap --script vuln 172.19.21.31
