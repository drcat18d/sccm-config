<p align="center">
    <a href="https://github.com/subat0mik/Misconfiguration-Manager">
    <img src="https://img.shields.io/endpoint?url=https%3A%2F%2Fraw.githubusercontent.com%2Fspecterops%2F.github%2Fmain%2Fconfig%2Fshield.json&style=flat"
        alt="Sponsored by SpecterOps"/></a>
    <a href="https://join.slack.com/t/bloodhoundhq/shared_invite/zt-1tgq6ojd2-ixpx5nz9Wjtbhc3i8AVAWw">
        <img src="https://img.shields.io/badge/Slack-%23sccm-blueviolet?logo=slack" alt="Slack"/></a>
    <a href="https://twitter.com/subat0mik">
        <img src="https://img.shields.io/twitter/follow/subat0mik?style=social"
        alt="@subat0mik on Twitter"/></a>
    <a href="https://twitter.com/_Mayyhem">
        <img src="https://img.shields.io/twitter/follow/_Mayyhem?style=social"
        alt="@_Mayyhem on Twitter"/></a>
    <a href="https://twitter.com/garrfoster">
        <img src="https://img.shields.io/twitter/follow/garrfoster?style=social"
        alt="@garrfoster on Twitter"/></a>
</p>

---

# Misconfiguration Manager

