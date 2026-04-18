Alert Title: Compromised Account and Information Exfiltration



Entities: 

User: John.Smith,

**IP Address: 185.220.101\[.]45,**



Attack Summary:

On 04/17/26 at ~~approximately~~ 6:20 PM, an alert was triggered indicating a potential brute force attack based on a rule detecting five or more unsuccessful login attempts within a short time frame. 

Upon investigation, OSINT analysis revealed that the source IP address **(185.220.101\[.]45)** originated from Russia and had been reported over 1,000 times on AbuseIPDB. <- **Missing reason**



Further analysis indicated that the IP was routing traffic through a Tor network, suggesting an attempt to mask malicious activity.

A deeper investigation identified that the attacker configured unauthorized email forwarding rules on the compromised account (john.smith) and deleted originating emails to evade detection. <- **What time?, Rule information?** 

After 18 unsuccessful login attempts, the attacker successfully gained unauthorized access to the account and began exfiltrating information. <- What time? 

This activity aligns with MITRE ATT\&CK technique T1110 (Brute Force).



**Did anything else happen following the rule creation? Was there any sign of further persistence establishment? I.e., attempted password reset, any signs of any new devices being enrolled etc.? How was the account compromised, what did the logon events show? Browser information, device information etc.**



Remediation Actions:

Password reset initiated for the compromised account

Revocation of all active sessions associated with the account



Recommended Actions:

Enforce Multi-Factor Authentication (MFA) to prevent reliance on single-factor authentication

Temporarily disable the affected account until security validation is complete

Require implementation of a stronger, more complex password policy

