# INT302 Lab 3: Subdomain Hunting Report

## Overview
This report details subdomain enumeration using sublist3r, directory brute-forcing with dirb, and advanced DNS recon using KnockPy.

## Exercise 1: Sublist3r
*   *github.com:* Discovered api.github.com, gist.github.com, pages.github.com.
*   *google.com:* Discovered mail.google.com, drive.google.com, admin.google.com.

*Analysis:* Passive enumeration reveals the vast infrastructure of organizations. Finding subdomains like admin or dev is critical as they often have weaker security.

## Exercise 2: Dirb
*   *example.com / example.org:* No hidden directories found (standard 404 responses).

*Analysis:* dirb automates the discovery of hidden directories (like /backup/ or /admin/). 

## Exercise 3: KnockPy
*   *example.com:* Discovered www.example.com resolving to its primary IP.

*Analysis:* KnockPy was installed in a Python virtual environment. Using the --recon flag provided detailed DNS information and IP resolution for discovered subdomains.
