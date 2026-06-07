# Incident Analysis Report

## Incident Summary

A network connectivity issue was reported after multiple users were unable to access the website:

`www.yummyrecipesforme.com`

Users experienced a **"Destination Port Unreachable"** error message after attempting to load the webpage.

A cybersecurity analyst investigated the incident using `tcpdump` to inspect network traffic and determine the source of the failure.

---

## Incident Timeline

**Approximate Time of Incident:**  
13:24 (based on tcpdump timestamps)

**Initial Report:**  
Users reported inability to access the website and observed connectivity errors.

**Investigation Method:**  
Network traffic analysis using `tcpdump`.

---

## Technical Findings

### Protocols Identified

The investigation revealed the use of the following network protocols:

| Protocol | Function |
|----------|----------|
| DNS | Resolves domain names into IP addresses |
| UDP | Transport protocol used by DNS |
| ICMP | Reports network communication errors |

### Traffic Analysis

The client system attempted to send DNS requests to the DNS server (`203.0.113.2`) over **UDP port 53** in order to resolve the domain name:

`www.yummyrecipesforme.com`

However, instead of receiving a valid DNS response, the system received an **ICMP error message** indicating:

> UDP Port 53 Unreachable

This indicates that the destination DNS service was unavailable or inaccessible.

Because DNS resolution failed, the browser could not retrieve the destination IP address required to establish a secure HTTPS connection to the web server.

---

## Root Cause Assessment

The most probable causes include:

- DNS service unavailable
- DNS server not listening on UDP port 53
- Firewall blocking DNS traffic
- DNS server misconfiguration

At this stage of the investigation, the issue appears to be related to DNS service availability.

---

## Recommended Remediation Actions

1. Verify DNS server operational status.
2. Confirm that UDP port 53 is active and listening.
3. Review firewall configurations affecting DNS traffic.
4. Inspect DNS server logs for service failures.
5. Test DNS resolution from internal and external networks.

---

## Conclusion

The affected service during the incident was **DNS**, operating over **UDP port 53**.

Although **ICMP** packets were observed in the network logs, they functioned as **error-reporting messages** rather than the root cause of the incident.

The incident prevented domain name resolution, making the website inaccessible to users.
