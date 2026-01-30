## Overview

The paper is a summary of cloud computing, its history, and various tradeoffs. The authors differentiate cloud computing from grid computing and utility computing.

## Definitions

- **Cloud Computing**: integration of distributed computing, parallel computing, utility computing + network storage, virtualization, load balance, high availablility. Can be provisioned on demand.
- **NIST definiton**:Cloud computing is a model for enabling ubiquitous, convenient, on-demand network access to a shared pool of configurable computing resources (e.g., networks, servers, storage, applications, and services) that can be rapidly provisioned and released with minimal management effort or service provider interaction.


- **Autonomic computing**: is a system that has self management capabilities

## Brief History

- Salesforce: Cloud computing started with salesforce in late 90s. Company provided their software as SaaS.
- Training: IN 2007, universties started offering classes for google and IBM clouds.
- **OpenStack**
    - July 2010
    - NASA and Rackspace collaborated with AMD, Intel, Dell
    - Provision local compute, storage, and network to make private cloud
- **Utility computing**
    - Started in the 60s
    - Share compute prices
    - Integrate servers, storage systems, and applications distributed around the world
    - Customers share and only pay for usage
- **Grid computing**
    - Group of computers coupled to form a virtual machine to perform large tasks
    - distributing tasks among various machines on the grid
    - solves the massive computing problems
- **Cloud computing**
    - combination of utility and grid computing
    - Cost savings + access to large compute and storage
- **Hybrid Computing**
    - Private + Public cloud
    - shared connectivity
- **Mobile Cloud Services**
    - mobile apps interface with cloud
- **Cloud Security**
    - constant battle of new encryption vs attacks
- **Cloud Design**
    - Can expand to a market without physical prescence

## Cloud Attributes
- On-Demand self-service
- Network Access
- Resource Pooling
- Rapid Elasticity
- Pay for what you use/Metered Service

## Service Models
- Infrastructure as a service (IaaS): Customers get raw compute and storage to build on
- Platform as a service (PaaS): Customers get a platform to dev on
- Software as a service (SaaS): Customers provided software over web

![Service Models](cloud-delivery.png)

## Deployment Model
- **Public cloud**: Amazon, Azure, Google 
- **Private Cloud**: Cloud within an org, higher security as network is internal
- **Community Cloud**: Private cloud shared between organizations
- **Hybrid cloud deployment**: Public + Private cloud networked together

## Software Development Changes
- Architecture needs to be cloud-compatable
- App should serve massive user base with huge data
- Services must be over internet
- Security should be high
- Services should be accesible over internet

## Paradigm Shifts
- Cloud Storage: Storage + compute in cloud
- Big Data: Clouds can distribute workload and handle massive datasets.
- Gaming: Server-side compute for gaming
- Internet of things (IoT): edge devices connected to cloud

## Cloud Security
Cloud vendors should encrypt stored passwords and seperate usernames/passwords to guard in the event of a breach.

- **Passwords**: used to connect to cloud services
- **Access Recovery**: Recover access to cloud
- **Encryption**: Use strong password encryption
- **Password Management**: Encourage strong passwords
- **Multi-factor auth**: Biometric, RSA, or USB key
- **Login Monitor**: Monitor for suspicious logins
- **Personal Devices**: Customers should only login on known safe devices to avoid key loggers
- **Virus, Malware, and Trojans**: Hacker attacks user machine to gain access to their cloud account

---

# Research Report: Cloud Computing - Evolution, Architecture, and Security Considerations

**Author:** Garrett Gruss
**Course:** Software Reliability Engineering
**Date:** January 2026

---

## Abstract

This report examines the evolution, architecture, and security considerations of cloud computing. Drawing from foundational literature, it traces cloud computing's development from early utility computing concepts through modern hybrid and mobile cloud deployments. The report analyzes the distinguishing characteristics of cloud computing, its service and deployment models, and the critical security challenges facing cloud environments today.

---

## 1. Introduction

Cloud computing has fundamentally transformed how organizations provision and consume computing resources. Rather than maintaining expensive on-premises infrastructure, organizations can now access virtually unlimited computing power, storage, and services on demand. This paradigm shift has enabled businesses of all sizes to leverage enterprise-grade technology without significant capital investment.

