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

## 2. Network Scanning and Host Discovery with Zenmap

### Overview

The second practical exercise focused on examining my Windows 11 machine using Zenmap, the graphical interface for Nmap. The scan was performed to identify open TCP ports, associated services, and operating system information.

This exercise provided practical experience in understanding how network scanning can reveal a host's exposed services and provide useful information for security assessment.

### 2.1 Identifying the Local Network Configuration

Before initiating the scan, I used the Windows Command Prompt to retrieve my network configuration.

```cmd
ipconfig
```

The command returned the following information:

| Network Configuration | Result |
|---|---|
| IPv4 Address | `10.176.196.83` |
| Subnet Mask | `255.255.255.0` |
| Network Prefix | `/24` |
| Operating System | Windows 11 |

These details helped me understand the network configuration of the machine selected for the practical exercise.

### 2.2 Port Scanning and Service Identification

I used Zenmap to scan my Windows 11 machine and examine the TCP ports that were accessible during the assessment.

The scan identified four open TCP ports and reported 996 closed TCP ports.

The following table summarizes the open ports and their associated services.

| Port | State | Service | Description |
|---|---|---|---|
| 135/TCP | Open | MSRPC | Microsoft Windows RPC |
| 139/TCP | Open | NetBIOS-SSN | Microsoft Windows NetBIOS Session Service |
| 445/TCP | Open | Microsoft-DS | Microsoft SMB-related service |
| 5357/TCP | Open | HTTP | Microsoft HTTPAPI 2.0 |

These results demonstrated how port scanning can help identify network-accessible services running on a Windows machine.

### 2.3 Operating System Detection

Zenmap also performed operating system detection and identified the scanned host as Microsoft Windows 11.

The scan returned the following information:

| Detection Parameter | Result |
|---|---|
| Operating System | Microsoft Windows 11 |
| OS Details | Windows 11 24H2 – 25H2 |
| Device Type | General Purpose |
| Network Distance | 0 Hops |
| Host Status | Up |

The operating system detection feature provided additional information about the scanned machine and helped demonstrate how Nmap can identify characteristics of a target host.

### 2.4 SMB Security Observation

The host script results included an observation relating to Server Message Block (SMB) security configuration.

```text
SMB Message Signing: Enabled and Required
```

This indicated that SMB message signing was enabled and required on the scanned Windows machine.

The finding provided an opportunity to understand how network scanning can reveal security-related configuration information and support further assessment of a system's network services.

### 2.5 Scan Summary

The following table presents a summary of the scan results.

| Scan Metric | Result |
|---|---|
| IP Address Scanned | `10.176.196.83` |
| Hosts Scanned | 1 |
| Open TCP Ports | 4 |
| Closed TCP Ports | 996 |
| Total TCP Ports Reported | 1,000 |
| Scan Duration | 22.05 seconds |
| Raw Packets Sent | 1,016 |
| Raw Packets Received | 2,044 |

The scan completed successfully and provided information about the host's open ports, services, and operating system.

### 2.6 Network Scanning Observation

The exercise focused on a single Windows 11 host rather than discovering multiple devices across the entire local network.

The four open ports represented services available on the scanned machine, not four separate network devices.

This distinction helped me better understand the difference between host discovery and port scanning during a network security assessment.

---

## 3. Findings and Risk Assessment

The reconnaissance and network discovery activities revealed several observations that may be relevant during a security assessment.

The findings below represent potential security considerations rather than confirmed vulnerabilities.

| No. | Observation | Security Implication | Risk Level |
|---|---|---|---|
| 1 | Website technologies were identified through WhatWeb, including WordPress and WP Download Manager. | Public technology information may assist further software security research and assessment. | Medium |
| 2 | The domain resolved to an identifiable IP address (`192.232.216.135`). | The IP address provides information about the network location of the web service. | Low |
| 3 | HTTP response headers and the `/wp-json/` endpoint were observable. | Application responses may expose technical information useful during further enumeration. | Low |
| 4 | ModSecurity was identified by Wafw00f. | Identification of the WAF technology provides information about the application's security architecture. | Low |
| 5 | DNSRecon collected DNS and service-related records. | DNS information may contribute to a broader understanding of the domain's infrastructure. | Medium |
| 6 | Zenmap identified four open TCP ports on the scanned Windows 11 machine: 135, 139, 445, and 5357. | Network-accessible services should be reviewed to confirm that they are necessary and appropriately configured. | Medium |
| 7 | Microsoft RPC, NetBIOS Session Service, SMB-related functionality, and HTTPAPI were identified. | Service identification provides information about the host's network exposure and may support further security assessment. | Medium |
| 8 | SMB message signing was reported as enabled and required. | This represents a security configuration observation relevant to assessing Windows network services. | Informational |

