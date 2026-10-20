# INT 301 Lab 3: Comprehensive Network Discovery and Analysis

## Part 1: Comprehensive Network Discovery
*Step 1: Advanced Interface Analysis*
- Displayed network interfaces using ip addr show and ip link show.
- Displayed network statistics using ss -tuln and cat /proc/net/dev.

*Exercise 1.1: ss vs netstat*
ss is the modern replacement for netstat. ss provides more detailed information, is significantly faster, and displays TCP internal information. netstat is deprecated and slower.

*Step 2: Network Configuration Management*
- Created a virtual Ethernet pair (veth0 and veth1).
- Assigned IP addresses (10.0.1.1/24 and 10.0.1.2/24) and brought the interfaces up.

*Exercise 1.2: Test Connectivity*
Successfully pinged between veth0 and veth1 to confirm routing worked within the virtual interfaces.

*Step 3: Advanced Routing Analysis*
- Checked routing tables using ip route show table all.
- Created a custom routing table and added a rule to test advanced routing concepts.

## Part 2: Advanced Connectivity Testing
*Step 1: Comprehensive Ping Techniques*
- Used ping -I eth0 to bind ping to a specific interface.
- Used ping -t 10 to set the Time-To-Live.
- Used sudo ping -f for a flood ping to stress test the network.

*Exercise 2.1: Flood Ping Analysis*
Flood ping sends packets as fast as possible to stress test a network and identify packet loss. It requires root because it can easily overwhelm a network.

## Part 3: Network Service Analysis
*Step 1 & 2: Port Scanning and Banner Grabbing*
- Scanned ports 20-80 on Google using nc -zv.
- Grabbed HTTP banner using echo "HEAD / HTTP/1.0\r\n\r\n" | nc google.com 80.
- Grabbed SMTP banner from Gmail using nc gmail-smtp-in.l.google.com 25.

*Exercise 3.1: Service Banners*
Service banners reveal critical information such as the software name, version number, and operating system. Attackers use this to find known vulnerabilities for specific versions.

## Part 4: Advanced Traffic Analysis
*Step 1 & 2: Comprehensive Packet Capture*
- Used tcpdump -vvv to capture verbose packet data.
- Used tcpdump -XX to view HEX and ASCII payloads.
- Applied filters to capture specific hosts, ports, and protocols.

*Exercise 4.1: DNS Filter*
Command: sudo tcpdump -i eth0 port 53 (Captures only DNS queries and responses).

## Part 5: DNS and Name Resolution
*Step 1 & 2: DNS Analysis Tools*
- Used nslookup and dig for basic and comprehensive DNS lookups.
- Used dig -x 8.8.8.8 for reverse DNS lookups.
- Used dig +trace (Note: This timed out due to VirtualBox NAT restrictions on direct root queries).
- Used dig google.com | grep "Query time" to check DNS response times.

*Exercise 5.1: DNS Response Times*
Local resolver responded in about 4ms. Google's public DNS (8.8.8.8) is highly optimized but subject to minor network latency.

## Part 6: Network Security Analysis
*Step 1 & 2: Firewall and ARP Analysis*
- Checked iptables rules using sudo iptables -L -v -n.
- Checked listening services using sudo ss -tulpn.
- Viewed ARP tables using arp -a and ip neighbor show.
- Monitored ARP traffic using sudo tcpdump -i eth0 -n arp.

## Part 7: Performance and Load Testing
*Step 1 & 2: Bandwidth and Stress Testing*
- Installed iperf3 and speedtest-cli.
- Installed stress-ng and generated network load using stress-ng --udp 4 --timeout 60s.
- Monitored bandwidth using iftop -i eth0.

## Challenge Exercises

*Challenge 1: Network Mapping*
Used nmap -sn 10.0.2.0/24 to discover live hosts (Kali machine, VirtualBox gateway, DNS). Used nmap -sV 10.0.2.2 to identify open ports and services on the gateway.

*Challenge 2: Traffic Analysis*
Captured traffic to traffic.pcap and analyzed the top protocols. Checked for plaintext credentials in the packet payloads (none found as traffic was ICMP/ping).

*Challenge 3: DNS Investigation*
Used dig NS google.com and dig MX google.com to map Google's authoritative name servers and mail exchange records. Checked TXT records for SPF/DMARC security configurations.

*Challenge 4: Network Troubleshooting Scenario*
Simulated a network outage by adding an iptables rule to drop outbound port 80 traffic. Confirmed the outage using curl. Inspected active firewall rules using iptables -L -n, identified the DROP rule, and successfully removed it using iptables -D to restore network functionality.
