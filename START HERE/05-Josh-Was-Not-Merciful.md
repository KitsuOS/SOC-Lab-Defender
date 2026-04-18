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
