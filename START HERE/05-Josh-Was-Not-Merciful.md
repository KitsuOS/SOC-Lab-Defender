As the title suggests, the next incident I chose to investigate was a significant step up in complexity—and Josh made sure of it.

While reviewing the incidents dashboard in Microsoft Defender, I began to notice a pattern that stood out. Several of the alerts were tied to a single user: john.smith. The repetition immediately caught my attention, as multiple alerts associated with one account often indicate a broader issue rather than isolated activity.

Initially, I planned to continue working through a medium-severity incident involving another user, emily.jones, to further build confidence. However, after discussing my approach with Josh—and having expressed that I was eager to challenge myself—I was encouraged to shift focus to the high-severity incidents instead.

Taking that advice, I pivoted my attention to the alerts involving John Smith. Given the number of incidents associated with this account and their elevated severity, it was clear that this investigation would require a more thorough and deliberate approach.

At this point, I knew I was stepping into something more complex—and I was ready to see where it led.

![Brute Force Incident](../images/Brute%20Force%20Incident.png)


The first detail that immediately stood out during my investigation was the geolocation of the source IP address, which was identified as originating from Russia within the alert details. While geolocation alone is not enough to determine malicious intent, it served as a strong indicator that warranted further investigation.

To validate this, I pivoted to external intelligence sources and began conducting OSINT analysis on the IP address. Using IP Abuse DB, I queried the address and found that it had been reported over one thousand times for malicious activity. This significantly increased the confidence that the activity was not benign.

Further analysis revealed that the IP was being routed through a Tor exit node, indicating an attempt to anonymize the origin of the traffic. This is a common tactic used by threat actors to obscure their identity and evade detection.

At this point, the combination of geolocation, reputation data, and anonymization techniques strongly suggested that the activity was malicious in nature, and the investigation began to shift from validation to confirmation and impact assessment.


From there, I kept the alert details open and pivoted into Advanced Hunting to begin a deeper investigation using KQL.


In the initial alert view, I had already identified that the environment was experiencing a brute force attack, with over 18 failed login attempts within a short time frame. This alone was concerning, but I wanted to determine whether the activity had progressed beyond failed access attempts.

As I continued reviewing related incidents on the main dashboard, I noticed something important—there was also an email-related alert tied to the same user account, john.smith. This suggested that the activity might not be isolated and could indicate a broader compromise.

Using KQL, I began correlating events tied to both the user and the associated IP address. As I worked through the data—filtering results and drilling into specific activities—I uncovered behavior that confirmed my suspicion.

![Email Forwarding](../images/Email%20Forwarding.png)
The attacker had successfully established email forwarding rules on the compromised account. Emails received by John Smith were being automatically forwarded to an external address, while the original messages were being deleted from the inbox.

This technique is commonly used by threat actors to quietly monitor communications and extract sensitive information without alerting the user. At this point, the investigation had clearly moved beyond attempted access and into active account compromise and data exfiltration.
At this stage of the investigation, one detail stood out—I was unable to locate clear log evidence of a successful login event tied to the attacker. Given the observed post-compromise behavior, particularly the unauthorized email forwarding rules, this created an inconsistency that required further consideration.

Initially, this raised questions about how access had been established without a clearly identifiable authentication event. Rather than drawing unsupported conclusions, I treated this as a limitation in available telemetry or logging visibility. It is possible that certain authentication events were not captured within the scope of the lab environment, or that the activity fell outside the data sources being monitored.

While alternative access methods such as session hijacking or token-based authentication can sometimes result in limited traditional login logs, I did not have sufficient evidence within the available data to confirm a specific technique. Instead, I focused on the confirmed indicators—post-compromise account activity and unauthorized configuration changes—which were sufficient to support a determination of account compromise.

This moment reinforced an important lesson: investigations do not always provide complete visibility, and it is critical to base conclusions on verified evidence while acknowledging gaps in telemetry.
