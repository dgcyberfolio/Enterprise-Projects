# Splunk Capstone

# SOC Incident Report - FRONTDESK-PC1 Compromise

**Incident Date:** October 15, 2025

---

## Affected Systems

**Host:** FRONTDESK-PC1.KCD.local

**User:** Ryan.Adams

**Host IP:** 172.16.0.184

**IOC External IP:** 157.245.46.190

---

## Indicators of Compromise (IOCs)

**File IOCs:**

* python.exe
* SHA 256: CFFAB896E9F0B12101034D9CED76332EF5AA4036AFA08E940E825E277C21A044

**Scheduled Task IOC:**

* PythonUpdate - Scheduled task configured to execute python.exe on system startup

**Threat Intelligence:**

* 157.245.46.190 reported 107 times (confidence 3%)

---

## Investigation

A brute force attack was initiated against FRONTDESK-PC1.KCD.local beginning at 2025-10-15 12:52:08 UTC. The attacker successfully authenticated as Ryan.Adams at 2025-10-15 12:52:12 UTC. Following successful login, a suspicious Python executable was downloaded via Chrome and written to C:\Users\Ryan.Adams\Music\python.exe. The file was executed between 12:57:00 and 13:00:33 UTC, after which it established an outbound connection to the external IP 157.245.46.190. At 2025-10-15 13:00:34 UTC, python.exe was observed modifying DNS settings on the domain controller. At 2025-10-15 13:04:59 UTC, a scheduled task named PythonUpdate was created via PowerShell to execute python.exe on every system startup, establishing persistence.

Scope checks confirm that python.exe does not exist on any other hosts within the environment and that the external IP 157.245.46.190 was accessed exclusively by Ryan.Adams. No evidence was found to suggest that any other endpoints were affected, indicating this was a targeted, isolated compromise.

---

## 5W1H

**Who:**

Hostname: FRONTDESK-PC1.KCD.local

Host IP: 172.16.0.184

User: Ryan.Adams

IOC External IP: 157.245.46.190 (malicious download source)

**What:**

Brute force login attempts against multiple accounts on FRONTDESK-PC1.KCD.local, followed by a successful login as Ryan.Adams. A suspicious python.exe was downloaded and executed, which modified DNS settings on the domain controller and established an outbound connection to an external IP. A scheduled task named PythonUpdate was created for persistence.

**When:**

First Brute Force Attempt: 2025-10-15 12:52:08 UTC

Successful Login: 2025-10-15 12:52:12 UTC

python.exe Created and Executed: 2025-10-15 12:57:00 to 13:00:33 UTC

DNS Modification: 2025-10-15 13:00:34 UTC

Scheduled Task Created: 2025-10-15 13:04:59 UTC

**Where:**

Hostname: FRONTDESK-PC1.KCD.local

Host IP: 172.16.0.184

File Path: C:\Users\Ryan.Adams\Music\python.exe

External Host: 157.245.46.190

Domain Controller (DNS modification target)

**Why:**

Based on the evidence, the activity reflects likely malicious intent aimed at achieving persistence, maintaining command and control, and enabling potential lateral movement within the environment.

**How:**

Attacker executed a brute force attack, gaining access to Ryan.Adams on FRONTDESK-PC1.KCD.local at 2025-10-15 12:52:12 UTC.

Attacker used Chrome to download python.exe to C:\Users\Ryan.Adams\Music\python.exe.

Attacker executed python.exe, which modified DNS settings on the domain controller and established an outbound connection to 157.245.46.190.

Attacker used PowerShell to create a scheduled task named PythonUpdate, configured to run python.exe with elevated privileges on every system startup.

Scope checks confirmed that no other hosts or users were affected, indicating targeted activity isolated to FRONTDESK-PC1.KCD.local and Ryan.Adams.

---

## Recommendations

**Containment:**

1. Immediately isolate FRONTDESK-PC1.KCD.local from the network to prevent potential lateral movement.
2. Temporarily disable the Ryan.Adams user account pending further investigation.

**Eradication:**

3. Delete python.exe from C:\Users\Ryan.Adams\Music\ and remove the PythonUpdate scheduled task.
4. Conduct a full scan of the workstation for any additional suspicious files or scripts.

**Investigation:**

