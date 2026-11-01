# INT302 Lab 2: Website Enumeration Report

## Overview
This report details the findings from utilizing whatweb to identify web technologies, server configurations, and security headers.

## Exercise 1: Basic Web Technology Detection
*   *example.com:* HTTP Status 200 OK, HTTPServer[cloudflare], Title[Example Domain]
*   *stackoverflow.com:* HTTP Status 301, Cookies[__cf_bm], HTTPServer[cloudflare], HSTS
*   *github.com:* HTTP Status 200 OK, HTTPServer[github.com], Ruby on Rails, HSTS

*Analysis:* Basic scans reveal the public-facing technologies and CDN usage (Cloudflare for Stack Overflow, Fastly for GitHub) which helps hide the true origin server.

## Exercise 2: Aggressive Scanning
*   *google.com:* HTTP Status 301, Google Web Server (GWS), HSTS, HTTP/3
*   *facebook.com:* HTTP Status 301, HTTP/3, Proxygen, HSTS

*Analysis:* Aggressive scans (-a 3) revealed deep security configurations like HSTS. Attempting this on major sites often triggers Web Application Firewalls (WAFs), resulting in 403/400 errors, demonstrating the limits of automated scanning against enterprise targets.
