---
layout: post
title: Security - Attacks
date: 2024-09-22 18:00:00
description: Concepts and understanding of Information Security
tags: WIL
categories: Info_Security
toc:
  sidebar: left
---

There are two different types of attacks, passive attack and active attack.  
  
# Passive Attack
> Attempt to learn or make use of information, but not affect system resources.  
  
Such as, release message contents and traffic analysis.  
It is relatively hard to detect, but easier to prevent by encryption.  
  
## Realease Message Contents
Message content is one of the passive attack. It involves the intruder stealing all the message or data transmitted. The information gathered by the intruder is stolen unethically.  
  
<div class="row mt-3">
<div class="col-sm mt-3 mt-md-0">
{% include figure.liquid loading="eager" path="assets/img/Security/release_message.jpeg" class="img-fluid rounded z-depth-1" %}
</div>
</div>
  
## Traffic Analysis
Masked traffic analysis is also one of the passive attack. It involves messages or data eing encrypted before transmission. The message being masked the intruder can't read the message but only understand the pattern and length of encryption.  
  
<div class="row mt-3">
<div class="col-sm mt-3 mt-md-0">
{% include figure.liquid loading="eager" path="assets/img/Security/traffic_analysis.jpeg" class="img-fluid rounded z-depth-1" %}
</div>
</div>
  
# Active Attack
> Attempt to alter system resources or affect their operation.  
  
It is relatively hard to prevent because it would require physical protection of all communications facilities and paths at all times, but easier to detect.  
  
There are four categories.
- Maquerade  
- Replay  
- Modification of messages  
- Denial of service  
  
## Masquerade Attack
The attacker tampers the information received by the receiver by claiming itself as the sender. It takes place when one entity pretends to be a different entity. It includes one of the other forms of active attack.  
  
<div class="row mt-3">
<div class="col-sm mt-3 mt-md-0">
{% include figure.liquid loading="eager" path="assets/img/Security/masquerade_attack.jpeg" class="img-fluid rounded z-depth-1" %}
</div>
</div>  
  
## Replay Attack
The attacker attacks the transmitted message through a passive channel and make the final message received by the receiver may appear to be authorized and safe. It involves the passive capture of a previously transmitted message and replaying it to produce an unauthorized effect.  
  
<div class="row mt-3">
<div class="col-sm mt-3 mt-md-0">
{% include figure.liquid loading="eager" path="assets/img/Security/replay.jpeg" class="img-fluid rounded z-depth-1" %}
</div>
</div>  
  
## Modification Attack
Some portion of a legitimate message is altered, or messages are delayed or reordered to produce an unauthorized effect.  
  
<div class="row mt-3">
<div class="col-sm mt-3 mt-md-0">
{% include figure.liquid loading="eager" path="assets/img/Security/modification.jpeg" class="img-fluid rounded z-depth-1" %}
</div>
</div>  
  
## Denial of Service Attack
The receiver is prevented from receiving the transmitted message as there is an overflow of requests to the receiver, which makes the services hampered from their usual behavior.  
  
<div class="row mt-3">
<div class="col-sm mt-3 mt-md-0">
{% include figure.liquid loading="eager" path="assets/img/Security/server.jpeg" class="img-fluid rounded z-depth-1" %}
</div>
</div>  