---
layout: post
title: Security Basic - Easiest penetration & Defense of Computer Systems
date: 2024-09-19 18:00:00
description: Concepts and understanding of Information Security
tags: WIL
categories: Info_Security
toc:
  sidebar: left
---

# Principle of Easiest Penetration
* Security principle:  
&nbsp    - A system is only as secure as its weakest link  
&nbsp    - An attacker will often target the easiest poin of encry in a system rather than the most obvious one  
  
Emphasizes the importance of identifying and addressing potential vulnerabilities in a system. As well as testing and regularly reviewing the security controls that are in place.  
  
## DevSecOps processing
1. Initialization Requirement  
2. Design  
&nbsp    - Threat modeling: Secure Design, Archetiecture  
3. Build Implementation  
&nbsp    - Secure code practice  
4. Testing  
&nbsp    - Static Analysis, Dynamic Analysis, Interactive Analysis, SCA  
5. Deployment Release  
6. Maintenance  

Authentication $$\in$$ Threat modeling  
  
# Principle of Adequate Protection
It highlights the need for balancing the cost of security measures with the potential impact of security incidents.  
Also, advises organizations not to overspend on security measures to protect a system that would only cause limited damage if compromise. This principle considers both technical and economic factors in implementing the most effective security measures to protect the assets.  
  
- A proper security risk assessment  
- To weigh the costs and the risks  
- Make sure the right protection measures are in place, balance; Not too much or too little  
  
# Balancing information security and access
This requires a balance between ==protection and availability==, known as the security vs. accessibility trade-off.  
Includes balancing the need to protect sensitive information with the need to allow employees, customers, and other stakeholders access to that information.  
  
* The goal is to find a balance that ensures the ==confidentiality, integrity, and availability of information== while enabling the organization to function effectively.  
  
# Cryptography
> Cyprtography is the practice of protecting data by convering it into an unreadable format (encryption) that can only be accessed by someone who has the proper decryption key.  
  
## Common uses
- Protecting data by making it unreadable  through the use of encryption algorithms  
- Authenticating users with digital signatures  
&nbsp    - use a combination of encryption and hashing to prove the identity of the sender  
- Authenticating transactions with cryptographic protocols, SSL/TLS  
&nbsp    - provide secure communication between web browsers and servers  
- Ensuring the integrity of stored data by using cryptographic techniques  
&nbsp    ex) Message Authentication Codes (MAC)  
- Aid customers' privacy by having their personal information automatically become unreadable after a certain length of time  
  
# Software controls
> Security measure that are used to protect computer systems and networks from unauthorized access and other types of threats.  
  
## Examples
- Passwords and other forms of access control  
&nbsp   ex) biometric authentication  
- Operating systems that include built-in security features  
&nbsp   ex) user accounts and permissions, be used to separate users' actions from each other on a system  
- Virus scanners watch for some kinds of malware  
- Develpment controls enforce quality measures on the original source code  
- Personal firewalls  
  
# Hardware controls
> Security measure that use separate hardware devices to protect computer systems and networks  
  
## Examples
- Biometric readers  
&nbsp   ex) fingerprint readers  
- Smart tokens  
&nbsp   ex) small and portable decices that generate one-time passcodes  
- Firewalls  
- Intrusion detection systems  
  
# Physical controls
> Security measure that are designed to protect the hardware itself and prvent physical access to the console, storage media, and other critical components of a computer system or network.  
  
## Examples
- Locks  
- Security guards  
- Off-site backups: To protect against the possibility of fire, flood, or other types of natural disasters  
- Location-based controls  
&nbsp   ex) Do not put data center on a fault line in California  
  
# Reference
- _CS458-Introduction to Information Security_. (2024). Sajad Meisami, Ph.D. Illinois Institute of Technology.  