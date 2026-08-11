# Darwin-SOC-macOS-Forensics-Artifact-Investigation-Lab
Hands-on macOS forensic investigation analyzing system, network, user, execution, Finder, and connected-device artifacts using TryHackMe, Linux, APOLLO, and KnowledgeC.

---

## Skills Demonstrated

- macOS Forensics
- Digital Forensics
- SOC Investigation
- DFIR
- Endpoint Analysis
- Artifact Analysis
- APFS Disk Analysis
- Linux Command Line
- APOLLO Forensics
- KnowledgeC Analysis
- System Log Analysis
- User Activity Analysis
- Network Artifact Analysis
- Command Execution Analysis
- Timeline Reconstruction
- Finder Artifact Analysis
- Bluetooth Artifact Analysis
- Evidence Documentation
- Incident Investigation

---

## Tools Used

- TryHackMe
- Linux
- APFS-FUSE
- APOLLO
- KnowledgeC.db
- Terminal
- grep
- zgrep
- strings
- find
- stat

---

# Investigation Process

## Screenshot 1 – macOS Forensics Lab Overview

Started the TryHackMe **macOS Forensics: Artefacts** room and reviewed the forensic investigation objectives.

The lab covered:

- System Information
- Network Information
- Account Activity
- Evidence of Execution
- File System Activity
- Connected Devices

![Screenshot 1 - macOS Forensics Lab Overview](01-macOS-Forensics-Lab-Overview.png)

---

## Screenshot 2 – APFS Data Volume Mount

Mounted the macOS forensic disk image using `apfs-fuse`.

Command used:

`apfs-fuse -v 4 mac-disk.img ~/mac`

The Data volume was selected so forensic artifacts could be examined from the attached Linux virtual machine.

This step provided access to the mounted macOS file system for further investigation.

![Screenshot 2 - APFS Data Volume Mount](02-macOS-APFS-Data-Volume-Mount-Verified.png)

---

## Screenshot 3 – macOS System Information

Reviewed the macOS system information artifact located at:

`/System/Library/CoreServices/SystemVersion.plist`

This artifact can provide information such as the installed macOS version, build version, and other operating-system details.

Identifying the operating system is important during a forensic investigation because artifact locations and available evidence can vary between macOS versions.

![Screenshot 3 - macOS System Information](03-macOS-System-Information-OS-Version.png)

---

## Screenshot 4 – System Information Verified

Analyzed macOS artifacts and historical system logs to identify important system information.

### Verified Findings

- OS Installation Date: `2024-12-08 17:42:28`
- Country Code: `AE`
- Last Boot Time: `2025-01-19 15:47:05 GMT`

Example command used:

`zgrep BOOT_TIME root/private/var/log/system.log*`

The historical boot records helped establish when the machine was last started and contributed to the forensic timeline.

![Screenshot 4 - System Information Verified](04-macOS-System-Information-Verified.png)

---

## Screenshot 5 – Network Artifact Investigation

Investigated macOS networking artifacts to identify network-interface and routing information.

### Verified Findings

- Built-in Network Interface: `en0`
- Router IP Address: `192.168.64.1`

Network artifacts can help investigators determine which network interfaces were active and which gateways or routers the endpoint previously communicated with.

This type of evidence can support investigations involving suspicious network activity, compromised endpoints, or unauthorized connections.

![Screenshot 5 - Network Artifact Investigation](05-macOS-Network-Artifact-Investigation.png)

---

## Screenshot 6 – Account Activity Verified

Investigated macOS user-account artifacts and historical system logs to identify account activity.

### Verified Findings

- Last Logged-In User: `thm`
- Password Hint: `count to 5`
- Last Logout Time: `Jan 19 07:52:43`

Example command used:

`zgrep -i "logout" root/private/var/log/system.log*`

This evidence helped establish which user was active on the system and when the user session ended.

Account artifacts are valuable during investigations involving unauthorized access, insider threats, or compromised credentials.

![Screenshot 6 - Account Activity Verified](06-macOS-Account-Activity-Verified.png)

---

## Screenshot 7 – Evidence of Execution Verified

Used the APOLLO forensic framework and the macOS KnowledgeC database to investigate application usage and command execution.

The user-level KnowledgeC database was located at:

`/Users/thm/Library/Application Support/Knowledge/knowledgeC.db`

### Verified Findings

- Last Command Executed: `vim creds.txt`
- Terminal Session GUID: `452AEA93-AEE7-420B-871E-C57053E15DD0`
- Terminal Closed: `2025-01-19 15:52:33`
- Terminal Focus Duration: `176 seconds`

