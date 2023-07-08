 Digital Forensics : Investigating Brute Force and Suspicious Activity  
This is a walkthrough of a digital forensics investigation, where we carefully examine signs of brute force and suspicious activity using a pcap file and an sslkeylogfile text file. In this exercise, we explore into the details of a compromised system, analyzing logs, captured data, and HTTP commands to uncover the truth behind the attack.

    Signs of Brute Force:

To determine if there were any signs of brute force, I analyzed the logs for failed login attempts and identified the following:

    User Account Brute Forced: The account "user" was targeted for the brute force attack.
    Multiple Failed Login Attempts: There were numerous failed login attempts from the IP address 142.55.0.11.

    Success and Suspicious Activity:

Regarding the success of the brute force attack, there were instances of successful logins into the "user" account. However, these sessions were short-lived, automatically closing within a few seconds. The persistence of the brute force attempts around these successful logins raised suspicions.

An intriguing event occurred at 14:04:02, where a successful login took place. This session, marked as session 22, displayed suspicious activity with the creation of a new user named "uesr." The brute force attacks ceased after this event, making session 22 highly suspicious.

    Evidence of New User Creation:

[Please refer to the provided screenshot for evidence of the new user creation.]

The screenshot exhibits the creation of the "uesr" account, which can be easily mistaken for the legitimate "user" account by system administrators.

The relevance of this new user creation to system compromise is that the attacker can now utilize the "uesr" account to gain access to the server, even if the password for the "user" account is changed. This can potentially evade detection since it closely resembles a valid username.

    Suspicious/Malicious HTTP Commands:

To uncover any suspicious or malicious HTTP commands, I examined the captured commands and their potential implications:

[Please refer to the provided screenshots for the list of commands.]

The captured commands indicate that the attacker utilized a PHP web shell to establish a shell session on the target machine and continue their attack. The attacker sent GET requests with shell commands to execute on the server.

The commands included listing files using 'ls,' checking the user with 'whoami,' and attempting to copy the "customer.csv" file to various locations. Eventually, the attacker succeeded in copying the sensitive "customer.csv" file, which contains personal information such as full names, emails, and credit card numbers of customers.

    Prevention Measures:

To mitigate similar attacks, several preventive measures can be implemented:

    Use stronger passwords or implement key-based authentication.
    Consider using nonstandard SSH ports to make it harder for attackers to find the SSH service.
    Implement mechanisms to limit login attempts and install a firewall to block suspicious login attempts.
    Adhere to the principle of least privilege when creating user accounts, granting only necessary privileges.
    Regularly audit file events, including create, modify, and delete actions.
    Monitor HTTP logs for signs of data exfiltration or suspicious activities.

By implementing these preventive measures, the risk of successful brute force attacks and subsequent compromise can be significantly reduced.
