Project 4 Theory: Host Investigation and Endpoint Context Review

Project 4 focuses on Host Investigation and Endpoint Context Review. This project comes after Project 3 because Project 3 showed that the suspicious hash/file appeared on only one system. After confirming that the file is not spread across many machines, the next logical SOC step is to investigate the affected host deeply.

In Project 1, we learned how to triage detections.
In Project 2, we investigated a high-severity Chrome ML detection.
In Project 3, we used the SHA256 hash to check whether the suspicious file appeared on other systems.
In Project 4, we now focus on the affected endpoint itself.

The main question changes from:

Where else did this file appear?

to:

What do we know about the affected host?

In this case, the hash search result showed:

Affected computers: 1
First written host: LAPTOP-J26AI80A
Last written host: LAPTOP-J26AI80A
Scope: Single-host scope

This means the suspicious file/hash was observed on only one endpoint. Because of that, the analyst should now investigate that endpoint: its hostname, operating system, IP addresses, product type, Real Time Response availability, cloud metadata, injection indicators, and process/service context.

The main concept of this project is:

Host Investigation = Endpoint Context

A detection tells us that something suspicious happened.
Hash Search tells us where the suspicious file appeared.
Host Investigation tells us what kind of system is affected.

This matters because response decisions depend heavily on the host context. A suspicious detection on a normal user workstation is handled differently from a suspicious detection on a production server. A host that is domain joined may have different risk than a standalone system. A host with Real Time Response available gives the analyst more options for live investigation and evidence collection.

The theoretical navigation flow is:

Hash Search Result
→ Identify affected host
→ Open Falcon Investigate
→ Go to Investigate Host
→ Search by hostname or Agent ID
→ Select relevant time range
→ Review Host Info
→ Review IP addresses
→ Review OS and product type
→ Check Real Time Response availability
→ Review cloud metadata
→ Review injection indicators
→ Review Processes and Services
→ Decide next investigation action

In Project 4 screenshots, the affected host is shown as a Windows workstation. The analyst can review local IP addresses, MAC addresses, external/agent IP, operating system version, manufacturer, model, product type, and domain information. This helps the analyst understand what kind of endpoint is involved.

One important part of the screenshot is the Real Time Response option. Real Time Response allows an analyst to connect to the host for deeper investigation. This can help with checking files, collecting evidence, reviewing artifacts, and supporting response decisions. However, an analyst should use it carefully and only when needed.

Another important part is the injection indicator section. The screenshot shows zero values for several injection-related indicators:

Unique DLL Injections: 0
Unique Browser-Injected Threads: 0
Injected Threads From Unsigned Modules: 0
Java Injected Threads: 0

This means CrowdStrike did not observe those specific injection behaviors during the selected time range. This is useful negative evidence. But it does not prove the host is completely clean. It only means those specific suspicious behaviors were not seen in that view and time range.

A SOC analyst should document both positive and negative evidence. Positive evidence means suspicious activity was found. Negative evidence means a suspicious behavior was checked but not observed. In this case, no injection indicators were observed, but the analyst still needs to review process executions, file activity, network activity, and the original Chrome ML detection context.

The analyst should ask:

Which host is affected?
Is it a workstation or server?
What operating system is running?
What IP addresses are linked to it?
Is Real Time Response available?
Is the host domain joined?
Are there multiple MAC addresses?
Is there cloud instance metadata?
Were injection indicators observed?
Are there suspicious process executions?
Does the host context match the original detection?

Based on the screenshots, the analyst interpretation can be:

The affected host is LAPTOP-J26AI80A.
It appears to be a Windows 11 workstation.
The hash search from Project 3 showed single-host scope.
Real Time Response is available.
Multiple local IP addresses and MAC addresses are visible.
Injection-related indicators show zero results in the selected view.
The case still needs investigation through process, file, and network evidence.

The correct current verdict should remain:

Needs Investigation

The host should not be considered clean only because injection indicators are zero. Also, immediate containment may not be required unless stronger evidence appears, such as malicious file execution, credential theft, command-and-control traffic, lateral movement, ransomware behavior, suspicious persistence, or active attacker activity.

The main takeaway is:

Project 3 tells us which host has the suspicious file.
Project 4 helps us understand that host.

So Project 4 teaches an important SOC skill: do not make response decisions based only on the alert. Understand the affected endpoint first.