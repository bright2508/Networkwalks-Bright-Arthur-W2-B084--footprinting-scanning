# Networkwalks-Bright-Arthur-W2-B084--footprinting-scanning


# Week 02: Footprinting, Reconnaissance & Network Scanning

## Cybersecurity & Ethical Hacking Internship | NETWORKWALKS

## Project Overview

This project documents my Week 02 practical activities as part of the Cybersecurity Internship Program at Networkwalks. The exercises focused on two important stages of penetration testing: **footprinting and reconnaissance**, followed by **network scanning and host discovery**.

The first exercise involved gathering publicly available information about the `networkwalks.com` domain using different Kali Linux reconnaissance tools. The second exercise focused on discovering active devices on my local network using Zenmap, the graphical interface for Nmap.

These practical sessions helped me understand how security professionals collect information about a target environment, identify network-connected devices, analyze technical information, and document potential security concerns before conducting further security assessments.

## Project Objectives

The primary objectives of this project were to:

- Gather publicly available information about a domain using reconnaissance tools.
- Identify domain registration and DNS-related information.
- Examine website technologies and HTTP response headers.
- Determine whether a Web Application Firewall (WAF) is present.
- Discover active devices within a local network.
- Identify IP and MAC addresses associated with discovered hosts.
- Generate a network topology using Zenmap.
- Analyze observations and recommend appropriate security improvements.
- Practice responsible security documentation and reporting.

## Laboratory Environment

| Component                | Description                                                    |
| ------------------------ | -------------------------------------------------------------- |
| Operating Systems        | Kali Linux and Windows                                         |
| Reconnaissance Platform  | Kali Linux                                                     |
| Network Scanning Tool    | Zenmap                                                         |
| Network Discovery Tool   | Nmap                                                           |
| Domain Under Assessment  | `networkwalks.com`                                             |
| Network Under Assessment | My own local LAN                                               |
| Training Program         | Networkwalks Cybersecurity Internship                          |
| Modules Completed        | W2-PM1 – Multiple Kali Tools; W2-PM5 – Zenmap Scanning         |
| Assessment Activities    | Footprinting, Reconnaissance, Host Discovery                   |
| Authorization            | Written permission secured for the applicable assessment scope |

## Authorization & Ethical Considerations

All practical activities were conducted within an authorized educational environment. The domain assessment was performed under the permission provided for the training exercise, while network scanning was restricted to my own local network.

The tools and techniques discussed in this repository are intended strictly for cybersecurity education, research, and authorized security assessments.

Unauthorized access or testing against systems without appropriate permission may violate applicable laws and regulations. Users are responsible for ensuring that their activities remain within an approved scope.

---

## Tools and Their Applications

The following tools were used during the practical exercises.

| Tool        | Application                                                                                 |
| ----------- | ------------------------------------------------------------------------------------------- |
| WHOIS       | Retrieve publicly available domain registration information and name server details.        |
| WhatWeb     | Identify technologies, platforms, and web application components associated with a website. |
| Nslookup    | Resolve domain names into IP addresses through DNS queries.                                 |
| Curl        | Retrieve HTTP response headers and inspect server responses.                                |
| Wafw00f     | Identify possible Web Application Firewall technologies.                                    |
| DNSRecon    | Gather DNS-related information, including name servers, mail servers, and other records.    |
| Zenmap      | Discover active network hosts and visualize network topology.                               |
| Windows CMD | Obtain local IP address, subnet, and network interface information.                         |

---

## 1. Footprinting and Reconnaissance

### Overview

The first phase involved gathering information about the `networkwalks.com` domain using six reconnaissance tools available in Kali Linux.

Each tool provided a different perspective on the target's publicly observable infrastructure and web technologies.

### 1.1 WHOIS – Domain Information Gathering

WHOIS was used to examine publicly available registration information associated with the domain.

The information collected included domain registration details and name server information, helping establish an initial understanding of the domain's registration and DNS infrastructure.

### 1.2 WhatWeb – Website Technology Identification

WhatWeb was used to identify technologies and components associated with the website.

The results indicated the presence of:

- WordPress 7.0.4
- WP Download Manager 3.3.58

The output also provided additional information about the website's technology environment.

This exercise demonstrated how publicly observable technology details can help security professionals understand the components supporting a web application.

### 1.3 Nslookup – Domain Name Resolution

Nslookup was used to resolve the domain name into its corresponding IP address.

