# Cybersecurity Incident Report: Network Traffic Analysis

> Fictional scenario. A handful of customers reported being unable to access the company website, `yummyrecipesforme.com`, seeing a "destination port unreachable" error. This report documents the packet-level investigation into the issue using `tcpdump`.

## tcpdump Log

```
13:24:32.192571 IP 192.51.100.15.52444 > 203.0.113.2.domain: 35084+ A? yummyrecipesforme.com. (24)
13:24:36.098564 IP 203.0.113.2 > 192.51.100.15: ICMP 203.0.113.2 udp port 53 unreachable, length 254

13:26:32.192571 IP 192.51.100.15.52444 > 203.0.113.2.domain: 35084+ A? yummyrecipesforme.com. (24)
13:27:15.934126 IP 203.0.113.2 > 192.51.100.15: ICMP 203.0.113.2 udp port 53 unreachable, length 320

13:28:32.192571 IP 192.51.100.15.52444 > 203.0.113.2.domain: 35084+ A? yummyrecipesforme.com. (24)
13:28:50.022967 IP 203.0.113.2 > 192.51.100.15: ICMP 203.0.113.2 udp port 53 unreachable, length 150
```

## Part 1: Summary of the Problem Found in the DNS and ICMP Traffic Log

As part of the DNS protocol, the UDP protocol was used to contact the DNS server (`203.0.113.2`) to retrieve the IP address for the domain name `yummyrecipesforme.com`. The ICMP protocol was used to respond with an error message, indicating issues contacting the DNS server.

The UDP query going from the client (`192.51.100.15`) to the DNS server is shown in the first line of every log event. The ICMP error response from the DNS server back to the client is shown in the second line of every event, with the error message **"udp port 53 unreachable."**

Since port 53 is the standard port for DNS traffic, this confirms the issue lies with the DNS server itself. This is further supported by the flags visible in the log: the plus sign after the query ID `35084` indicates flags associated with the UDP message, and the `A?` symbol indicates a DNS request for an A record — the record type that maps a domain name to an IP address.

Because every outgoing UDP query to the DNS server is met with an ICMP "port 53 unreachable" response, it is highly likely that the DNS server is not responding to any DNS requests.

## Part 2: Analysis and Root Cause

**When the problem was first reported:** The log's first timestamp, `13:24:32`, shows the incident occurring today at 1:24 p.m. (24-hour format).

**Initial reports:** A handful of customers contacted the company to report that they were unable to access the website, seeing the error "destination port unreachable" after the page failed to load.

**Current status:** The issue was reported to a direct supervisor and is now being handled by security engineers.

**Investigation so far:** After reproducing the error by visiting the site directly, the network analyzer tool `tcpdump` was used to capture live traffic while reloading the page. The capture showed repeated UDP queries to the DNS server, each met with an ICMP "udp port 53 unreachable" response — confirming that DNS resolution for the domain is consistently failing.

**Next steps:** Determine whether the DNS server itself is down, or whether traffic to port 53 is being blocked by the firewall. If the DNS server is functioning normally, firewall configuration should be checked for any recent changes blocking port 53.

**Suspected root cause:** The unreachable port could result from:
- A **Denial of Service (DoS) attack** against the DNS server — a flood of traffic sent to overwhelm the server and prevent it from responding to legitimate requests, or
- A **firewall misconfiguration** — a configuration change that unintentionally blocked traffic on port 53.
