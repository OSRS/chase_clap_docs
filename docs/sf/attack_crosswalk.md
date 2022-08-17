# Crosswalk for Global Analysis to the MITRE Attack Framework

Link to framework: https://attack.mitre.org 

Attack can be looked at in 2 high-level stages: Pre-attack and Attack

The lifecycle can be depicted in a set of stages mapping to the higher level stages as follows:

```
|----Pre-attack----|-------------Attack-------------------------------|
 Recon - Weaponize - Deliver - Exploit - Control - Execute - Maintain
```

The attack phase is the primary area of emphasis for a defender, with the attack section dealing with the following tactics:
| ID | Name | Description
| ----- | ----- | -----
| TA0001 | Initial Access | The adversary is trying to get into your network.
| TA0002 | Execution | The adversary is trying to run malicious code.
| TA0003 | Persistence | The adversary is trying to maintain their foothold.
| TA0004 | Privilege Escalation | The adversary is trying to gain higher-level permissions.
| TA0005 | Defense Evasion | The adversary is trying to avoid being detected.
| TA0006 | Credential Access | The adversary is trying to steal account names and passwords.
| TA0007 | Discovery | The adversary is trying to figure out your environment.
| TA0008 | Lateral Movement | The adversary is trying to move through your environment.
| TA0009 | Collection | The adversary is trying to gather data of interest to their goal.
| TA0011 | Command and Control | The adversary is trying to communicate with compromised systems to control them.
| TA0010 | Exfiltration | The adversary is trying to steal data.
| TA0040 | Impact | The adversary is trying to manipulate, interrupt, or destroy your systems and data. 


Techniques for each Tactic are multiple in number and therefore not fully  listed here. Instead, we will attempt to provide a crosswalk from tactics to anaytics here for techniques we can potential detect.

| Tactic | Technique | Applies To | Analytic Detectable |
| ------ | ------ | ------ | ------
| TA0001 | [Drive-by-compromise](https://attack.mitre.org/techniques/T1189/) | HTTP/S(outbound) | Host/Ip Ratings / rareity / script detection
| TA0001 | [Exploit Public-Facing Application](https://attack.mitre.org/techniques/T1190/) | HTTP/S(inbound) | Behavior anomaly / sql injection detection
| TA0001 | [Phishing](https://attack.mitre.org/techniques/T1566/) | Email / HTTP/S(outbound) | Email inspection (attachments/links) / Host/Ip Ratings / rareity / script detection
| TA0001 | [Supply Chain Compromise](https://attack.mitre.org/techniques/T1195/) | Filesystem / HTTP/S(outbound) | Filesystem signature verification / download verification
| TA0002 | [Shared Modules](https://attack.mitre.org/techniques/T1129/) | Filesystem | Filesystem signature verification 
| TA0002 | [User Execution](https://attack.mitre.org/techniques/T1204/) | System Logs | Executable initiation monitoring / anomaly detection
| TA0003 | [BITS Jobs](https://attack.mitre.org/techniques/T1197/) | HTTP/S(outbound) / SMB Net log | remote address validation / anomaly detection
| TA0003 | [Browser Extensions](https://attack.mitre.org/techniques/T1176/) | HTTP/S(outbound) | Installation traffic(initial download) / blacklisting