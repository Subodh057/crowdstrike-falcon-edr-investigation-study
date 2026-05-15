Project 3 Theory: Hash Search and File Prevalence Investigation

Project 3 focuses on Hash Search and File Prevalence Investigation. This project comes after Project 2 because, in Project 2, we investigated a high-severity Chrome-related ML detection. That detection gave us an important artifact: a SHA256 hash. In SOC/EDR investigation, a hash is very useful because it works like a unique fingerprint of a file. Even if the file name changes, the hash can still help identify the same file.

In Project 2, the main question was: What happened on this one endpoint? We checked the detection details, triggering file, process tree, file information, and network activity. But after finding a suspicious SHA256 hash, the next question becomes: Did this same file appear anywhere else?

That is why we move to Hash Search.

Hash Search helps the analyst check whether the suspicious file is only present on one host or whether it has appeared on multiple hosts. This process is called scoping. Scoping means understanding how big the incident is. If the hash appears on only one endpoint, the incident may be isolated. If the same hash appears on many endpoints, the incident may be widespread and may require escalation.

The navigation flow is simple:

Detection Details
→ Find SHA256 / Associated IOC
→ Copy the hash
→ Go to Investigate
→ Open Hash Search
→ Paste SHA256 hash
→ Submit search
→ Review Hash Written History
→ Check affected computers
→ Check first written host
→ Check last written host
→ Decide incident scope

The main concept of this project is:

Hash Search = File Scoping

It helps answer:

Where else did this file appear?

A SOC analyst uses Hash Search because one detection only tells us that something suspicious happened on one machine. But Hash Search helps us understand whether the suspicious file is limited to that one machine or has touched other systems too.

For example, if the result shows:

# of Computers: 1
First Written On: LAPTOP-J26AI80A
Last Written On: LAPTOP-J26AI80A

then the analyst can say:

The suspicious file currently appears limited to one host. Continue investigating that endpoint.

But if the result shows:

# of Computers: 12
First Written On: HOST-01
Last Written On: HOST-12

then the analyst should think:

The suspicious file has appeared on multiple endpoints. This may be wider exposure and should be escalated.

Important terms in this project include hash, SHA256, IOC, file prevalence, hash written history, first written host, last written host, and affected computers.

A hash is a unique fingerprint of a file. Common hash types include MD5, SHA1, and SHA256. In cybersecurity, SHA256 is commonly used because it gives a strong way to identify a file. An IOC, or Indicator of Compromise, is an artifact that may be connected to suspicious or malicious activity. Examples include file hashes, IP addresses, domains, URLs, file paths, and registry keys.

File prevalence means how common or rare a file is. If a file is rare inside the environment, it deserves more attention. Hash Written History shows where and when a file hash was written to disk. It helps the analyst understand the timeline and affected systems.

The analyst should ask these questions during this project:

What SHA256 hash was found?
What file name is connected to the hash?
How many computers saw this hash?
Which host saw it first?
Which host saw it last?
When was it first written?
When was it last written?
Is the file still appearing?
Is this limited to one endpoint?
Does the investigation need to expand?

The final analyst logic is:

If the hash appears on one host:
The incident may be isolated. Continue investigating that host.
If the hash appears on many hosts:
The incident may be widespread. Identify all affected hosts and escalate.
If the hash appears repeatedly over time:
The file may be persistent, repeatedly downloaded, or distributed by some process.

The SOC value of this project is that it teaches how an analyst moves from a single detection to environment-wide investigation. Detection tells us something suspicious happened. Hash Search tells us where else the suspicious file appeared.

The final takeaway is:

Project 2 = Investigate one suspicious detection.
Project 3 = Use the file hash to check the scope across endpoints.

So, Project 3 teaches an important SOC skill: do not stop after finding one suspicious file. Search the hash and confirm whether the issue is isolated or widespread.
