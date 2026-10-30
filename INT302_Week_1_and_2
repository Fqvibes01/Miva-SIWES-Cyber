#!/bin/bash

# ==========================================
# INT302 Lab 1: Advanced Reconnaissance Framework
# Author: Farouq Suleiman
# Matric No: 30104026
# ==========================================

DOMAIN="$1"

if [ -z "$DOMAIN" ]; then
    echo "Usage: $0 <domain>"
    exit 1
fi

OUTPUT_DIR="recon_output_${DOMAIN}"
mkdir -p "$OUTPUT_DIR"
COMPREHENSIVE_REPORT="${OUTPUT_DIR}/comprehensive_report.txt"

# --- 1. Ping Analysis ---
advanced_ping_analysis() {
    echo " Performing Ping Analysis for $DOMAIN" | tee -a "$COMPREHENSIVE_REPORT"
    echo "----------------------------------------" | tee -a "$COMPREHENSIVE_REPORT"
    
    ping -c 4 "$DOMAIN" > "${OUTPUT_DIR}/ping_raw.txt"
    
    local avg_ping=$(grep "avg" "${OUTPUT_DIR}/ping_raw.txt" | awk -F'/' '{print $5}')
    local packet_loss=$(grep "packet loss" "${OUTPUT_DIR}/ping_raw.txt" | awk '{print $6}')
    
    echo "Average RTT: ${avg_ping} ms" | tee -a "$COMPREHENSIVE_REPORT"
    echo "Packet Loss: ${packet_loss}" | tee -a "$COMPREHENSIVE_REPORT"
    echo "" | tee -a "$COMPREHENSIVE_REPORT"
}

# --- 2. Comprehensive DNS ---
comprehensive_dns_scan() {
    echo " Comprehensive DNS Analysis" | tee -a "$COMPREHENSIVE_REPORT"
    echo "----------------------------------------" | tee -a "$COMPREHENSIVE_REPORT"
    
    for record in A AAAA MX TXT NS SOA CNAME; do
        echo " $record Records:" | tee -a "$COMPREHENSIVE_REPORT"
        dig "$DOMAIN" $record +short | tee -a "$COMPREHENSIVE_REPORT"
        echo "" | tee -a "$COMPREHENSIVE_REPORT"
    done
}

# --- 3. Summary Generation ---
generate_summary() {
    echo " Reconnaissance Summary" | tee -a "$COMPREHENSIVE_REPORT"
    echo "----------------------------------------" | tee -a "$COMPREHENSIVE_REPORT"

    local ip_count=$(dig "$DOMAIN" A +short | wc -l)
    local mx_count=$(dig "$DOMAIN" MX +short | wc -l)
    local ns_count=$(dig "$DOMAIN" NS +short | wc -l)

    echo " Infrastructure Overview:" | tee -a "$COMPREHENSIVE_REPORT"
    echo "  IP Addresses: $ip_count" | tee -a "$COMPREHENSIVE_REPORT"
    echo "  Mail Servers: $mx_count" | tee -a "$COMPREHENSIVE_REPORT"
    echo "  Name Servers: $ns_count" | tee -a "$COMPREHENSIVE_REPORT"
    echo "" | tee -a "$COMPREHENSIVE_REPORT"

    echo " Security Observations:" | tee -a "$COMPREHENSIVE_REPORT"
    echo "  - Check for SPF/DKIM/DMARC records in TXT" | tee -a "$COMPREHENSIVE_REPORT"
    echo "  - Verify name server security" | tee -a "$COMPREHENSIVE_REPORT"
    echo "  - Analyze subdomain structure" | tee -a "$COMPREHENSIVE_REPORT"
}

# --- Main Execution ---
main() {
    echo " Starting comprehensive reconnaissance for: $DOMAIN" | tee -a "$COMPREHENSIVE_REPORT"
    echo "" | tee -a "$COMPREHENSIVE_REPORT"

    advanced_ping_analysis
    comprehensive_dns_scan
    generate_summary

    echo " Reconnaissance complete!" | tee -a "$COMPREHENSIVE_REPORT"
    echo " Results saved in: $OUTPUT_DIR" | tee -a "$COMPREHENSIVE_REPORT"
    echo " Main report: $COMPREHENSIVE_REPORT" | tee -a "$COMPREHENSIVE_REPORT"
}

main "$@"
