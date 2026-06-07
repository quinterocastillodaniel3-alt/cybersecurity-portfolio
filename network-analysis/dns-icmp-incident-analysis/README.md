# DNS and ICMP Incident Analysis Using tcpdump

## Overview

This project documents the analysis of a cybersecurity network incident involving DNS service failure and ICMP error responses. The investigation was performed using `tcpdump` network logs to determine the affected protocol and identify a probable root cause.

## Scenario

Users reported that they were unable to access the website:

`www.yummyrecipesforme.com`

After attempting to load the webpage, users received the error:

> Destination Port Unreachable

A network traffic analysis was conducted to determine the cause of the issue.

## Objective

The objective of this investigation was to:

- Analyze DNS and ICMP traffic
- Identify the affected network protocol
- Determine the impacted service
- Establish a likely root cause
- Propose remediation steps

---

## Network Traffic Evidence

Traffic evidence can be found in the following directory:

`evidence/tcpdump-log.png`

---

## Technical Analysis

### Protocols Observed

| Protocol | Purpose |
|----------|----------|
| DNS | Domain name resolution |
| UDP | Transport protocol for DNS requests |
| ICMP | Error reporting and network diagnostics |

### Findings

The client device attempted to contact the DNS server (`203.0.113.2`) using UDP port 53 to resolve the domain name of the target website.

However, the DNS server returned an ICMP error message indicating:

> UDP Port 53 Unreachable

This prevented successful DNS resolution, meaning the browser could not obtain the destination IP address required to establish an HTTPS connection to the website.

---

## Root Cause Assessment

The likely causes include:

- DNS service failure
- DNS daemon not listening on port 53
- Firewall blocking UDP traffic on port 53
- DNS server misconfiguration

---

## Recommended Next Steps

1. Verify DNS server availability.
2. Confirm that port 53 is actively listening.
3. Review firewall rules affecting DNS traffic.
4. Check DNS service logs.
5. Validate external DNS connectivity.

---

## Tools Used

- `tcpdump`
- Network traffic analysis
- DNS/ICMP packet inspection

## Skills Demonstrated

- Packet analysis
- Network troubleshooting
- DNS troubleshooting
- Incident documentation
- Cybersecurity investigation