**Observed result:**

```text
192.232.216.135
```

This provided an IP address associated with the domain during the assessment.

### 1.4 Curl – HTTP Header Inspection

The Curl utility was used with the `-I` option to retrieve the website's HTTP response headers.

The output provided additional technical information about the web server's response and revealed the WordPress REST API endpoint:

```text
/wp-json/
```

This activity helped demonstrate how HTTP headers and publicly accessible application endpoints can contribute to the reconnaissance process.

### 1.5 Wafw00f – Web Application Firewall Identification

Wafw00f was used to investigate whether the website was protected by a Web Application Firewall.

The tool identified:

```text
ModSecurity (SpiderLabs)
```

This finding provided an indication of the WAF technology associated with the target website.

### 1.6 DNSRecon – DNS Record Enumeration

DNSRecon was used to gather additional information about the domain's DNS configuration.

The results provided information relating to:

- Name servers (NS)
- Mail servers (MX)
- SPF and TXT records
- Service records (SRV)
- DNS-related infrastructure information

This exercise demonstrated the importance of DNS information during the early stages of a security assessment.

---

## 2. Network Scanning and Host Discovery with Zenmap

### Overview

The second practical exercise focused on identifying active devices connected to my local network.

Zenmap was used to visualize the scanning process and identify hosts responding within the selected subnet.

### 2.1 Identifying the Local Network

Before beginning the scan, the Windows Command Prompt was used to obtain the local network configuration.

The following command was executed:

```cmd
ipconfig
```

This helped identify the local IP address and network configuration required to determine the appropriate scanning range.

### 2.2 Discovering Active Hosts

After identifying the network subnet, it was entered into Zenmap for host discovery.

The **Ping Scan** option was selected to identify devices responding within the specified network range.

The sample practical results showed the following active hosts:

| No. | IP Address |
| --- | ---------- |
| 1   | 10.0.0.1   |
| 2   | 10.0.0.4   |
| 3   | 10.0.0.19  |
| 4   | 10.0.0.5   |

The example results also contained MAC address information for the discovered devices.

> **Important:** These addresses are sample results from the reference practical. Replace them with the actual IP addresses and MAC addresses obtained from your own authorized network scan before publishing your project.

### 2.3 Network Topology Visualization

Following the host discovery exercise, the Topology section in Zenmap was used to visualize the discovered network devices.

The topology view was configured with the legend enabled, and the resulting network diagram was saved in PDF format as part of the practical documentation.

This provided a visual representation of the discovered network environment and demonstrated how network topology visualization can support network documentation and security analysis.

---

## 3. Findings and Risk Assessment

The reconnaissance and network discovery activities revealed several observations that may be relevant during a security assessment.

The findings below represent potential security considerations rather than confirmed vulnerabilities.

| No. | Observation                                                     | Security Implication                                                                                     | Risk Level |
| --- | --------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------- | ---------- |
| 1   | Website technology information was identified through WhatWeb.  | Public technology details may assist further software security research and assessment.                  | Medium     |
| 2   | The domain resolved to an identifiable IP address.              | The IP address provides information about the network location of the web service.                       | Low        |
| 3   | HTTP headers and the `/wp-json/` endpoint were observable.      | Application responses may expose technical information useful during further enumeration.                | Low        |
| 4   | ModSecurity was identified by Wafw00f.                          | Identification of the WAF technology provides information about the application's security architecture. | Low        |
| 5   | DNSRecon collected DNS and service-related records.             | DNS information may contribute to a broader understanding of the domain's infrastructure.                | Medium     |
| 6   | Multiple devices were discovered during local network scanning. | Unrecognized or unmanaged devices may require further investigation and verification.                    | Medium     |

### Risk Assessment Notes

The observations recorded during these exercises should not automatically be interpreted as security weaknesses.

Identifying a software platform, IP address, DNS record, or security technology does not independently establish that a system is vulnerable.

The activities covered information gathering and network discovery only. No exploitation or vulnerability validation was performed during these modules.

Any suspected security issue would require additional authorized investigation before being classified as a confirmed vulnerability.

---

## 4. Security Recommendations

Based on the observations made during the practical exercises, the following security measures are recommended.

### 4.1 Review Publicly Exposed Technology Information

Organizations should periodically evaluate the technical information their websites disclose publicly, including information about application platforms, plugins, and supporting technologies.