This evidence demonstrated how macOS activity databases can be used to reconstruct user actions and application activity.

Command-execution evidence is especially valuable during SOC and DFIR investigations because it can reveal suspicious commands, unauthorized activity, or attacker behavior.

![Screenshot 7 - Evidence of Execution Verified](07-macOS-Evidence-of-Execution-Verified.png)

---

## Screenshot 8 – File System Activity Verified

Analyzed macOS Finder artifacts to identify user file-system activity and folder-view preferences.

### Verified Findings

- `/Users/thm` View Setting: `Open in list view`
- Last Finder Directory: `Recents`

Finder artifacts can help determine which folders or files a user recently accessed.

This evidence can support investigations involving suspicious file access, unauthorized data handling, or user activity reconstruction.

![Screenshot 8 - File System Activity Verified](08-macOS-File-System-Activity-Verified.png)

---

## Screenshot 9 – Connected Devices Verified

Reviewed macOS KnowledgeC artifacts associated with connected Bluetooth devices.

### Verified KnowledgeC Stream

`Bluetooth/isConnected`

This stream can provide evidence about Bluetooth connection states and connected peripherals.

Connected-device artifacts can be useful during forensic investigations involving removable devices, wireless peripherals, unauthorized hardware, or possible data-transfer activity.

![Screenshot 9 - Connected Devices Verified](09-macOS-Connected-Devices-Verified.png)

---

## Screenshot 10 – Lab Completion

Successfully completed the TryHackMe **macOS Forensics: Artefacts** room at 100%.

The investigation included:

- macOS system-information analysis
- APFS disk-image mounting
- Network artifact analysis
- User-account investigation
- Historical login and logout analysis
- Command-execution reconstruction
- APOLLO and KnowledgeC analysis
- Finder activity investigation
- File-system artifact analysis
- Connected-device investigation
- Forensic timeline development

![Screenshot 10 - macOS Forensics Lab Completed](10-macOS-Forensics-Lab-Completed.png)

---

# Key Findings

| Category | Finding |
|---|---|
| OS Installation Date | `2024-12-08 17:42:28` |
| Country Code | `AE` |
| Last Boot | `2025-01-19 15:47:05 GMT` |
| Network Interface | `en0` |
| Router IP | `192.168.64.1` |
| Last Logged-In User | `thm` |
| Password Hint | `count to 5` |
| Last Logout | `Jan 19 07:52:43` |
| Last Command | `vim creds.txt` |
| Terminal Session GUID | `452AEA93-AEE7-420B-871E-C57053E15DD0` |
| Terminal Closed | `2025-01-19 15:52:33` |
| Terminal Focus Time | `176 seconds` |
| Finder View | `Open in list view` |
| Last Finder Directory | `Recents` |
| Bluetooth Stream | `Bluetooth/isConnected` |

---

# SOC / DFIR Relevance

This project demonstrates hands-on skills relevant to SOC Analyst, Cybersecurity Analyst, Incident Response, and DFIR roles.

Key SOC and DFIR skills practiced include:

- Endpoint forensic investigation
- macOS artifact identification
- Evidence collection
- System log analysis
- User-account investigation
- Command-execution reconstruction
- Network artifact analysis
- Timeline reconstruction
- Application activity analysis
- File-system investigation
- Connected-device analysis
- Linux-based forensic analysis
- Technical documentation

These techniques can support investigations involving:

- Suspicious endpoint behavior
- Account compromise
- Unauthorized access
- Malware execution
- Insider threats
- Suspicious command activity
- Unauthorized device connections
- Data-access investigations
- Incident response

---

# What I Learned

This lab strengthened my understanding of how forensic evidence is stored on macOS systems and how different artifacts can be combined to reconstruct system and user activity.

I gained hands-on experience working with:

- APFS disk images
- macOS plist artifacts
- Historical system logs
- KnowledgeC databases
- APOLLO forensic tooling
- Finder artifacts
- Bluetooth artifacts
- Linux forensic commands

The investigation also reinforced the importance of validating findings through multiple sources of evidence rather than relying on a single artifact.

---

# Conclusion

This project provided hands-on experience investigating a macOS forensic disk image and extracting useful evidence from system files, historical logs, preference files, Finder artifacts, account information, and the KnowledgeC database.

Using Linux command-line tools and APOLLO, I was able to identify system information, investigate network activity, reconstruct user sessions, recover command-execution evidence, examine Finder activity, analyze connected devices, and document the findings in a structured forensic investigation.

Completing this lab expanded my SOC and incident-response experience beyond Windows environments and strengthened my ability to investigate macOS endpoints using practical DFIR techniques.