### Risk Assessment Notes

The findings in this report reflect observations from reconnaissance and network scanning, not confirmed vulnerabilities.

The identification of website technologies, DNS records, open ports, or network services does not independently establish that a system is vulnerable.

The practical exercises focused on information gathering, service identification, and host scanning. No exploitation or vulnerability validation was performed.

Any potential security weakness would require additional authorized investigation before being classified as a confirmed vulnerability.

## 4. Security Recommendations

Based on the findings from the footprinting, reconnaissance, and network scanning exercises, the following security measures are recommended to improve the protection and management of web applications and network systems.

### 4.1 Review Publicly Exposed Technology Information

Organizations should regularly assess the technical information their websites make publicly available. Details relating to content management systems, plugins, and supporting technologies should be reviewed to identify unnecessary information exposure.

### 4.2 Maintain Updated Software

Web applications, content management systems, plugins, and supporting components should be kept up to date. Regular updates help address known security weaknesses and improve the overall security of the application environment.

### 4.3 Strengthen HTTP Security Configuration

HTTP response headers should be reviewed to identify unnecessary technical information and assess the availability of appropriate security headers. Organizations should apply suitable security configurations to help protect their web applications.

### 4.4 Review and Secure DNS Configurations

DNS records should be reviewed periodically to ensure that they are accurate, properly configured, and limited to required services. Unnecessary DNS records and service information should be evaluated to reduce avoidable information exposure.

### 4.5 Configure and Monitor Web Application Firewalls

Web Application Firewalls should be properly configured and regularly monitored to support the protection of web applications against malicious traffic and common web-based attacks.

Where ModSecurity is deployed, its security rules should be maintained and reviewed to ensure that the configuration remains appropriate for the application environment.

### 4.6 Review Open Network Ports and Running Services

The Zenmap scan identified four open TCP ports on the Windows 11 machine: 135, 139, 445, and 5357.

These ports are associated with Microsoft RPC, NetBIOS Session Service, SMB-related functionality, and HTTPAPI.

It is recommended that network administrators review these services to confirm that they are necessary for the machine's intended operation. Unnecessary services should be disabled, while required services should be appropriately configured and monitored.

### 4.7 Strengthen Windows Network Security

The identification of Windows network services highlights the importance of maintaining appropriate security configurations on Windows systems.

Organizations should review firewall settings, restrict network service access to trusted environments where appropriate, and ensure that operating systems receive regular security updates.

### 4.8 Maintain Appropriate SMB Security Configuration

The scan indicated that SMB message signing was enabled and required on the examined Windows machine.

This configuration should be maintained and periodically reviewed as part of Windows network security management. Organizations should also ensure that SMB access is appropriately restricted to authorized systems and users.

### 4.9 Monitor Network Devices and Maintain Accurate Documentation

Organizations should regularly review connected devices, maintain accurate IP address assignments, and document network infrastructure.

Unrecognized devices and unexpected changes in network activity should be investigated to establish their legitimacy and authorization status.

### 4.10 Ensure Proper Authorization for Security Testing

All reconnaissance, network scanning, and security assessment activities should be performed within an approved scope and with the necessary authorization.

Security findings should be properly documented, reviewed, and communicated to the relevant system owners.


## 5. Key Learning Outcomes

The practical activities completed during Week 02 provided valuable experience in footprinting, reconnaissance, and network scanning. The exercises strengthened my understanding of the following cybersecurity concepts:

### Footprinting and Reconnaissance

I developed practical experience in gathering publicly available information about a domain and using different reconnaissance tools to examine its digital footprint.

### Web Technology Identification

Using WhatWeb, I learned how to identify website technologies and understand how publicly observable application components contribute to the information available during an assessment.

### DNS Analysis

The use of Nslookup and DNSRecon improved my understanding of domain resolution, DNS records, and the role of DNS information in identifying domain-related infrastructure.

### HTTP Response Analysis

Curl provided practical exposure to retrieving HTTP response headers and identifying application-related information that may be observable through web responses.

### Web Application Firewall Identification

