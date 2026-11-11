# PENETRATION TESTING REPORT
### Footprinting & Network Scanning Phases

**W2-PM-FINAL | CYBERSECURITY | NETWORKWALKS**

| Field | Details |
|---|---|
| **Pentester Name** | Yin Keo Odom |
| **Program/Batch** | B084 - Networkwalks |
| **Date** | 11 October 2026 |
| **Modules Completed** | W2-PM1 (Kali Linux Tools) and W2-PM5 (Zenmap Scanning) |
| **Client/Target** | 1. `networkwalks.com`  2. Metasploitable 2 (Own Lab VM) |
| **Permission Secured?** | Yes. Written permission was obtained for the Networkwalks activity. The scanning activity was conducted in my own lab. |
| **Phases Covered** | Phase 1: Reconnaissance & Footprinting; Phase 2: Scanning & Network Discovery; Phases 3–5: In Progress |

---

## 1. Liability Disclaimer

All activities described in this report were performed either on systems and networks for which I had obtained permission from Networkwalks or within my own devices and authorized lab environment. Any scanning, vulnerability assessment, or exploitation involving Metasploitable 2 was conducted exclusively within my own lab.

All materials are intended strictly for educational and research purposes. Unauthorized testing or access to systems without proper permission is prohibited. I take responsibility for my actions and the use of the knowledge presented here. Unauthorized access may violate applicable laws and result in legal consequences.

## 2. Introduction

This report covers two practical activities from Week 2 of my Cybersecurity & Ethical Hacking internship at Networkwalks: footprinting the `networkwalks.com` domain using Kali Linux (W2-PM1) and network scanning using Zenmap (W2-PM5).

The footprinting activity focuses on gathering publicly available information about a domain. The network scanning activity focuses on discovering active hosts and identifying the availability of my Metasploitable 2 virtual machine within my own lab network.

Each activity includes the tools used, observations, screenshots, and brief security explanations.

## 3. Tools Used

The following table lists the tools used during the practical activities and their purposes.

| Tool | Purpose |
|---|---|
| Kali Linux | Operating system used for reconnaissance and information gathering. |
| WHOIS | Retrieves domain registration details, including registration dates and name servers. |
| WhatWeb | Identifies website technologies, servers, CMS platforms, and plugins. |
| nslookup | Resolves domain names to IP addresses using DNS. |
| curl -I | Retrieves HTTP response headers from a website. |
| wafw00f | Identifies Web Application Firewall (WAF) technologies. |
| DNSRecon | Enumerates DNS records, including NS, MX, SPF, TXT, and SRV records. |
| Zenmap (Nmap GUI) | Discovers live hosts and displays network scanning information, including IP and MAC addresses where available. |
| Metasploitable 2 | An intentionally vulnerable virtual machine used as a target in my own security testing lab. |

## 4. Activities Performed

### 4.1 Footprinting & Reconnaissance

I performed reconnaissance on the `networkwalks.com` domain using six Kali Linux tools: **WHOIS, WhatWeb, Nslookup, Curl, Wafw00f, and DNSRecon**.

- **WHOIS:** Collected domain registration details and identified name servers.
- **WhatWeb:** Identified website technologies, including WordPress 7.1.4 and WP Download Manager 3.3.76.
- **Nslookup:** Resolved the domain name to the IP address `192.232.216.135`.
- **Curl:** Used the `-I` option to inspect HTTP response headers and observed the WordPress REST API endpoint (`/wp-json/`).
- **Wafw00f:** Identified ModSecurity (SpiderLabs) as the Web Application Firewall.
- **DNSRecon:** Enumerated DNS records, including name servers, mail servers, SPF/TXT records, and service records.

These findings provided an overview of the domain's registration details, DNS configuration, web technologies, and security infrastructure.

### 4.2 Network Scanning with Zenmap

For the second activity, I used **Zenmap (Nmap GUI)** to perform network discovery within my own lab environment.

I first used the Linux `ip addr` command to identify my local IP address and network interface information. I then entered the target IP address into Zenmap and selected **Ping Scan** to check whether the Metasploitable 2 virtual machine was reachable.

