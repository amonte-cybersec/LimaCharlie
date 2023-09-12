<h2>Section 1: Initial Setup</h2> 

- Acquire a compatible Windows virtual machine (VM) from Microsoft to ensure compatibility with VMware Workstation.
- Download the Ubuntu Server 22.04.1 installer ISO from the VMWare Hypervisor website.
- During the Ubuntu installation in VMware Workstation, choose to set a static IP address for the Ubuntu VM, ensuring it remains constant throughout lab activities.
- Take note of the gateway IP address and subnet details.


 <p align="center">
  Screenshot of Victim (Windows VM) and Attacker (Linux VM) : <br/>
<img src="https://imgur.com/Amn3cY7.png" height="70%" width="80%" alt="Disk Sanitization Steps"/> 
<img src="https://imgur.com/Q69IE2U.png" height="70%" width="80%" alt="Disk Sanitization Steps"/>

<h2>Section 2: Windows VM Configuration</h2> 

- Disable Microsoft Defender's Tamper Protection and other options via the Windows Security settings.
- To ensure that Microsoft Defender doesn't interfere with lab tasks, use the Local Group Policy Editor and Registry Editor to permanently disable it.

<h2>Section 3: Environment Stability</h2> 

- Execute specific commands in an administrative command prompt to prevent the VM from entering standby mode, thereby avoiding interruptions during lab work.

<h2>Section 4: Security Tools Installation</h2> 

- Begin by downloading Sysmon, a powerful system monitoring tool, and SwiftOnSecurity's Sysmon configuration.
- Install Sysmon using the provided configuration while carefully validating the installation's success.
- Create an account on the LimaCharlie platform, set up an organization, and add a dedicated Windows sensor for the Windows VM.
- Download the LimaCharlie sensor executable and install it on the Windows VM using the provided command.
- Configure LimaCharlie to ship Sysmon event logs alongside its own Endpoint Detection and Response (EDR) telemetry for comprehensive visibility.

<h2>Section 5: Linux VM Setup</h2> 

- Establish an SSH connection to the Linux VM from the host system.
- Download Sliver, a Command & Control (C2) framework developed by BishopFox, and configure it within the Linux VM.
- To keep your work organized, create a dedicated working directory.
- Generate a C2 session payload using Sliver and store it in the /opt/sliver directory on the Linux VM.

<h2>Section 6: Payload Transfer</h2> 

- From the Linux VM, use a Python command to transfer the C2 payload to the Windows VM.
- In the Windows VM, launch an Administrative PowerShell console and download the C2 payload using the Linux VM's IP address.

<p align="center">
Screenshot of Payload successfully transferred: <br/>
<img src="https://imgur.com/ylXHumD.png" height="70%" width="80%" alt="Disk Sanitization Steps"/> 

<h2>Section 7: Threat Analysis</h2> 

- Use VirusTotal, a widely used online threat intelligence platform, for hash analysis of a suspicious file.
- Query VirusTotal to gather any associated information regarding the hash, which surprisingly returns no results, suggesting the file may have been
- custom-crafted to evade traditional antivirus detection.

<h2>Section 8: Exploring LimaCharlie's EDR Capabilities</h2> 

- Within LimaCharlie, observe the detection of a threat with a custom detection signature.
- Expand the detection entry to view the raw event and access the event timeline where the event occurred.

<p align="center">
Screenshot of Detections I created: <br/>
<img src="https://imgur.com/e3GLEPN.png" height="70%" width="80%" alt="Disk Sanitization Steps"/>

 <h2>Section 9: Performing Adversarial Actions</h2> 

- Simulate adversarial actions by conducting activities such as dumping lsass.exe, a common tactic used by adversaries to steal credentials on a system.
- Filter the LimaCharlie timeline for "SENSITIVE_PROCESS_ACCESS" events, allowing you to identify credential access attempts.
- Based on events targeting the lsass.exe process, build detection rules to enhance your lab's ability to focus on monitoring and flagging potential malicious activities involving lsass.exe. Capture relevant screenshots for documentation.

<h2>Conclusion</h2> 

This project has equipped me with essential technical skills, hands-on experience with cybersecurity tools, and the ability to conduct threat analysis and incident response effectively. It has strengthened my risk assessment capabilities, emphasized the importance of documentation and reporting, and honed my adaptive thinking. These skills and experiences will play a crucial role in my journey towards becoming a proficient cybersecurity analyst, where identifying and mitigating threats, customizing security measures, and responding to incidents are central to the role.




































<p align="center">
Screenshot of Victim (Windows VM) and Attacker (Linux VM) : <br/>

<img src="https://imgur.com/Amn3cY7.png" height="70%" width="80%" alt="Disk Sanitization Steps"/> 
<img src="https://imgur.com/Q69IE2U.png" height="70%" width="80%" alt="Disk Sanitization Steps"/> 

<p align="center">
Screenshot of Payload successfully transferred: <br/>
<img src="https://imgur.com/ylXHumD.png" height="70%" width="80%" alt="Disk Sanitization Steps"/> 

<p align="center">
Screenshot of Detections I created: <br/>
<img src="https://imgur.com/e3GLEPN.png" height="70%" width="80%" alt="Disk Sanitization Steps"/> 
 

