---
layout: blog
course: Intro-Cybersecurity-Tools-&-Attacks
title: Security Services X800
tags: security cybersecurity service
comments: true
date: 2021-11-28
---

# Security Service: X.800

X.800 is a security architecture for open, interconnected systems. It was published by the [International Telecommunication Union](https://www.itu.int/rec/T-REC-X.800-199103-I/en) in 1991.

![X800](/assets/X800.PNG)

X.800 defines security service as `a service provided by a protocol layer of communicating open systems, which ensures adequate security of the systems or of data transfers`.

## Key Concepts

### Authentication
*   Peer Entity Authentication: to authenticate the entity sending the message
*   Data-Origin Authentication: to authenticate where the data is coming from

### Access Control 
*   To prevent unauthorized use of a resource

### Data Confidentiality
*   Connection Confidentiality: All user data is protected
*   Connectionless Confidentiality: Only user data in a single data block is protected
*   Selective-Field Confidentiality: Specific fields are protected
*   Traffic-flow Confidentiality： Protecting traffic flow from analysis

### Data Integrity 
*   To ensure that the data received is original with no modification, insertion, deletion, or replay

### Nonrepudiation
*   Protection against denial by one of the parties in a communication

_Source:
_1. [https://www.coursera.org/learn/introduction-cybersecurity-cyber-attacks](https://www.coursera.org/learn/introduction-cybersecurity-cyber-attacks)
_2. [https://people.cs.vt.edu/~hamid/cs6204/slides/Security_2.pdf](https://people.cs.vt.edu/~hamid/cs6204/slides/Security_2.pdf)