The National Institute of Standards and Technology (NIST) defines cloud computing as "a model for enabling ubiquitous, convenient, on-demand network access to a shared pool of configurable computing resources (e.g., networks, servers, storage, applications, and services) that can be rapidly provisioned and released with minimal management effort or service provider interaction" (Mell & Grance, 2011). This definition captures the essential nature of cloud computing: accessibility, flexibility, and efficiency.

This report synthesizes research on cloud computing to provide a comprehensive overview of its history, defining characteristics, service models, deployment strategies, and security considerations.

---

## 2. Historical Development

### 2.1 Foundational Concepts

Cloud computing did not emerge in isolation but evolved from several predecessor technologies. Utility computing, originating in the 1960s, introduced the concept of shared computing resources where customers pay only for what they use—similar to traditional utilities like electricity and water (Buyya et al., 2009). This economic model forms the financial foundation of modern cloud services.

Grid computing contributed the technical framework for distributed processing. By coupling groups of computers to form virtual machines capable of performing large computational tasks, grid computing demonstrated the feasibility of distributing workloads across geographically dispersed systems (Foster et al., 2008).

### 2.2 Commercial Evolution

The commercial cloud computing era began with Salesforce in the late 1990s, which pioneered the delivery of enterprise software as a service over the internet. This Software-as-a-Service (SaaS) model proved that complex business applications could be delivered reliably through web browsers without local installation.

Amazon Web Services launched in 2006, establishing the Infrastructure-as-a-Service (IaaS) model that would become the industry standard. By 2007, universities began offering courses on cloud technologies in partnership with Google and IBM, signaling the technology's mainstream acceptance (Zhang et al., 2010).

The open-source community made significant contributions with OpenStack in July 2010. This collaboration between NASA and Rackspace, supported by AMD, Intel, and Dell, provided organizations the tools to build private clouds using local compute, storage, and network resources (OpenStack Foundation, 2010).

---

## 3. Essential Characteristics

Cloud computing is distinguished by five essential characteristics as defined by NIST:

**On-Demand Self-Service:** Users can provision computing resources automatically without requiring human interaction with service providers. This capability enables rapid deployment and scaling of applications.

**Broad Network Access:** Resources are available over the network and accessed through standard mechanisms that promote use across heterogeneous platforms including mobile phones, tablets, laptops, and workstations.

**Resource Pooling:** Provider resources are pooled to serve multiple consumers using a multi-tenant model, with different physical and virtual resources dynamically assigned according to demand. Customers generally have no control or knowledge over the exact location of provided resources.

**Rapid Elasticity:** Capabilities can be elastically provisioned and released to scale rapidly with demand. To the consumer, available capabilities often appear unlimited and can be appropriated in any quantity at any time.

**Measured Service:** Cloud systems automatically control and optimize resource use by leveraging metering capabilities. Resource usage can be monitored, controlled, and reported, providing transparency for both provider and consumer.

---

## 4. Service Models

Cloud computing services are categorized into three primary models, each offering different levels of abstraction and management responsibility:

### 4.1 Infrastructure as a Service (IaaS)

IaaS provides fundamental computing resources including processing, storage, and networks. Consumers deploy and run arbitrary software including operating systems and applications. The consumer does not manage the underlying cloud infrastructure but has control over operating systems, storage, and deployed applications. Examples include Amazon EC2, Microsoft Azure Virtual Machines, and Google Compute Engine.

### 4.2 Platform as a Service (PaaS)

PaaS provides a platform allowing customers to develop, run, and manage applications without the complexity of building and maintaining infrastructure. The consumer deploys applications created using programming languages, libraries, and tools supported by the provider. Examples include Google App Engine, Heroku, and Microsoft Azure App Service.

### 4.3 Software as a Service (SaaS)

SaaS provides complete applications running on cloud infrastructure. The consumer does not manage infrastructure or platform capabilities; they simply use the application. This model offers the highest level of abstraction and lowest management burden for consumers. Examples include Salesforce, Microsoft 365, and Google Workspace.

---

## 5. Deployment Models

Organizations can deploy cloud resources through four primary models:

