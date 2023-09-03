Step 1: Setting up My Virtual Environment

- I acquired a Windows virtual machine (VM) from Microsoft, ensuring it was compatible with VMware Workstation.
- To create a controlled environment, I downloaded the Ubuntu Server 22.04.1 installer ISO with from the VM Ware Hypervisor.
- During the installation of Ubuntu in VMware Workstation, I chose to set a static IP address for the Ubuntu VM, preventing it from changing throughout my lab activities. I also took note of the gateway IP and subnet details. Additionally, I copied the "Address" from the previously assigned DHCP settings.

<p align="center">
Screenshot of Victim (Windows VM) and Attacker (Linux VM) : <br/>

<img src="https://imgur.com/Amn3cY7.png" height="70%" width="80%" alt="Disk Sanitization Steps"/> 
<img src="https://imgur.com/zjAlFLV.png" height="70%" width="80%" alt="Disk Sanitization Steps"/> 

**Step 2: Disabling Microsoft Defender on My Windows VM**
- I disabled Tamper Protection and other options via Windows Security settings.
- To ensure that Microsoft Defender wouldn't interfere with my lab tasks, I used the Local Group Policy Editor and Registry Editor to permanently disable it.

**Step 3: Preventing Standby Mode**
- To prevent the VM from entering standby mode and interrupting my lab work, I executed specific commands in an administrative command prompt.

**Step 4: Installing Sysmon on My Windows VM**
- I started by downloading Sysmon and SwiftOnSecurity's Sysmon configuration.
- After downloading, I proceeded to install Sysmon using the provided configuration. I carefully validated that the installation was successful.

**Step 5: Installing LimaCharlie on My Windows VM**
- I created a LimaCharlie account on their platform, set up an organization, and added a Windows sensor dedicated to my Windows VM.
- Following the setup, I downloaded the LimaCharlie sensor executable and installed it using the provided command.
- To ensure comprehensive visibility, I configured LimaCharlie to ship Sysmon event logs alongside its own EDR telemetry.

**Step 6: Setting up the Attack System on My Linux VM**
- I established an SSH connection to my Linux VM from my host system.
- Next, I downloaded Sliver, a Command & Control (C2) framework developed by BishopFox, and configured it within my Linux VM.
- To organize my work, I created a working directory, generated a C2 session payload using Sliver, and stored it in the /opt/sliver directory on the Linux VM.

**Step 7: Transferring the C2 Payload to My Windows VM**
- From the Linux VM, I ran a Python command to transfer the C2 payload.
- In the Windows VM, I launched an Administrative PowerShell console and downloaded the C2 payload using the Linux VM's IP address.

<p align="center">
Screenshot of Payload successfully transferred: <br/>
<img src="https://imgur.com/ylXHumD.png" height="70%" width="80%" alt="Disk Sanitization Steps"/> 

**Step 8: Conducting Hash Analysis**
- For hash analysis of a suspicious file, I turned to VirusTotal, a widely used online threat intelligence platform.
- I queried VirusTotal to gather any associated information regarding the hash. Surprisingly, no results were returned, suggesting that the file might have been custom-crafted to evade traditional antivirus detection.

**Step 9: Exploring LimaCharlie's EDR Capabilities**
- Within LimaCharlie, I observed that a threat had been detected with my custom detection signature.
- I expanded the detection entry to view the raw event and accessed the event timeline where the event occurred.

<p align="center">
Screenshot of Detections I created: <br/>
<img src="https://imgur.com/e3GLEPN.png" height="70%" width="80%" alt="Disk Sanitization Steps"/> 
 

**Step 10: Performing Adversarial Actions**
- To simulate adversarial actions, I conducted activities like dumping lsass.exe, a common tactic used by adversaries to steal credentials on a system.
- I filtered the LimaCharlie timeline for "SENSITIVE_PROCESS_ACCESS" events, allowing me to identify credential access attempts.
- Based on the events targeting the lsass.exe process, I built detection rules, enhancing my lab's ability to focus on monitoring and flagging potential malicious activities involving lsass.exe.

**Conclusion:**
- In conclusion, this lab provided me with valuable hands-on experience in various aspects of cybersecurity.
- I successfully set up virtual machines, performed security configurations, and conducted adversarial simulations.
- My understanding of Security Operations was significantly enhanced, and I developed better detection and response capabilities to address cyber threats effectively.