![MM-cropped](https://github.com/subat0mik/Misconfiguration-Manager/assets/41414134/0c88e861-4b13-4722-a8b1-7db53f782ee8)

This repository serves as a central knowledge base for all known Microsoft Configuration Manager (a.k.a. MCM, ConfigMgr, System Center Configuration Manager, or SCCM) tradecraft and associated defensive and hardening guidance. Our goal is to help demystify SCCM tradecraft and simplify SCCM attack path management for defenders while also educating offensive security professionals on this nebulous attack surface. Designed to go beyond the static nature of whitepapers, this living repository documents known SCCM misconfigurations and their abuses and encourages ongoing contributions from the community to enhance its relevance and utility.

We've curated this repository to raise awareness of the rapidly evolving SCCM threat landscape, drawing inspiration from the [MITRE ATT&CK framework](https://attack.mitre.org/matrices/enterprise/), with a few deviations. We were also strongly influenced by Push Security's [SaaS attack techniques matrix](https://github.com/pushsecurity/saas-attacks/tree/main) as well as Will Schroeder and Lee Chagolla-Christensen's [Certified Pre-Owned](https://specterops.io/wp-content/uploads/sites/3/2022/06/Certified_Pre-Owned.pdf) whitepaper.

Our approach extends beyond cataloging the tactics of known adversaries to include contributions from the realm of penetration testing, red team operations, and security research. At SpecterOps, we've leveraged many misconfigurations highlighted in this repository in real-world environments, while others represent experimental and exploratory research projects proved out in a lab environment.

This project also serves as a central point of reference for all of the [SCCM attack and defense resources](./RESOURCES.md) that we're aware of.

We openly invite you to submit both proven and exploratory SCCM-focused attack techniques and defensive strategies and resources to this project and to provide any feedback and recommendations about the content in this repository.

<hr>
<br>

# How to use this project

Start with the SCCM Attack Matrix and SCCM Attack and Defense Matrix below, which map attack techniques to their MITRE ATT&CK framework tactics, as well as to their detection and prevention strategies.

Offensive security practitioners may also benefit from reviewing the list of known and documented [Attack Techniques](./attack-techniques/_attack-techniques-list.md), which identifies the security context and network access that are required for each technique.

Defenders and IT administrators may benefit from reviewing the list of known and documented [Defense Techniques](./defense-techniques/_defense-techniques-list.md), which identifies the administrator roles we think are most likely to be involved in the implementation of each item.

Curious about how a hierarchy can be completely compromised in certain, mostly default conditions? Check out the list of [TAKEOVER techniques](https://github.com/subat0mik/Misconfiguration-Manager/blob/main/attack-techniques/TAKEOVER/_takeover-techniques-list.md).

If you aren't familiar with a term used in a technique's description, refer to the [glossary page](./GLOSSARY.md), which contains definitions for terms commonly used in SCCM.

If you'd like to test these techniques in a lab environment or learn more about SCCM attack and defense, please refer to the [resources page](./RESOURCES.md), which contains links to all the SCCM lab and attack/defense resources that we are aware of, many of which inspired and informed the information in this repository.

If we've overlooked anything or are missing credits for prior work, please reach out to us or submit a pull request and we'd be happy to make updates.

<hr>
<br>

# SCCM Attack Matrix

|                              Initial Access                              |                                 Execution                                  |                                     Persistence                                     |                                       Privilege Escalation                                       |                              Defense Evasion                               |                                     Credential Access                                     |                                      Discovery                                       |                                         Lateral Movement                                         |                             Collection                              | Command and Control |                            Exfiltration                             |
| :----------------------------------------------------------------------: | :------------------------------------------------------------------------: | :---------------------------------------------------------------------------------: | :----------------------------------------------------------------------------------------------: | :------------------------------------------------------------------------: | :---------------------------------------------------------------------------------------: | :----------------------------------------------------------------------------------: | :----------------------------------------------------------------------------------------------: | :-----------------------------------------------------------------: | :-----------------: | :-----------------------------------------------------------------: |
| [PXE Credentials](./attack-techniques/CRED/CRED-1/cred-1_description.md) |  [App Deployment](./attack-techniques/EXEC/EXEC-1/exec-1_description.md)   |       [App Deployment](./attack-techniques/EXEC/EXEC-1/exec-1_description.md)       |   [Relay to Site System (SMB)](./attack-techniques/ELEVATE/ELEVATE-1/ELEVATE-1_description.md)   |  [App Deployment](./attack-techniques/EXEC/EXEC-1/exec-1_description.md)   |         [PXE Credentials](./attack-techniques/CRED/CRED-1/cred-1_description.md)          |     [LDAP Enumeration](./attack-techniques/RECON/RECON-1/recon-1_description.md)     |  [Relay to Site DB (MSSQL)](./attack-techniques/TAKEOVER/TAKEOVER-1/takeover-1_description.md)   | [CMPivot](./attack-techniques/RECON/RECON-4/recon-4_description.md) |                     | [CMPivot](./attack-techniques/RECON/RECON-4/recon-4_description.md) |
|                                                                          | [Script Deployment](./attack-techniques/EXEC/EXEC-2/exec-2_description.md) |     [Script Deployment](./attack-techniques/EXEC/EXEC-2/exec-2_description.md)      | [Relay Client Push Installation](./attack-techniques/ELEVATE/ELEVATE-2/ELEVATE-2_description.md) | [Script Deployment](./attack-techniques/EXEC/EXEC-2/exec-2_description.md) |    [Policy Request Credentials](./attack-techniques/CRED/CRED-2/cred-2_description.md)    |     [SMB Enumeration](./attack-techniques/RECON/RECON-2/recon-2_description.md)      |   [Relay to Site DB (SMB)](./attack-techniques/TAKEOVER/TAKEOVER-2/takeover-2_description.md)    |                                                                     |                     |                                                                     |
|                                                                          |                                                                            | [Relay to AD CS](./attack-techniques/TAKEOVER/TAKEOVER-3/takeover-3_description.md) |  [Relay to Site DB (MSSQL)](./attack-techniques/TAKEOVER/TAKEOVER-1/takeover-1_description.md)   |                                                                            |        [DPAPI Credentials](./attack-techniques/CRED/CRED-3/cred-3_description.md)         |     [HTTP Enumeration](./attack-techniques/RECON/RECON-3/recon-3_description.md)     |      [Relay Between HA](./attack-techniques/TAKEOVER/TAKEOVER-7/takeover-7_description.md)       |                                                                     |                     |                                                                     |
|                                                                          |                                                                            | [Relay to LDAP](./attack-techniques/TAKEOVER/TAKEOVER-8/takeover-8_description.md)  |        [Relay to LDAP](./attack-techniques/TAKEOVER/TAKEOVER-8/takeover-8_description.md)        |                                                                            |        [Legacy Credentials](./attack-techniques/CRED/CRED-4/cred-4_description.md)        |         [CMPivot](./attack-techniques/RECON/RECON-4/recon-4_description.md)          |             [App Deployment](./attack-techniques/EXEC/EXEC-1/exec-1_description.md)              |                                                                     |                     |                                                                     |
|                                                                          |                                                                            |                                                                                     |   [Relay to Site DB (SMB)](./attack-techniques/TAKEOVER/TAKEOVER-2/takeover-2_description.md)    |                                                                            |    [Site Database Credentials](./attack-techniques/CRED/CRED-5/cred-5_description.md)     | [SMS Provider Enumeration](./attack-techniques/RECON/RECON-5/recon-5_description.md) |            [Script Deployment](./attack-techniques/EXEC/EXEC-2/exec-2_description.md)            |                                                                     |                     |                                                                     |
|                                                                          |                                                                            |                                                                                     |        [Relay to ADCS](./attack-techniques/TAKEOVER/TAKEOVER-3/takeover-3_description.md)        |                                                                            | [Client Push Installation Account](./attack-techniques/CRED/CRED-6/cred-6_description.md) |                                                                                      |   [Relay to Site System (SMB)](./attack-techniques/ELEVATE/ELEVATE-1/ELEVATE-1_description.md)   |                                                                     |                     |                                                                     |
|                                                                          |                                                                            |                                                                                     |     [Relay CAS to Child](./attack-techniques/TAKEOVER/TAKEOVER-4/takeover-4_description.md)      |                                                                            | [Distribution Point Looting](./attack-techniques/CRED/CRED-6/cred-6_description.md)       |                                                                                      | [Relay Client Push Installation](./attack-techniques/ELEVATE/ELEVATE-2/ELEVATE-2_description.md) |                                                                     |                     |                                                                     |
|                                                                          |                                                                            |                                                                                     |    [Relay to AdminService](./attack-techniques/TAKEOVER/TAKEOVER-5/takeover-5_description.md)    |                                                                            |                                                                                           |                                                                                      |     [Relay CAS to Child](./attack-techniques/TAKEOVER/TAKEOVER-4/takeover-4_description.md)      |                                                                     |                     |                                                                     |
|                                                                          |                                                                            |                                                                                     | [Relay to SMS Provider (SMB)](./attack-techniques/TAKEOVER/TAKEOVER-6/takeover-6_description.md) |                                                                            |                                                                                           |                                                                                      | [Relay to SMS Provider (SMB)](./attack-techniques/TAKEOVER/TAKEOVER-6/takeover-6_description.md) |                                                                     |                     |                                                                     |
|                                                                          |                                                                            |                                                                                     |      [Relay Between HA](./attack-techniques/TAKEOVER/TAKEOVER-7/takeover-7_description.md)       |                                                                            |                                                                                           |                                                                                      |      [SQL Linked as DBA](./attack-techniques/TAKEOVER/TAKEOVER-9/takeover-9_description.md)      |                                                                     |                     |                                                                     |
|                                                                          |                                                                            |                                                                                     |      [SQL Linked as DBA](./attack-techniques/TAKEOVER/TAKEOVER-9/takeover-9_description.md)      |                                                                            |                                                                                           |                                                                                      |                                                                                                  |                                                                     |                     |                                                                     |
|                                                                          |                                                                            |                                                                                     |   [Relay to Site DB (SMB)](./attack-techniques/TAKEOVER/TAKEOVER-2/takeover-2_description.md)    |                                                                            |                                                                                           |                                                                                      |                                                                                                  |                                                                     |                     |                                                                     |

<br>

# SCCM Attack and Defense Matrix

|                       | CRED&#x2011;1 | CRED&#x2011;2 | CRED&#x2011;3 | CRED&#x2011;4 | CRED&#x2011;5 | CRED&#x2011;6 | ELEVATE&#x2011;1 | ELEVATE&#x2011;2 | ELEVATE&#x2011;3 | EXEC&#x2011;1 | EXEC&#x2011;2 | RECON&#x2011;1 | RECON&#x2011;2 | RECON&#x2011;3 | RECON&#x2011;4 | RECON&#x2011;5 | TAKEOVER&#x2011;1 | TAKEOVER&#x2011;2 | TAKEOVER&#x2011;3 | TAKEOVER&#x2011;4 | TAKEOVER&#x2011;5 | TAKEOVER&#x2011;6 | TAKEOVER&#x2011;7 | TAKEOVER&#x2011;8 | TAKEOVER&#x2011;9 |
| :-------------------- | :-----------: | :-----------: | :-----------: | :-----------: | :-----------: | :-----------: | :--------------: | :--------------: | :--------------: | :-----------: | :-----------: | :------------: | :------------: | :------------: | :------------: | :------------: | :---------------: | :---------------: | :---------------: | :---------------: | :---------------: | :---------------: | :---------------: | :---------------: | :---------------: |
| **CANARY&#x2011;1**   |       X       |       X       |       X       |       X       |       X       |       X       |                  |                  |                  |               |               |                |                |                |                |                |                   |                   |                   |                   |                   |                   |                   |                   |                   |
| **DETECT&#x2011;1**   |               |               |               |               |               |               |        X         |        X         |        X         |       X       |               |                |                |                |                |                |         X         |         X         |         X         |         X         |         X         |         X         |         X         |         X         |                   |
| **DETECT&#x2011;2**   |               |               |               |               |               |               |                  |                  |                  |               |               |       X        |                |                |                |                |                   |                   |                   |                   |                   |                   |                   |                   |                   |
| **DETECT&#x2011;3**   |               |               |               |               |               |               |                  |        X         |        X         |       X       |               |                |                |                |                |                |                   |                   |                   |                   |                   |                   |                   |                   |                   |
| **DETECT&#x2011;4**   |               |               |               |               |               |               |                  |                  |                  |       X       |               |                |                |                |                |                |                   |                   |                   |                   |                   |                   |                   |                   |                   |
| **DETECT&#x2011;5**   |               |               |               |               |               |               |                  |                  |                  |               |               |                |                |                |       X        |       X        |         X         |         X         |                   |                   |                   |                   |                   |                   |                   |
| **PREVENT&#x2011;1**  |               |               |               |               |               |               |                  |        X         |        X         |       X       |               |                |                |                |                |                |                   |                   |                   |                   |                   |                   |                   |                   |                   |
| **PREVENT&#x2011;2**  |               |               |               |               |               |               |                  |        X         |        X         |       X       |               |                |                |                |                |                |                   |                   |                   |                   |                   |                   |                   |                   |                   |
| **PREVENT&#x2011;3**  |       X       |       X       |       X       |       X       |               |       X       |                  |                  |                  |               |               |                |                |                |                |                |                   |                   |                   |                   |                   |                   |                   |                   |                   |
| **PREVENT&#x2011;4**  |               |       X       |       X       |       X       |               |       X       |                  |                  |                  |               |               |                |                |                |                |                |                   |                   |                   |                   |                   |                   |                   |                   |                   |
| **PREVENT&#x2011;5**  |               |               |               |               |               |               |                  |        X         |        X         |       X       |               |                |                |                |                |                |                   |                   |                   |                   |                   |                   |                   |                   |                   |
| **PREVENT&#x2011;6**  |       X       |               |               |               |               |               |                  |                  |                  |               |               |                |                |                |                |                |                   |                   |                   |                   |                   |                   |                   |                   |                   |
| **PREVENT&#x2011;7**  |       X       |               |               |               |               |               |                  |                  |                  |               |               |                |                |                |                |                |                   |                   |                   |                   |                   |                   |                   |                   |                   |
| **PREVENT&#x2011;8**  |               |       X       |               |               |               |       X       |                  |        X         |                  |               |               |                |                |                |                |                |                   |                   |                   |                   |                   |         X         |                   |                   |                   |
| **PREVENT&#x2011;9**  |               |               |               |               |               |               |                  |                  |                  |       X       |       X       |                |                |                |                |       X        |         X         |                   |                   |                   |                   |         X         |                   |                   |                   |
| **PREVENT&#x2011;10** |               |       X       |       X       |       X       |       X       |       X       |                  |                  |                  |               |               |                |                |                |                |                |                   |                   |                   |                   |                   |                   |                   |                   |                   |
| **PREVENT&#x2011;11** |               |               |               |               |               |               |                  |        X         |                  |               |               |                |                |                |                |                |                   |                   |         X         |                   |                   |                   |                   |         X         |                   |
| **PREVENT&#x2011;12** |               |               |               |               |               |               |        X         |        X         |        X         |       X       |               |                |                |                |                |                |                   |         X         |                   |         X         |                   |         X         |         X         |                   |                   |
| **PREVENT&#x2011;13** |               |               |               |               |               |               |                  |                  |                  |               |               |                |                |                |                |                |                   |                   |                   |                   |                   |                   |                   |         X         |                   |
| **PREVENT&#x2011;14** |               |               |               |               |               |               |                  |                  |                  |               |               |                |                |                |                |                |         X         |                   |         X         |                   |         X         |                   |                   |                   |                   |
| **PREVENT&#x2011;15** |               |               |               |       X       |               |               |                  |                  |                  |               |               |                |                |                |                |                |                   |                   |                   |                   |                   |                   |                   |                   |                   |
| **PREVENT&#x2011;16** |               |       X       |               |               |               |               |                  |                  |                  |               |               |                |                |                |                |                |                   |                   |                   |                   |                   |                   |                   |                   |                   |
| **PREVENT&#x2011;17** |       X       |       X       |       X       |       X       |       X       |       X       |                  |                  |                  |               |               |                |                |                |                |                |                   |                   |                   |                   |                   |                   |                   |                   |                   |
| **PREVENT&#x2011;18** |               |               |               |               |       X       |               |                  |                  |                  |               |               |                |                |                |                |                |                   |                   |                   |                   |                   |                   |                   |                   |                   |
| **PREVENT&#x2011;19** |               |               |               |               |       X       |               |                  |                  |                  |               |               |                |                |                |                |                |                   |                   |                   |                   |                   |                   |                   |                   |         X         |
| **PREVENT&#x2011;20** |               |               |               |               |       X       |               |        X         |                  |                  |       X       |       X       |                |       X        |       X        |       X        |       X        |         X         |         X         |         X         |         X         |         X         |         X         |         X         |         X         |                   |
| **PREVENT&#x2011;21** |       X       |               |               |               |               |               |                  |                  |                  |               |               |                |                |                |                |                |                   |                   |                   |                   |                   |                   |                   |                   |                   |
| **PREVENT&#x2011;22** |               |               |               |               |               |       X       |                  |                  |                  |               |               |                |                |                |                |                |                   |                   |                   |                   |                   |                   |                   |                   |                   |

---

<br>
<br>

# Taxonomy Overview

> At the time of release, TAKEOVER-1 through TAKEOVER-9, in our opinion, are ordered in descending order of likelihood based on system defaults and our experiences testing SCCM hierarchies. Further additions will follow sequential order by release date.

> With the exception of TAKEOVER, these techniques are numbered in no particular order. A higher or lower number does not represent our opinion of the item's importance, likelihood, or how it should be prioritized.

## Attack Techniques

### CRED

Techniques coded with a CRED moniker primarily abuse credential access. CRED techniques are the most common we've seen and often lead to direct hierarchy takeover or domain compromise.

### ELEVATE

Techniques coded with an ELEVATE moniker can be used for either local or domain privilege escalation. In some cases, these can be chained with other techniques for a hierarchy takeover primitive.

### EXEC

Techniques coded with an EXEC moniker can be used to execute commands, scripts, code, etc. on a remote target through SCCM's builtin functionality.

### RECON

Techniques coded with a RECON moniker relate to either performing reconnaissance against SCCM infrastructure or using SCCM to conduct further reconnaissance.

### TAKEOVER

Techniques coded with a TAKEOVER moniker describe the various steps necessary to compromise an SCCM hierarchy.

<hr>
<br>

## Defense Techniques

### CANARY

Defensive strategies coded with a CANARY moniker describe deception strategies that could be used to deceive adversaries in tripping a high-fidelity detection.

### DETECT

Defensive strategies coded with a DETECT moniker describe strategies for detecting offensive techniques. In some cases, multiple DETECT strategies may be required for a stronger detection.

### PREVENT

Defensive strategies coded with a PREVENT moniker describe configuration changes to mitigate one or more aspects of an offensive technique. In some cases, multiple PREVENT strategies may be needed to fully mitigate an offensive technique.

**NOTE:** We strongly recommend proper and thorough testing of any changes before configuring them in a production environment. The authors and contributors of this repository are not responsible for any breaking changes. Use as a guide at your own risk.

<hr>
<br>

# Contributors

[Duane Michael](https://twitter.com/subat0mik), [Chris Thompson](https://twitter.com/_Mayyhem), and [Garrett Foster](https://twitter.com/garrfoster) are the primary authors of this project, with contributions from:

- [Diego Lomellini](https://twitter.com/DiLomSec1)
- [Josh Prager](https://twitter.com/Praga_Prag)
- [Marshall Price](https://twitter.com/__Mastadon)
- [Alberto Rodriguez](https://x.com/__ar0d__)

Please reach out to us on Twitter or join us in the `#sccm` channel on the [BloodHoundGang Slack](https://bloodhoundgang.herokuapp.com/) if you have any questions or are interested in contributing!
