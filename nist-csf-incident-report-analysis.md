# Incident Report Analysis — NIST Cybersecurity Framework (CSF)

> Fictional scenario. Acting as a cybersecurity analyst for a multimedia company offering web design, graphic design, and social media marketing services to small businesses. The company recently experienced a DoS attack that disrupted its internal network for two hours. This report analyzes the incident using the five functions of the NIST Cybersecurity Framework: Identify, Protect, Detect, Respond, and Recover.

## Summary

During the attack, the organization's network services suddenly stopped responding due to an incoming flood of ICMP packets, and normal internal traffic could not reach any network resources. The incident management team responded by blocking incoming ICMP packets, taking non-critical network services offline, and restoring critical services — resolving the disruption within two hours.

The cybersecurity team's subsequent investigation found that a malicious actor had sent a flood of ICMP pings into the network through an **unconfigured firewall**, allowing the attacker to overwhelm the network and cause a denial of service.

## Identify

A malicious actor targeted the company with an ICMP flood attack, exploiting a firewall that had no rules in place to filter incoming or outgoing traffic. The entire internal network was affected, and all critical network resources needed to be secured and restored to a functioning state.

## Protect

To mitigate this type of threat going forward, the security team implemented:
- A new firewall rule to **limit the rate of incoming ICMP packets**.
- An **IDS/IPS system** to filter out ICMP traffic exhibiting suspicious characteristics.

## Detect

To improve detection capabilities, the team implemented:
- **Source IP address verification** on the firewall, to check for spoofed IP addresses on incoming ICMP packets.
- **Network monitoring software** to detect abnormal traffic patterns going forward.

## Respond

For future security events of this kind, the cybersecurity team will:
- Isolate affected systems to prevent further disruption to the network.
- Attempt to restore any critical systems and services disrupted by the event.
- Analyze network logs for suspicious or abnormal activity.
- Report all incidents to upper management and appropriate legal authorities, where applicable.

## Recover

To recover from a DDoS-style ICMP flood attack, the following sequence restores network services to normal operation:

1. Block the external ICMP flood at the firewall.
2. Take all non-critical network services offline to reduce internal network traffic.
3. Restore critical network services first.
4. Once the flood of ICMP packets has subsided, bring all non-critical network systems and services back online.
