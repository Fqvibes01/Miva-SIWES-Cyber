# INT302 Lab 8: Web App Security Testing (Burp Suite & ZAP)

## Overview
This report documents web application testing using Burp Suite and OWASP ZAP against testphp.vulnweb.com.

## Tools & Configuration
*   *Burp Suite:* Configured Firefox to route traffic through the proxy (127.0.0.1:8080).
*   *OWASP ZAP:* Used the automated scanner to identify vulnerabilities.

## Key Findings
*   Intercepted HTTP requests and observed headers.
*   Spidering discovered endpoints like /login.php and /search.php.
*   Both tools successfully identified *SQL Injection* and *Cross-Site Scripting (XSS)* vulnerabilities.
*   Fuzzing with Burp Intruder confirmed the SQL Injection vulnerability via error-based payloads.

## Comparison
*   *Burp Suite:* Better for manual interception and fine-tuned testing.
*   *OWASP ZAP:* Easier to use for automated scanning and generating quick reports.

## Recommendations
*   Implement input validation and output encoding.
*   Use parameterized queries for database interactions.