### 4.2 Maintain Updated Software

Web applications, content management systems, plugins, and supporting components should be regularly updated.

Security advisories should be reviewed to identify relevant patches and potential security improvements.

### 4.3 Evaluate HTTP Response Headers

HTTP response headers should be examined to determine whether unnecessary technical information is exposed.

Where appropriate, organizations should implement suitable security headers and review their configuration.

### 4.4 Regularly Audit DNS Records

DNS configurations should be reviewed periodically to ensure that records remain accurate and that unnecessary services or information are not exposed.

### 4.5 Configure and Monitor Web Application Firewalls

Organizations should maintain appropriate WAF configurations and review their effectiveness.

Where ModSecurity is deployed, its rules should be properly configured, monitored, and maintained to support the organization's security requirements.

### 4.6 Perform Periodic Internal Network Discovery

Regular network discovery exercises can help organizations maintain visibility into connected devices and identify unexpected changes within their infrastructure.

### 4.7 Investigate Unrecognized Network Devices

Devices that cannot be immediately identified should be investigated to establish their ownership, purpose, and authorization status.

### 4.8 Maintain Accurate Network Documentation

Network diagrams, device inventories, IP address assignments, and related infrastructure documentation should be maintained and updated whenever changes occur.

### 4.9 Ensure Proper Authorization for Security Testing

All reconnaissance, scanning, and security assessment activities should be conducted within a clearly defined and approved scope.

---

## 5. Key Learning Outcomes

This practical exercise strengthened my understanding of several fundamental cybersecurity concepts.

### Footprinting and Reconnaissance

I gained practical exposure to collecting publicly available information about a domain and understanding how different reconnaissance tools contribute to information gathering.

### Web Technology Identification

I learned how WhatWeb can identify web application technologies and how this information contributes to an initial understanding of a website's technical environment.

### DNS Analysis

Using Nslookup and DNSRecon helped me understand domain resolution and the role DNS records play in identifying infrastructure information.

### HTTP Response Analysis

Curl provided practical experience in examining HTTP response headers and identifying application-related information exposed through web responses.

### WAF Identification

Wafw00f demonstrated how security professionals can identify technologies associated with web application protection.

### Network Discovery

Using Zenmap helped me understand how to discover active devices within a network and identify their associated IP and MAC addresses.

### Network Topology Visualization

I gained experience generating a visual representation of discovered network hosts and documenting network relationships using Zenmap.

### Security Documentation

The exercises reinforced the importance of presenting technical observations clearly, assessing their potential implications, and recommending appropriate security improvements.

### Ethical Security Testing

I developed a stronger appreciation for the importance of authorization, defined assessment boundaries, and responsible use of cybersecurity tools.

---

## 6. Conclusion

Week 02 provided an opportunity to apply practical cybersecurity techniques in the areas of footprinting, reconnaissance, and network scanning.

Through the use of multiple Kali Linux tools, I explored how publicly available domain information, website technologies, HTTP responses, and DNS records can contribute to an initial understanding of a target environment.

The Zenmap exercise introduced me to local network discovery, host identification, IP and MAC address analysis, and network topology visualization.

Beyond the technical activities, the practical strengthened my understanding of how reconnaissance findings should be documented, evaluated, and communicated in a professional security report.

Overall, this project represents an important step in developing my practical cybersecurity skills and building a foundation for further learning in ethical hacking, penetration testing, and network security.

---

## 7. Evidence and Documentation

Screenshots and supporting evidence from the practical exercises should be organized in this section.

Suggested evidence structure:

```text
Week-02-Footprinting-Network-Scanning/

```

Evidence may include:

- WHOIS output
- WhatWeb technology identification results
- Nslookup domain resolution output
- Curl HTTP response headers
- Wafw00f WAF identification results
- DNSRecon enumeration results
- Zenmap host discovery screenshots
- Network topology PDF

---

## Author

**Name:** [Your Name]
**Role:** Aspiring Cybersecurity Professional
**Program:** Networkwalks Cybersecurity Internship
**Project:** Week 02 – Footprinting & Network Scanning

## Disclaimer

This repository is intended for educational and research purposes. All security testing must be conducted on systems owned by the tester or with explicit authorization from the relevant system owner.

The author does not support or encourage unauthorized access, malicious activities, or the misuse of cybersecurity tools.

---

*Documented as part of my ongoing cybersecurity learning journey.*
