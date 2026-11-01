# INT302 Lab 5: Wireshark Network Analysis

## Overview
This report documents capturing and analyzing live network traffic using Wireshark and tshark.

## Key Exercises Completed
*   *Interface & Tools:* Identified GUI components. Compared Wireshark GUI (visual, color-coded) with tshark CLI (fast, scriptable).
*   *Filtering:* Applied display filters (http, dns, ip.addr == <IP>) to isolate traffic.
*   *Packet Details:* Analyzed OSI layers (Ethernet, IPv4, TCP) and observed SYN/ACK flags.
*   *Follow TCP Stream:* Reconstructed an HTTP session, viewing the GET request and HTML response in plain text.
*   *Statistics:* Generated a Protocol Hierarchy report (TCP was most prevalent) and I/O Graphs to visualize traffic spikes.

## Security Applications
*   *Data Retention:* Saved .pcap files allow retroactive analysis of breaches.
*   *Troubleshooting:* Identified that TCP Retransmissions or Zero Window errors cause slow network performance.
*   *Threat Hunting:* Wireshark is used to spot unencrypted credentials (HTTP) and malware beaconing (repetitive DNS queries).
