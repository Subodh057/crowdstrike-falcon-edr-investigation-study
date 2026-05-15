Yes, your README should include terminology explanations, especially because this project is for learning and portfolio.

That will make your repo much stronger because a recruiter/SOC person can see that you are not just uploading screenshots — you actually understand the EDR concepts.

For Project 2, your README should include a section like this:

## Key Terminology Explained

Inside that section, explain terms used in the screenshots.

⸻

Terms to Explain in Project 2 README

1. EDR

EDR stands for Endpoint Detection and Response.

It helps security teams monitor endpoint activity, detect suspicious behavior, investigate alerts, and respond to threats.

In this project, CrowdStrike Falcon is used as the EDR interface being studied.

⸻

2. Detection

A detection is an alert generated when the EDR identifies suspicious or malicious behavior.

In this case, the detection is related to:

chrome.exe
Machine Learning via Sensor-Based ML
High severity

⸻

3. Triggering File

The triggering file is the file or process that caused the detection.

Example:

chrome.exe

Important point:

chrome.exe is legitimate, but the behavior around it may be suspicious.

⸻

4. Severity

Severity shows how serious the detection may be.

Common severity levels:

Critical
High
Medium
Low
Informational

For this project:

Severity: High

This means the alert should be reviewed with priority.

⸻

5. Sensor-Based ML

Sensor-Based ML means the endpoint sensor used machine learning to detect suspicious file or behavior patterns.

It may detect characteristics such as:

High entropy
Packing
Obfuscation
Anti-malware evasion
Similarity to known malware
Suspicious file structure

Important point:

Machine learning detection does not automatically mean confirmed malware. It still needs analyst validation.

⸻

6. IOA

IOA means Indicator of Attack.

It focuses on suspicious behavior, not just a known bad file.

Example:

A browser writing a suspicious executable
A process launching PowerShell unexpectedly
A tool performing credential dumping behavior

IOA is behavior-focused.

⸻

7. IOC

IOC means Indicator of Compromise.

It usually refers to known suspicious artifacts like:

File hash
IP address
Domain
URL
Filename
Registry key

IOC is artifact-focused.

Simple difference:

IOA = suspicious behavior
IOC = suspicious artifact

⸻

8. Process Tree

A process tree shows parent-child process relationships.

It answers:

Who started whom?

Example:

explorer.exe
   └── chrome.exe
        └── chrome.exe
             └── detection node

This means the user likely opened Chrome, Chrome created child processes, and one Chrome process triggered the detection.

⸻

9. Process Activity

Process activity shows what the process actually did.

It answers:

What actions happened?

Examples:

File created
Executable written
Network connection made
DLL loaded
Child process launched

Simple difference:

Process tree = relationship
Process activity = behavior

⸻

10. Hash

A hash is a unique fingerprint of a file.

Common hash types:

MD5
SHA1
SHA256

SHA256 is commonly used in security investigations because it helps identify the exact file.

⸻

11. Hash Search

Hash Search is used to find where a file appeared in the environment.

It helps answer:

How many hosts saw this file?
Which host saw it first?
Was it written or executed?
Is the incident limited to one machine?

⸻

12. Local Prevalence

Local prevalence means how common the file is inside the organization/environment.

Example:

Local prevalence: Unique

This means the file was seen rarely or only once in that environment.

⸻

13. Global Prevalence

Global prevalence means how common the file is globally across broader telemetry.

Example:

Global prevalence: Common

This means the file is widely seen globally.

Important point:

A file can be globally common but locally rare.

⸻

14. Network Operations

Network operations show network connections made by the process or host.

Important fields:

Local IP
Remote IP
Remote port
Protocol
Connection time

For example:

Remote port: 443

Port 443 usually means HTTPS traffic.

But HTTPS alone is not malicious. The analyst must check the destination and timing.

⸻

15. Network Containment

Network containment isolates the endpoint from the network.

After containment, the host may only communicate with CrowdStrike cloud for management and response.

Containment is used when there is evidence of:

Malware execution
Credential theft
Command and control
Lateral movement
Ransomware behavior

⸻

16. Status

Status shows where the detection is in the investigation lifecycle.

Examples:

New
In Progress
True Positive
False Positive
Ignored
Closed
Reopened

For Project 2, best status:

In Progress

Because the alert needs more investigation before final classification.



