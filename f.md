Step 1: Analyzing the Compromised Workstation

During my analysis, I observed unusual login activity on the compromised workstation. Whenever a user logs in, a Command Prompt window automatically opens, displaying a list of images being uploaded to an undisclosed location. This raises suspicions and indicates a compromise.

Step 2: Determining the Attacker's Objective

Further investigation reveals that the attacker's objective is to exfiltrate files from the workstation, specifically images from the "C:/Systemcore/library" directory. I discovered an "upload.ps1" script in the "C:\Systemcore" folder, which facilitates the exfiltration process. This script is designed to upload files from the source directory ("C:\Systemcore\library") to a remote FTP server at "ftp://dlpuser:rNrKYTX9g7z3RgJRmxWuGHbeu@ftp.dlptest.com."

Step 3: Identifying Persistence Mechanisms

To maintain unauthorized access to the compromised workstation, the attacker employs a persistence mechanism. I found a script named "Untitled4.ps1" scheduled to execute "Untitled2.ps1" daily at 3 am. Additionally, "Untitled2.ps1" is triggered during user logins, ensuring persistent unauthorized access.

Step 4: Restoration and Mitigation Measures

To restore the compromised system's security, I recommend the following mitigation measures:

    Removal of suspicious scheduled tasks: Eliminate the "Untitled4.ps1" script and associated tasks to prevent further unauthorized execution.
    Deletion of PowerShell scripts: Remove all PowerShell scripts, including "Upload.ps1," to disable the exfiltration mechanism.
    Network-wide investigation: Extend the investigation to other systems within the network. Look for similar files, scheduled tasks, or indicators of compromise. Utilize network monitoring tools such as Intrusion Detection Systems (IDS) or packet sniffers to identify potential compromises and block malicious traffic.

Step 5: Network-Wide Compromise Assessment

To assess if other systems in the network have been compromised using the same malware, follow these steps:

    Searching for common files and scheduled tasks: Conduct a systematic search for files and scheduled tasks resembling those found on the compromised workstation.
    Network traffic analysis: Utilize IDS or packet sniffers to identify any packets originating from or destined for the identified FTP server. Monitor and block such traffic to detect potential compromises across the network.

By diligently following these investigation procedures and implementing the recommended mitigation measures, you can restore the compromised workstation's security and safeguard the broader network against potential threats.


Step 6: Recommendations for Future Prevention

To prevent similar methods from being successful in the future and enhance overall system security, consider the following recommendations:

    Strengthen access controls: Review and improve user access controls, employing the principle of least privilege to limit unauthorized access to sensitive files and directories.

    Keep software up to date: Regularly update and patch all software, including operating systems, applications, and security tools, to address vulnerabilities and protect against known threats.

    Provide security awareness training: Educate users on best practices for maintaining a secure environment, including strong passwords, recognizing phishing attempts, and avoiding suspicious downloads or websites.

    Implement network segmentation: Separate the network into segments or zones to limit the impact of a compromise and prevent lateral movement by attackers. Consider isolating workstations that do not require FTP access from those that do.

    Configure firewall rules: Utilize a firewall solution to control inbound and outbound traffic. Configure firewall rules to block FTP ports (typically port 21 for FTP control connection and port range 20-21 for FTP data connections) for workstations that do not need FTP access.

    Enable robust monitoring and logging: Implement comprehensive logging and monitoring systems to detect and alert on suspicious activities, enabling proactive threat detection and response.

    Conduct regular security assessments: Perform periodic vulnerability assessments and penetration testing to identify and address system weaknesses before they can be exploited.

    Establish an incident response plan: Develop a well-defined incident response plan that outlines roles, responsibilities, communication protocols, and remediation procedures to effectively respond to security incidents.

In conclusion, this investigation has provided me with valuable hands-on experience in digital forensics, allowing me to apply theoretical knowledge to real-world scenarios. It highlights the critical role of digital forensics in detecting and responding to security incidents, emphasizing the importance of proactive measures in maintaining a secure digital environment. Thank you for your attention, and I'm happy to answer any questions you may have.
