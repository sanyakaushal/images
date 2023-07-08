As part of my cybersecurity studies, I recently undertook a challenging digital forensics assignment focused on advanced information systems forensics and electronic discovery. The assignment involved investigating a compromised workstation and implementing necessary measures to restore its security. Here are the key findings and actions taken during the investigation:

    Detecting Compromise: Unusual Login Activity

Upon analyzing the compromised workstation, we observed abnormal login activity. Every time a user logged in, a Command Prompt window automatically opened, displaying a list of images being uploaded to an undisclosed location. This unusual behavior raised suspicion and indicated a compromise.

    Attacker's Objective: File Exfiltration

Further analysis revealed that the attacker's goal was to exfiltrate files from the workstation, specifically images from the "C:/Systemcore/library" directory. We discovered an "upload.ps1" script in the "C:\Systemcore" folder, responsible for facilitating the exfiltration process. The script was designed to upload files from the source directory ("C:\Systemcore\library") to a remote FTP server at "ftp://dlpuser:rNrKYTX9g7z3RgJRmxWuGHbeu@ftp.dlptest.com."

Additional suspicious files and applications were found in the same folder, indicating a coordinated effort by the attacker. These files included "load.cmd," "test.bat," "Untitled4.ps1," "Upload.ps1," "PS1 to Service.exe," and "Untitled2.ps1," suggesting a complex attack strategy.

    Persistence Mechanisms: Maintaining Unauthorized Access

To ensure continued access to the compromised workstation, the attacker employed a persistence mechanism. We discovered the presence of "Untitled4.ps1," a script scheduled to execute "Untitled2.ps1" daily at 3 am. Additionally, "Untitled2.ps1" was triggered during the user's login, establishing persistent unauthorized access.

    Restoration and Mitigation Measures

To restore the compromised system to a secure state, the following mitigation measures were recommended:

    Removal of suspicious scheduled tasks: The "Untitled4.ps1" script and associated tasks needed to be eliminated to prevent further unauthorized execution.
    Deletion of PowerShell scripts: All PowerShell scripts, including "Upload.ps1," were advised to be removed to disable the exfiltration mechanism.
    Network-wide investigation: It was essential to extend the investigation to other systems within the network. This involved searching for similar files, scheduled tasks, or indicators of compromise. Network monitoring tools, such as Intrusion Detection Systems (IDS) or packet sniffers, could aid in identifying potential compromises and blocking malicious traffic.

    Network-Wide Compromise Assessment

To determine if other systems in the network were compromised using the same malware, the following steps were suggested:

    Searching for common files and scheduled tasks: A systematic search for files and scheduled tasks resembling those found on the compromised workstation should be conducted.
    Network traffic analysis: The use of IDS or packet sniffers can help identify any packets originating from or destined for the identified FTP server. Monitoring and blocking such traffic would assist in detecting potential compromises across the network.

By diligently following these investigation procedures and implementing the recommended mitigation measures, we aimed to restore the compromised workstation's security and safeguard the broader network against potential threats.

This assignment provided valuable hands-on experience in digital forensics, allowing me to apply theoretical knowledge to real-world scenarios. It emphasized the critical role of digital forensics in detecting and responding to security incidents, reinforcing the significance of proactive measures in ensuring a secure digital environment
