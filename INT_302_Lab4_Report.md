# INT302 Lab 4: Port Scanning and Vulnerability Assessment

## Overview
This report details network scanning and vulnerability detection using nmap and nikto against an authorized local target VM.

## 1. Basic Scan (nmap)
*   *Open Ports:* 21 (FTP), 22 (SSH), 80 (HTTP), 8080 (HTTP-Proxy), 3306 (MySQL).
*   *Analysis:* Reveals a full web application stack and broad attack surface.

## 2. Aggressive Scan (nmap -sV -O)
*   *Service Versions:* vsftpd 2.3.4, OpenSSH 5.3, Apache httpd 2.2.8.
*   *Operating System:* Linux 2.6.9 - 2.6.33.
*   *Analysis:* Fingerprinting identified vsftpd 2.3.4, which contains a famous backdoor (CVE-2011-2523).

## 3. Vulnerability Scan (nmap --script vuln)
*   *Findings:* vsftpd-backdoor, http-slowloris (Denial of Service).

## 4. Web Vulnerability Scan (nikto)
*   *Findings:* Missing X-Frame-Options (Clickjacking risk), exposed /admin/ directory, outdated Apache version.