The scan identified one live host:

- `192.168.122.76` — Metasploitable 2

Zenmap also provided host information, including the MAC address where available.

After completing the scan, I opened the **Topology** section in Zenmap, enabled the legend, and saved the network topology in PDF format as required by the practical task.

**Note:** This activity focused on identifying the Metasploitable 2 lab machine rather than scanning the entire subnet.

## 5. Risk Analysis / Impact

Based on the information collected during the footprinting and network scanning activities, I identified the following observations and potential risks.

| # | Risk / Finding | Evidence / Observation | Potential Impact | Risk Level |
|---|---|---|---|---|
| 1 | Web technology information exposed | WhatWeb identified WordPress and WP Download Manager. | May help attackers identify software versions and potential vulnerabilities. | **Low** |
| 2 | Server IP address identifiable | Nslookup resolved the domain to `192.232.216.135`. | Reveals the public IP address associated with the domain. | **Low** |
| 3 | HTTP technical information exposed | Curl returned HTTP headers and showed `/wp-json/`. | May assist technology fingerprinting and further enumeration. | **Low** |
| 4 | WAF technology identifiable | Wafw00f identified ModSecurity (SpiderLabs). | Reveals information about the website's security infrastructure. | **Low** |
| 5 | DNS infrastructure information exposed | DNSRecon identified DNS, mail, and service-related records. | Helps build a profile of the domain's infrastructure. | **Low** |
| 6 | Metasploitable 2 host identified | Zenmap Ping Scan confirmed that `192.168.122.76` was reachable. | Confirms that the lab target is available on the local network. | **Informational** |

**Risk Level Key:** Critical | High | Medium | Low | Informational

The findings above are observations from the footprinting and scanning exercises, not confirmed vulnerabilities. These activities primarily involved information gathering and host discovery. No exploitation or vulnerability validation was performed during these exercises.

The presence of information such as software versions, IP addresses, or DNS records does not automatically indicate a security vulnerability. Further authorized testing would be required to confirm any actual weaknesses.

## 6. Recommendations

Based on the observations from these activities, I recommend the following security improvements:

1. **Keep Software Updated:** Regularly update CMS platforms, plugins, and other web technologies.
2. **Review Information Exposure:** Avoid exposing unnecessary technical details through HTTP headers and website configurations.
3. **Secure DNS Records:** Regularly review DNS records and remove unnecessary entries.
4. **Monitor Network Devices:** Perform regular network scans and investigate unknown devices.
5. **Maintain Security:** Properly configure security tools and conduct regular authorized security assessments.

## 7. Conclusion

During Week 2 of my Cybersecurity & Ethical Hacking internship at Networkwalks, I completed practical activities covering network footprinting, reconnaissance, and network scanning.

In the footprinting activity, I used six Kali Linux tools to collect information about the `networkwalks.com` domain. I learned how WHOIS provides domain registration details, WhatWeb identifies web technologies, Nslookup resolves domain names, Curl inspects HTTP headers, Wafw00f identifies WAF technologies, and DNSRecon enumerates DNS records.

In the network scanning activity, I used Zenmap to discover an active host and verify that my Metasploitable 2 virtual machine was reachable within my own lab network.

These exercises improved my understanding of information gathering, network discovery, and security assessment. I also gained experience analyzing technical findings, documenting evidence, and identifying potential security risks.

Finally, I learned the importance of conducting reconnaissance and scanning activities within an authorized scope.

# 8. Evidences Collected

*Screenshots collected as evidence during the activities (stored in the `screenshots/` folder):*

![whois output](screenshots/whois.png)

![whatweb output](screenshots/whatweb.png)

![nslookup output](screenshots/nslookup.png)

![curl output](screenshots/curl.png)

![wafw00f output](screenshots/wafw00f.png)

![dnsrecon output](screenshots/zenmap.png)

![Zenmap scan and topology](screenshots/zenmap2.png)

**End of Week 2 Report**