**Public Cloud:** Infrastructure is provisioned for open use by the general public and owned by cloud service providers such as Amazon, Microsoft, and Google. This model offers the greatest economies of scale but less control over security and compliance.

**Private Cloud:** Infrastructure is provisioned for exclusive use by a single organization. Private clouds offer greater control and security as the network remains internal, making them suitable for organizations with strict regulatory requirements.

**Community Cloud:** Infrastructure is shared by several organizations with common concerns such as security requirements, policy, or compliance considerations. This model balances cost sharing with restricted access.

**Hybrid Cloud:** A composition of two or more distinct cloud infrastructures (private, community, or public) that remain unique entities but are bound together by standardized technology enabling data and application portability.

---

## 6. Security Considerations

Cloud security presents unique challenges that require comprehensive approaches spanning technical controls, policies, and user education.

### 6.1 Authentication and Access Control

Strong authentication mechanisms are critical in cloud environments. Multi-factor authentication combining passwords with biometric verification, RSA tokens, or USB security keys significantly reduces unauthorized access risk. Cloud vendors must encrypt stored passwords and maintain separation between authentication credentials to limit breach impact (Subashini & Kavitha, 2011).

### 6.2 Monitoring and Detection

Continuous monitoring for suspicious login activity enables rapid detection of potential security incidents. Anomaly detection systems can identify unusual access patterns that may indicate compromised credentials or insider threats.

### 6.3 Endpoint Security

Cloud security extends beyond the provider's infrastructure to customer endpoints. Users must access cloud services only from known, secure devices to avoid credential theft through keyloggers and other malware. Viruses, malware, and trojans targeting user machines remain a primary vector for cloud account compromise.

### 6.4 Data Protection

Encryption of data both in transit and at rest provides essential protection against interception and unauthorized access. Access recovery mechanisms must balance usability with security to prevent both lockout and unauthorized recovery attempts.

---

## 7. Impact on Software Development

Cloud computing has necessitated significant changes in software development practices:

- Architecture must be designed for cloud compatibility, embracing distributed systems principles
- Applications should scale to serve massive user bases handling substantial data volumes
- Services must be accessible over the internet with appropriate security controls
- Development teams must consider cloud-native patterns including microservices, containers, and serverless computing

---

## 8. Conclusion

Cloud computing represents a convergence of utility computing's economic model with grid computing's distributed architecture, enhanced by virtualization and modern networking. Its evolution from Salesforce's pioneering SaaS offering through today's sophisticated hybrid and multi-cloud deployments demonstrates continuous innovation in how computing resources are provisioned and consumed.

The five essential characteristics—on-demand self-service, broad network access, resource pooling, rapid elasticity, and measured service—distinguish cloud computing from traditional IT models. Organizations must carefully evaluate service models (IaaS, PaaS, SaaS) and deployment options (public, private, community, hybrid) against their specific requirements.

Security remains a critical consideration requiring comprehensive approaches spanning authentication, monitoring, endpoint protection, and data encryption. As cloud adoption continues to accelerate, addressing these security challenges while maintaining the agility and cost benefits of cloud computing will remain a central focus for both providers and consumers.

---

## References

Buyya, R., Yeo, C. S., Venugopal, S., Broberg, J., & Brandic, I. (2009). Cloud computing and emerging IT platforms: Vision, hype, and reality for delivering computing as the 5th utility. *Future Generation Computer Systems*, 25(6), 599-616.

Foster, I., Zhao, Y., Raicu, I., & Lu, S. (2008). Cloud computing and grid computing 360-degree compared. *2008 Grid Computing Environments Workshop*, 1-10.

Mell, P., & Grance, T. (2011). The NIST definition of cloud computing. *National Institute of Standards and Technology Special Publication 800-145*.

OpenStack Foundation. (2010). OpenStack: The open source cloud operating system. Retrieved from https://www.openstack.org/

Subashini, S., & Kavitha, V. (2011). A survey on security issues in service delivery models of cloud computing. *Journal of Network and Computer Applications*, 34(1), 1-11.

Zhang, Q., Cheng, L., & Boutaba, R. (2010). Cloud computing: State-of-the-art and research challenges. *Journal of Internet Services and Applications*, 1(1), 7-18.