5. Review DNS changes made on the domain controller to assess the scope of any configuration modifications.
6. Examine PowerShell and Chrome logs for additional indicators of malicious activity.
7. Validate that no other endpoints established connections to 157.245.46.190.

**Prevention:**

8. Enforce multi-factor authentication for all user accounts.
9. Block or monitor access to 157.245.46.190 at the firewall level.
10. Deploy endpoint protection capable of detecting unauthorized script execution and suspicious downloads.
11. Conduct a password audit and initiate a credential reset if compromise is confirmed.

**Monitoring:**

12. Configure alerts for new scheduled task creation, DNS configuration changes, and unusual executable launches.
13. Monitor for any future outbound connections to previously flagged external IP addresses.

---

## Attack Timeline

2025-10-15 12:52:08 UTC - Brute force attack initiated against FRONTDESK-PC1.KCD.local targeting multiple accounts including Ryan.Adams from source IP 172.16.0.184.

2025-10-15 12:52:12 UTC - Successful login achieved on account Ryan.Adams at FRONTDESK-PC1.KCD.local, Logon Type 3.

2025-10-15 12:55:50 UTC - Microsoft Defender Antivirus Real-time Protection scanning for malware and other potentially unwanted software was disabled.

2025-10-15 12:57:00 UTC - python.exe created at C:\Users\Ryan.Adams\Music\python.exe via parent process chrome.exe.

2025-10-15 13:00:33 UTC - python.exe executed via command line: "C:\Users\Ryan.Adams\Music\python.exe", parent process: C:\Windows\Explorer.EXE.

2025-10-15 13:00:34 UTC - python.exe connecting from FRONTDESK-PC1.KCD.local, source IP 172.16.0.110, user Ryan.Adams to 172.16.0.7 over port 135.

2025-10-15 13:00:34 UTC - python.exe connecting from FRONTDESK-PC1.KCD.local, source IP 172.16.0.110, user Ryan.Adams to external IP 157.245.46.190 over port 8888.

2025-10-15 13:00:34 UTC - python.exe queried DNS for ADDC01.KCD.local, receiving answer ::ffff:172.16.0.7, indicating DNS resolution of the domain controller.

2025-10-15 13:00:35 UTC - python.exe connecting from FRONTDESK-PC1.KCD.local, source IP 172.16.0.110, user Ryan.Adams to 172.16.0.7 over port 49669.

2025-10-15 13:04:08 UTC - Command line executed: "PowerShell.exe" -noexit -command Set-Location -literalPath 'C:\Users\Ryan.Adams\Music', parent process: C:\Windows\Explorer.EXE.

2025-10-15 13:04:59 UTC - PowerShell executed schtasks.exe to create scheduled task PythonUpdate: "C:\Windows\system32\schtasks.exe" /create /tn PythonUpdate /tr C:\Users\Ryan.Adams\Music\python.exe /sc onstart /ru SYSTEM /f, parent process: powershell.exe.

2025-10-15 13:04:59 UTC - PythonUpdate scheduled task created, located at C:\Windows\System32\Tasks\PythonUpdate.

2025-10-15 13:05:06 UTC - powershell.exe created C:\Users\Ryan.Adams\AppData\Local\Microsoft\Windows\PowerShell\StartupProfileData-Interactive.

2025-10-15 13:05:53 UTC - Windows Defender status updated to SECURITY_PRODUCT_STATE_SNOOZED.

2025-10-15 13:06:40 UTC - Security Event ID 4634: account Ryan.Adams logged off.

2025-10-15 13:06:41 UTC - Special privileges assigned to new logon, Event ID 4672, user SYSTEM.

2025-10-15 13:06:41 UTC - Event ID 4624: SYSTEM account successfully logged on from host FRONTDESK-PC1.KCD.local.

---

## Scope

python.exe was not found on any other hosts within the environment outside of FRONTDESK-PC1.KCD.local. The external IP 157.245.46.190 was accessed exclusively by Ryan.Adams. No evidence was identified to suggest a broader compromise, indicating this incident was isolated to a single host and user account.

---

## Investigation Findings - Appendix

---

**1 - Brute Force Behavior**

**Query:**

```
index="mydfir-soc" "Ryan.Adams" sourcetype="WinEvent:Security" host="FRONTDESK-PC1" source="security.csv" EventCode=4625
| stats count by _time, user, ComputerName, src_ip, Logon_Type
```

