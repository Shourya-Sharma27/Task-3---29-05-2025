# Task-3---29-05-2025

Vulnerability Assessment Using Nessus

This project focuses on conducting a vulnerability scan on a Windows machine using Tenable Nessus, a powerful tool for identifying known security issues 
in operating systems and installed software. The task walks through each step, from installation to identifying and mitigating high-risk vulnerabilities, 
with emphasis on documenting actionable insights.

1. Installation and Setup
 The first step involved installing Nessus Professional on a Kali Linux virtual machine. The process included:
 •	Downloading Nessus 10.8.4 from Tenable’s official site.
 •	Installing the .deb package via:
      bash 
      CopyEdit
      dpkg -i Nessus-10.8.4-debian6_amd64.deb
 •	Starting the Nessus service:
      bash
      CopyEdit
      /bin/systemctl start nessusd.service
 •	Registering and activating a trial license using an email (admin@root.com).
 •	Setting up login credentials and completing the initial configuration.

2. Targeting a Localhost Windows Machine
 The vulnerability scan targeted a fresh Windows installation hosted on VMware:
 •	Target IP: 192.168.141.131
 •	The machine had deliberately introduced vulnerabilities for testing purposes.

3. Starting a Full Vulnerability Scan
 •	From the Nessus dashboard, a new advanced scan was created.
 •	Target IP and scan parameters were set under the custom configuration.
 •	After initialization, Nessus performed a full scan against the Windows host.
4. Reviewing the Results
 The scan reported a total of 311 vulnerabilities, classified as follows:
  Severity	Count
    Critical - 37
    High -     73
    Medium -   27
    Low	 -     1
    Info -     173
This classification helps prioritize remediation based on risk and exploitability.

5. Documenting Critical Vulnerabilities
 The critical vulnerabilities included outdated system components and well-known security flaws. Key examples:
•	Missing Windows Security Updates (2020–2024):
• KB4551853, KB5003171, KB5039217
•	Apache Log4j 1.x vulnerabilities (RCE risk)
•	Adobe Flash Player <= 32.0.0.371 (End-of-life, high exploitability)
•	Microsoft Message Queuing (MSMQ) – CVE-2023-21554
•	Mozilla Firefox < 128.0
•	Oracle Java (April 2024 CPU) – RCE vulnerabilities

6. Remediation Strategy
 Each critical issue was reviewed for fixability and immediate mitigation steps. Remedies include:
 1. Windows Security Updates
 •	Use Windows Update, WSUS, or SCCM to apply latest patches for:
   •	Windows 10 v1809
   •	Windows Server 2019
 2. Apache Log4j 1.x
   •	Replace with Log4j 2.17.1+
   •	Remove legacy JARs, restart services
 3. Adobe Flash Player
   •	Uninstall via Control Panel or use Adobe’s official uninstaller
 4. Microsoft Message Queuing
   •	If unused, disable with:
bash
CopyEdit
dism /Online /Disable-Feature /FeatureName:MSMQ-Server
   •	Else, patch using Microsoft’s security update
 5. Firefox < 128.0
   •	Upgrade to latest version from Mozilla.org 
 6. Oracle Java
   •	Uninstall outdated versions
   •	Install the latest supported LTS version (e.g., Java 17 or 21)
7. Saving Results
Scan reports were saved within Nessus in HTML and CSV format for documentation and audit purposes. Exporting options in Nessus include:
   •	PDF
   •	HTML
   •	CSV
Here PDF format file has been attached for reference

•	Conclusion
This task demonstrates the critical role of vulnerability scanning in maintaining system security. By using Nessus, key risks were identified, prioritized,
and addressed with effective solutions. Regular scans and patch management are essential in mitigating exploit risks and securing IT environments.
