---
layout: blog
topic: Azure
title: AZ-900 Azure Fundamentals
tags:  datascience data azure
comments: true
date: 2022-10-26
---

# AZ-900: Azure Fundamentals

- [Cloud Computing](#cloud-computing)
  - [Dedicated Server](#dedicated-server)
  - [Virtual Private Server](#virtual-private-server)
  - [Shared Hosting](#shared-hosting)
  - [Cloud Hosting](#cloud-hosting)
- [Dedicated vs VM vs Containers vs Functions](#dedicated-vs-vm-vs-containers-vs-functions)
  - [Dedicated](#dedicated)
  - [Virtual Machines](#virtual-machines)
  - [Containers](#containers)
  - [Functions](#functions)
- [SaaS vs PaaS vs IaaS](#saas-vs-paas-vs-iaas)
- [Azure Deployment mODEL](#azure-deployment-model)
  - [Public Cloud](#public-cloud)
  - [Private Cloud](#private-cloud)
  - [Hybrid](#hybrid)
  - [Cross-cloud](#cross-cloud)
- [High Availability (HA)](#high-availability-ha)
- [High Scalability](#high-scalability)
- [High Elasticity](#high-elasticity)
- [High Durability](#high-durability)
- [Global Infrastructure](#global-infrastructure)
  - [Region](#region)
    - [Sovereign Regions](#sovereign-regions)
  - [Geography](#geography)
  - [Availability Zones (AZ)](#availability-zones-az)
  - [Availability Sets](#availability-sets)
- [Redundancy](#redundancy)
  - [Redundancy in the primary region](#redundancy-in-the-primary-region)
    - [Locally redundant storage (LRS)](#locally-redundant-storage-lrs)
    - [Zone-redundant storage (ZRS)](#zone-redundant-storage-zrs)
  - [Redundancy in the secondary region](#redundancy-in-the-secondary-region)
    - [Geo-redundant storage](#geo-redundant-storage)
    - [Geo-zone-redundant storage](#geo-zone-redundant-storage)
- [Defense-in-depth](#defense-in-depth)
- [Scale Sets](#scale-sets)
- [IoT](#iot)

## Cloud Computing

### Dedicated Server
- One physical machine
- Used by one business
- Runs a single website/app
- Very expensive, high maintenance, high security

### Virtual Private Server
- One physical machine virtualized into sub-machines
- Used by one business
- Runs multiple website/apps

### Shared Hosting
- One physical machine virtualized into sub-machines
- Used by multiple business
- Very cheap, very limited

### Cloud Hosting
- Multiple physical machines act as one system
- The system is abstracted into multiple cloud services
- Flexible, scalable, secure, cost-effective, high configurability

## Dedicated vs VM vs Containers vs Functions

### Dedicated
- A physical server used by only one customer
- Capacity not elastic, maybe unerpaying or overpaying for capacity
- Ungrading will be expensive
- Limited by the operating system
  
![](/assets/2022-10-27-09-44-29.png)

### Virtual Machines
- **Hypervisor** can build multiple VMs to run on one physical server
- Pay for a fraction of the server
- Limited by the guest operating system
- Multiple apps on a single VM can result in conflicts in resource sharing

![](/assets/2022-10-27-09-49-28.png)

### Containers
- **Docker Deamon** allows multiple containers to run on a VM
- Maximize the utility of available capacity
- More cost effective
- Apps not limited to the Guest OS and will not cause conflicts during resources sharing

![](/assets/2022-10-27-09-50-51.png)

### Functions
- AKA **Serverless Computing**
- Only responsible for the code and data
- Extremely cost effective, only pay for the time code is running 
- Cold Start: has to wait for a server to start before the code will execute
  
![](/assets/2022-10-27-09-55-21.png)

## SaaS vs PaaS vs IaaS

![](/assets/2022-10-24-19-08-16.png)

![](/assets/2022-10-27-00-01-38.png)

## Azure Deployment mODEL

### Public Cloud

- Everything built on the cloud service provider
- AKA cloud native
- Most cost effective, organizations pay only for what they use	and no capital expenditures to scale up	
- Organizations don’t have complete control over resources and security	


### Private Cloud

- Everthing built on the company's servers
- AKA on-premise
- Most expensive
- Hardware must be purchased for startup and maintenance	
- Organizations are responsible for hardware maintenance and updates	
- Organizations have complete control over resources and security	

### Hybrid
- Use both on-premise and cloud service provider
- Organizations control security, compliance, or legal requirements


### Cross-cloud
- Use multiple cloud service providers
- AKA multi-cloud, hybrid-cloud

## High Availability (HA)
- Services remain available by ensuring there is no **single point of failure**
- Running workload across multiple **availability zone** 

## High Scalability 
- Increase capacity based on increasing demand of traffic, memory and computing power
- Vertical scaling: upgrade to a bigger server
- Horizontal scaling: add more servers

## High Elasticity
- Ability to automatically adjust capacity based on demand

## High Durability
- Ability to recover from a disaster, aka Disaster Recovery (DR)

## Global Infrastructure

### Region
- A group of multiple data centers
- Each region is paired with another region 300 miles away; only one region is updated at a time to ensure no outages

#### Sovereign Regions
- Instances of Azure that are isolated from the main instance of Azure. - - Use sovereign region for compliance or legal purposes.

Azure sovereign regions include:

US DoD Central, US Gov Virginia, US Gov Iowa and more: These regions are physical and logical network-isolated instances of Azure for U.S. government agencies and partners. These datacenters are operated by screened U.S. personnel and include additional compliance certifications.
China East, China North, and more: These regions are available through a unique partnership between Microsoft and 21Vianet, whereby Microsoft doesn't directly maintain the datacenters.
### Geography
- A discreet market of two or more regions that preserves data residency and complicance boundaries

### Availability Zones (AZ)
- A physical location made up of more or more data center
- A region generally has 3 availability zones
- High Availability: 
  - For all VMs that have two or more instances deployed across two or more AZs -> 99.99% SLA (Service level agreement)
  - For all VMs that have two or more instances deployed in the same AZ -> 99.95% SLA (Service level agreement)
- **Recommended Regions** are supposed to have 3 AZs
- Regions that does not support az are known as **Alternate** or **Other**

### Availability Sets
- A logical grouping of VMs that have different fault domain and update domains to avoid downtime
- Each VM in an availability set is assigned a fault domain and update domain
  - Fault domain: a group of servers that share a common power source and network switch - a single point of failure
  - Update domain: a group of servers that can be updated and rebooted at the same time

## Redundancy

### Redundancy in the primary region

#### Locally redundant storage (LRS)
- LRS replicates data three times within a single data center in the primary region. 
- LRS provides at least 11 nines of durability (99.999999999%) of objects over a given year.

#### Zone-redundant storage (ZRS)
- ZRS replicates  Azure Storage data synchronously across three AZs in the primary region. Z
- RS offers durability for Azure Storage data objects of at least 12 nines (99.9999999999%) over a given year.

### Redundancy in the secondary region

#### Geo-redundant storage
- GRS copies data synchronously three times within a single physical location in the primary region using LRS. It then copies  data asynchronously to a single physical location in the secondary region (the region pair) using LRS. 
- GRS offers durability for Azure Storage data objects of at least 16 nines (99.99999999999999%) over a given year.

#### Geo-zone-redundant storage
- Data is replicated data across three AZs in the primary region (similar to ZRS) and is also replicated to a secondary geographic region, using LRS, for protection from regional disasters. Microsoft recommends using GZRS for applications requiring
- Provides maximum consistency, durability, and availability, excellent performance, and resilience for disaster recovery.

## Defense-in-depth

![](/assets/2022-10-28-01-13-36.png)

- The physical security layer is the first line of defense to protect computing hardware in the datacenter.
- The identity and access layer controls access to infrastructure and change control.
- The perimeter layer uses distributed denial of service (DDoS) protection to filter large-scale attacks before they can cause a denial of service for users.
- The network layer limits communication between resources through - segmentation and access controls.
- The compute layer secures access to virtual machines.
- The application layer helps ensure that applications are secure and free of security vulnerabilities.
- The data layer controls access to business and customer data that you need to protect.
  
## Scale Sets
- Group together identical VMs to automatically increases or decrease the number of servers based on:
  - change in CPU, memory, network performance
  - on a predefined schedule

## IoT
- A network of Internet connected objects able to collect and exchange data




