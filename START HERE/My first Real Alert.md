It was time to take on my first real alert.

I began by reviewing the incidents page within Microsoft Defender, taking a moment to understand the scope of what was in front of me. The environment had been populated with multiple alerts—three categorized as medium severity and three as high severity—each representing a different scenario to investigate.

To approach this strategically, I chose to start with the medium severity alerts. My goal was to build confidence and reinforce my investigative process on scenarios that were likely less complex before moving on to higher-severity incidents that would require deeper analysis and more critical decision-making.

This decision allowed me to ease into the workflow while still treating each alert with the level of attention it deserved. From there, I selected my first case: a mass file download from SharePoint, which would serve as the starting point for my initial independent investigation within this lab.

![Given Alerts Created by Josh](../images/Given%20alerts%20created%20by%20josh.png)


I opened the alert and began my investigation.

From the initial incident view, I immediately noticed that Microsoft Defender had already mapped the activity to a MITRE ATT&CK technique: T1530. While this was helpful context, I made a point to validate and include this mapping independently in my final report after completing the investigation.

As I reviewed the alert details, I identified the trigger condition: 20 or more files downloaded from SharePoint by a single user within a 15-minute window. This type of activity can indicate potential data exfiltration, so it warranted a deeper look.

![Running KQL](../images/Running%20KQL%20to%20find%20more%20information.png)


From there, I moved into Advanced Hunting and began using KQL to expand the investigation. I focused on both the source IP address and the user account david.kumar, drilling into the available logs to better understand the scope and nature of the activity. By navigating through the query results, I was able to review the specific files being accessed and downloaded.

What stood out immediately was the type of content involved. The files being downloaded included onboarding materials, policy documents, and internal reports—content that would typically be accessed by someone in an onboarding or HR-related role. While I did ask Josh whether the user was associated with such a department, that level of user context was not available within the lab environment, and I was expected to make a determination based on the data in front of me.

Given the consistency of the activity, the nature of the files, and the lack of any additional indicators of compromise—such as unusual login behavior, suspicious IP reputation, or anomalous access patterns—I assessed that the activity aligned with legitimate business operations.

Based on this analysis, I determined the alert to be benign, likely representing normal onboarding or internal documentation access rather than malicious data exfiltration.

Below is the incident report I created, which represents my first fully documented investigation completed with guidance from a SOC analyst.

[View First Incident Report](../incidents/first%20incident%20report.txt)
