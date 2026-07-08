# Start Your Cyber Security Journey

*This module covers the offensive and defensive approaches to security, then the search skills and specialized resources used to research threats, tools, and vulnerabilities.*

[Offensive Security Introduction](#-offensive-security-introduction) · [Defensive Security Introduction](#-defensive-security-introduction) · [Search Skills](#-search-skills)

> Notes from the first section of TryHackMe's **Cyber Security 101** learning path.

## <img src="https://github.com/user-attachments/assets/14e8c19d-29b1-40ed-aecc-1ec8b53df85b" width="50" height="50" align="middle" alt="Offensive Security Introduction room icon"> Offensive Security Introduction

*This room covers the introduction to offensive security.*

**Offensive Security** is the practice of proactively attacking systems, networks, and applications, thinking and acting like an attacker, to find and exploit vulnerabilities before malicious actors do.

> Red teams are part of the offensive security landscape.

### Key Takeaways

Offensive security is about adopting an attacker's mindset to find weaknesses before real adversaries can exploit them. The work is proactive rather than reactive. Offensive practitioners deliberately probe systems, networks, and applications for exploitable flaws. Red teams operate in this space, emulating real-world attacks so that gaps can be identified and fixed before an attacker can reach them.

## <img src="https://github.com/user-attachments/assets/20883c6a-a6eb-49d1-bbb5-d850fe103e62" width="50" height="50" align="middle" alt="Defensive Security Introduction room icon"> Defensive Security Introduction

*This room covers the introduction to defensive security.*

**Defensive Security** is the practice of protecting systems and responding to threats, with a focus on preventing intrusions and detecting them when they occur.

> Blue teams are part of the defensive security landscape.

### Key Takeaways

Defensive security is the counterpart to offensive work. Its goal is to protect systems and to detect and respond to threats as they arise. It combines prevention, stopping intrusions before they succeed, with detection and response, identifying activity that slips through and acting on it. Blue teams operate in this space, monitoring environments and reacting to incidents to limit the damage an attacker can do.

## <img src="https://github.com/user-attachments/assets/27cff360-2059-4ebd-8e2c-dedd8f401dea" width="50" height="50" align="middle" alt="Search Skills room icon"> Search Skills

*This room covers the search of the Internet and the use of specialized services and technical docs for information.*

### Shodan

**Shodan** is a search engine for Internet-connected devices. Rather than indexing web pages, it scans and catalogs devices exposed to the Internet such as servers, webcams, routers, and industrial control systems, alongside the services and ports they have open. Security professionals use it for reconnaissance and to discover exposed or vulnerable systems.

### VirusTotal

**VirusTotal** is an online service that analyzes files, URLs, domains, and IP addresses for malicious content by running them against dozens of antivirus engines and threat-intelligence feeds at once. It's a staple for quickly checking whether something is known to be malicious, making it a common first stop in triage and investigation.

### Vulnerability Databases

**Common Vulnerabilities and Exposures** (CVE) is a publicly available, standardized list of known security vulnerabilities, each assigned a unique identifier in the format: CVE-YEAR-NUMBER.

> If the vulnerability is impactful enough, it may even get a moniker.

###### These vulnerabilities are given a score (CVSS) based on a variety of factors, such as:

- **Impact**: What damage can this vulnerability lead to?
- **Complexity**: Is the vulnerability easy to exploit or not?
- **Availability**: Are working exploits already publicly available, making exploitation more likely?

> Organizations use scoring like this to prioritize their level of risk, addressing the highest scoring first.

These identifiers function as a reference point among vendors, researchers, security tools, and documentation, ensuring that everyone discussing a vulnerability refers to the same issue.

### Technical Documentation

Each major security tool or platform provides its own documentation, which is more reliable and up-to-date than any third-party tutorials.

> When you're troubleshooting unexpected bevavior or trying to understand how to use a tool in a certain way, the official documentation should always be your first stop.

#### Linux Man Pages

The Linux manual pages serve as documentation that you can read within your terminal about any command on Linux, and a majority of cybersecurity tooling.

To view the manual page, run: `man <command>`

### GitHub

**GitHub** is a great resource for staying updated on the latest threats and vulnerabilities. Researchers often publish proof-of-concept (PoC) code, exploitation tools, and detailed technical reports there, which are usually faster than official channels.

Searching for a CVE identifier directly on GitHub often reveals repositories containing PoC code, scanner scripts, or detailed analyses of the vulnerability.

> Not all PoCs are equally reliable. Some are incomplete, some are intentionally flawed, and occasionally a "PoC" repository is malicious itself. Always verify what you're about to execute.

### Key Takeaways

Knowing where to look is as important in security work as knowing what to do with what you find. Specialized search engines like Shodan expose internet-facing devices and their open services, while VirusTotal checks files, URLs, and domains against many detection engines at once. Vulnerability databases assign every known flaw a standardized CVE identifier and a CVSS score, giving practitioners a shared reference point and a way to prioritize risk. Official documentation, Linux man pages, and community sources such as GitHub complete the toolkit, though any proof-of-concept pulled from a public repository should be verified before it is trusted or run.