Wafw00f introduced me to the process of identifying Web Application Firewall technologies and understanding their role in web application protection.

### Host Scanning and Service Identification

Using Zenmap, I examined my Windows 11 machine and identified four open TCP ports associated with Microsoft RPC, NetBIOS Session Service, SMB-related functionality, and HTTPAPI.

This exercise helped me understand how port scanning and service identification provide information about a host's network exposure.

### Operating System Detection

I gained experience interpreting operating system detection results from Nmap and identifying characteristics of the scanned Windows 11 machine.

### SMB Security Configuration

The scan revealed that SMB message signing was enabled and required. This helped me understand how network scanning can provide security-related configuration observations about Windows systems.

### Security Documentation and Risk Assessment

The practical reinforced the importance of documenting technical findings accurately, distinguishing observations from confirmed vulnerabilities, and communicating potential security implications professionally.

### Ethical Security Testing

I strengthened my understanding of responsible security testing, authorization requirements, and the importance of conducting assessments within an approved scope.

---

## 6. Conclusion

Week 02 provided an opportunity for me to apply practical cybersecurity techniques in footprinting, reconnaissance, and network scanning.

Through the use of WHOIS, WhatWeb, Nslookup, Curl, Wafw00f, and DNSRecon, I explored different approaches to gathering publicly available domain information, identifying web technologies, examining HTTP responses, and understanding DNS-related infrastructure.

The Zenmap exercise allowed me to examine my Windows 11 machine, identify four open TCP ports, recognize their associated services, and review operating system detection information. I also observed SMB message signing as enabled and required, providing additional insight into Windows network security configuration.

Beyond the technical activities, these exercises strengthened my ability to interpret scanning results, document observations, assess potential security implications, and recommend appropriate security improvements.

Overall, this practical represents an important milestone in my cybersecurity learning journey and contributes to building a stronger foundation in ethical hacking, penetration testing, and network security.

---

## 7. Evidence and Documentation

Screenshots and supporting materials from the practical exercises are organized to provide visual evidence of the activities performed and the results obtained.

### Evidence Directory Structure

Week-02-Footprinting-Network-Scanning/
<img width="1917" height="982" alt="Image" src="https://github.com/user-attachments/assets/f7d5d6a4-e3c2-414e-b7ab-149e311999ba" />

<img width="1917" height="987" alt="Image" src="https://github.com/user-attachments/assets/11f7247d-05bd-4ba5-a37f-61c962eaabf2" />

<img width="1912" height="975" alt="Image" src="https://github.com/user-attachments/assets/ef09ac90-2f89-4c3f-a6bc-e627254fe580" />

<img width="1917" height="897" alt="Image" src="https://github.com/user-attachments/assets/77c1f65f-0728-4e90-9207-b8dd0bf330af" />

<img width="1917" height="907" alt="Image" src="https://github.com/user-attachments/assets/120faf4c-b9b3-4d6d-b37d-c136edd23a7e" />

<img width="1912" height="906" alt="Image" src="https://github.com/user-attachments/assets/0089fe72-fa23-49bb-a8d8-c79f803ae336" />

<img width="1905" height="991" alt="Image" src="https://github.com/user-attachments/assets/af99c513-cd4c-4aac-abf6-4d5a03ef65d2" />

<img width="1907" height="976" alt="Image" src="https://github.com/user-attachments/assets/1d529260-90c1-4eaa-acf1-56ee261b69c1" />

<img width="729" height="732" alt="Image" src="https://github.com/user-attachments/assets/8e805c81-6a70-4f66-a69c-c9ee81412fa2" />


Evidence includes:

- WHOIS output
- WhatWeb technology identification results
- Nslookup domain resolution output
- Curl HTTP response headers
- Wafw00f WAF identification results
- DNSRecon enumeration results
- Zenmap host discovery screenshots
- Network topology PDF


## Author

**Name:** Bright Arthur
**Role:** Cybersecurity Professional Intern
**Program:** Networkwalks Cybersecurity Internship
**Project:** Week 02 – Footprinting & Network Scanning
**LinkedIn:** [Bright Arthur](https://www.linkedin.com/in/brightarthur/)

## Disclaimer

This repository is intended for educational and research purposes. All security testing must be conducted on systems owned by the tester or with explicit authorization from the relevant system owner.

The author does not support or encourage unauthorized access, malicious activities, or the misuse of cybersecurity tools.


*Documented as part of my ongoing cybersecurity learning journey.*
