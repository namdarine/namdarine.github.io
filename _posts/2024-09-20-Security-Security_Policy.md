---
layout: post
title: Security Policy 
date: 2024-09-20 18:00:00
description: Concepts and understanding of Information Security
tags: WIL
categories: Info_Security
toc:
  sidebar: left
---

> A set of rules and practices that specify how a system or organization provides security services to protect its assets.  
  
Security policy defines the measures that are in place to <U>ensure the confidentiality, integrity, and availability</U> of data, networks, and system.  
  
# Things covered
- **Who can access what**: explain who is allowed to use certain computers, programs, and information  
- **How to keep data safe**: provide steps for keeping data safe from being stolen or lost  
- **What to do if something goes wrong**: give instructions on how to handle problems like computer hacks, data breaches, or other security issues  
- **Using the internet and emails safely**: provide guidelines for using the internet and emails in a way that doesn't put the organization at risk  
- **Making sure software is up to date**: explain why it's important to regularly update software and how to do it  
- **Training employees**: include instructions for teaching employees about security risks and how to protect the organization  
- **Physical security**: might cover things like locking doors, keeping servers in safe places, and making sure only authorized people can enter certain areas  
  
# Aspects of Security
> The security architecture provides a systematic approach to address the dynamic and evolving nature of security challenges in information systems.  
  
It offers a framework for organizations to build and maintain a secure environment for their <U>data, systems, and networks</U> by focusing on attacks, mechanisms, and services.  
  
## Security Attack
These attacks can take **various forms**, unauthorized access, disclosure, modification, or destruction of data, systems, or networks.  
The goal is to protect against such actions and maintain the confidentiality, integrity, and availability of information (CIA Traids).  
  
## Security Mechanism
Methods designed to detect, prevent, or recover from security attacks. They act as security barriers to safeguard an organization's assets. They operate independently or in conjunction.  
  
### Common security mechanisms
- Cryptography  
- Message digests and digital signatures  
- Digital certificates  
- Public Key Infrastructure (PKI): A framework that manages digital keys and certificates, facilitating secure communication.
&nbsp Different entieties excange information using digital certification  
  
## Security Service
It is functionalities offered by security mechanisms to enhance the security of a system. And it represent the specific functionalities offered by security mechanisms. It can include authentication, access control, data confidentiality, data integrity, and non-repudiation.  
  
### Authentication
> Used to assure the identity of the sender or creator of the data. It is a process of verifying the identity of a user, device, or system, to ensure that it is not and imposter or malicious actor.  
  
=> Assure that the communicating entity is the one that it claims to be  
  
#### Two specific authentication services
- **Peer Entity Authentication**: Used to authenticate the identity of other entities with which the system is communicating  
- **Data Origin Authentication**: Used to authenticate the origin of a message or data, to ensure that it was sent by the entity that it claims to be form  
  
Both of these services are important for ensuring the authenticity and integrity of communication, in order to prevent unauthorized access, tampering, or impersonation. It ensures that the data or communication is from the intended source and not an imposter or an attacker.  
  
**Process**: Identification -> Authentication -> Authorization -> Auditing -> Accountability -> IAAA  
  
### Access Control
> It used to prevent misuse of resources and ensure that only authorized users have access to the available rewources.  
  
=> Prevent unauthorized use of a resource  
  
#### Examples
- **Discretionary Access Control (DAC)**: allows the owner or administrator of a resource to decide who is allowed to access it  
- **Role-based Access Control (RBAC)**: allows access based on the role of the user within the organization. ex) AWS account  
- **Mandatory Access Control (MAC)**: the access is granted based on a set of predefined rules  
- **Attribute-based Access Control (ABAC)**: the access is granted based on the attributes of the requestor, the resource, and the context in which the access request is made  
  
### Data Confidentiality
> Responsible for ensuring that the data is <U>kept extremely safe from third-party intruders.</U>  
  
=> Protect data from unauthorized disclosure  
  
#### Types of data confidentiality
- **Protecting data in transit**: to protect data that is being transmitted between two parties, over a network or through the internet. Can include both passive and active protection measures, encryption.  
- **Protecting data at rest**: to protect data that is <U>stored on a device or system</U>, on a HD or in a DB. Can include access controls, encryption, and backups to prevent unauthorized access or data loss.  
- **Protecting traffic flow from analysis**: to protect the characteristics of the traffic flow, the source and destination, frequency, length and other characteristics of the traffic on a communication facility. Can include measures such as traffic padding and traffic encryption.  
  
* Data Confidentiality services are important for maintaining the privacy and security of sensitive information, and they can take many forms to protect data in transit, at rest and traffic flow from analysis.  
  
### Data Integrity
> Ensure that the transmitted information received by the receiver is **well-authenticated** and there is <U>no tampering with the information received.</U>  
  
=> Assure data received are exactly as sent by authorized entity
  
Helps to ensure that the data received is the same as the data that was sent and that it has not been **modified**, **deleted**, or **tampered** <U>with in any way.</U>  
  
* Data Integrity services are important for <U>maintaning the authenticity and accuracy of transmitted information</U>, and they can take many forms to protect a stream of messages, individual messages, or selected fields within a message.  
  
### Nonrepudiation
Used to prevent either sender or receiver of a transmitted message from denying that the message was sent or received.  
  
=> Protect against denial of one entity involved in communications of having participated in communications
  
- **Message is sent**: the receiver can prove that the alleged sender in fact sent the message  
- **Message is received**: the sender can prove that the alleged receiver in fact received the message  

<div class="row mt-3">
<div class="col-sm mt-3 mt-md-0">
{% include figure.liquid loading="eager" path="assets/img/Security/Security_Services.jpeg" class="img-fluid rounded z-depth-1" %}
</div>
</div>

# Reference
- _CS458-Introduction to Information Security_. (2024). Sajad Meisami, Ph.D. Illinois Institute of Technology.   