**Evidence:**
Failed logon events (EventCode 4625) recorded against FRONTDESK-PC1.KCD.local from source IP 172.16.0.184, Logon Type 3, consistent with brute force password attack behavior targeting Ryan.Adams.

![1-Brute-Force_Behavior](screenshots/1-Brute-Force_Behavior.png)

---

**2 - Successful Logon**

**Query:**

```
index="mydfir-soc" "Ryan.Adams" sourcetype="WinEvent:Security" host="FRONTDESK-PC1" source="security.csv" EventCode=4624
| stats count by _time, user, ComputerName, src_ip, Logon_Type
```

**Evidence:**
Successful logon events (EventCode 4624) recorded for Ryan.Adams on FRONTDESK-PC1.KCD.local from source IP 172.16.0.184, Logon Type 3, beginning at 2025-10-15 12:52:12 UTC.

![2-Successful-Logon](screenshots/2-Successful-Logon.png)

---

**3 - Malicious Process**

**Query:**

```
index="mydfir-soc" "Ryan.Adams" sourcetype="WinEvent:Sysmon" host=splunk source="sysmon.csv" EventCode=1
| table _time, parent_process, CommandLine, OriginalFileName
| sort -_time
```

**Evidence:**
Sysmon EventCode 1 (Process Create) identified python.exe executed at 2025-10-15 13:00:33 UTC from C:\Users\Ryan.Adams\Music\python.exe with parent process C:\Windows\Explorer.EXE. PowerShell activity also observed, culminating in the creation of the PythonUpdate scheduled task via schtasks.exe at 2025-10-15 13:04:59 UTC.

![3-Malicious_Process](screenshots/3-Malicious_Process.png)

---

**3.1 - File Create**

**Query:**

```
index="mydfir-soc" "Ryan.Adams" sourcetype="WinEvent:Sysmon" host=splunk source="sysmon.csv" EventCode=11 "python.exe"
| table _time, process_name, TargetFilename
```

**Evidence:**
Sysmon EventCode 11 (File Create) confirmed python.exe written to C:\Users\Ryan.Adams\Music\python.exe at 2025-10-15 12:57:00 UTC via parent process chrome.exe.

![3_1-FileCreate](screenshots/3_1-FileCreate.png)

---

**Network Telemetry**

**Query:**

```
index="mydfir-soc" "Ryan.Adams" sourcetype="WinEvent:Sysmon" host=splunk source="sysmon.csv" EventCode=3
| table _time, src_ip, src_port, dest_ip, dest_port, Image
| sort -_time
```

**Evidence:**
Sysmon EventCode 3 (Network Connection) showed python.exe initiating outbound connections from 172.16.0.110 to 157.245.46.190 over port 8888 and to 172.16.0.7 over ports 135 and 49669. Chrome.exe network activity also present during the download window.

![NetworkTelemetry](screenshots/NetworkTelemetry.png)

---

**DNS Telemetry**

**Query:**

```
index="mydfir-soc" "Ryan.Adams" sourcetype="WinEvent:Sysmon" host=splunk source="sysmon.csv" EventCode=22 "python.exe"
| table _time, answer, QueryName, Image
```

**Evidence:**
Sysmon EventCode 22 (DNS Query) recorded python.exe querying for ADDC01.KCD.local at 2025-10-15 13:00:34 UTC, receiving answer ::ffff:172.16.0.7, confirming DNS resolution of the domain controller by the malicious executable.

![DNSTelemetry](screenshots/DNSTelemetry.png)

---

**Scope Check - External IP**

**Query:**

```
index="mydfir-soc" "Ryan.Adams" "157.245.46.190"
| stats count by user
```

**Evidence:**
Search confirmed that the external IP 157.245.46.190 was accessed exclusively by Ryan.Adams, with a count of 1, indicating no other users contacted this address.

![last2](screenshots/last2.png)

---

**Scope Check - python.exe Host Distribution**

**Query:**

```
index="mydfir-soc" "Ryan.Adams" "python.exe"
| stats count by Computer
```

**Evidence:**
Search confirmed that all 12 events associated with Ryan.Adams and python.exe were isolated to FRONTDESK-PC1.KCD.local, with no instances observed on any other host in the environment.

![last](screenshots/last.png)
