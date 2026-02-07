## Topics

- What is EC2
- Pricing Options
- Using roles
- Security groups and bootstrap scripts
- EC2 Metadata and user data
- Networking with EC2
- AWS Outposts

## What is EC2
- Stands for elastic compute cloud
- A virtual machine or server that is hosted in AWS
- Allows you to provision capacity when you need it
- You have complete control of your instances
- Launched in 2006
- Game changer for cloud computing
    * Organizations no longer needed to plan for compute and purchase servers
    * Can scale up and scale down on-demand

## EC2 Pricing
- Pay-as-you-go
- Pay less when you use more
- Pay less when you reserve capacity
- AWS Pricing calculator

- Tiers
    * On-Demand: Pay fixed rate by hour
    * Savings plan: Capacity reservation with discount. Upfront payment. 1 or 3 year contract.
    * Spot Instance: Bid a price for unused instance capacity
    * Reserved Instances (RI): Reserved on-demand. Significant discount
    * Dedicated Hosts: Physical EC2 server dedicated for your use. Allow users to use server-bound software license

### On-Demand use cases
- Low upfront cost and flexibility
- Short term, spiky, unpredictable workloads that cannot be interrupted
- Test or development

### Savings Plans use cases
- Consistent and steady-state usage
- Want to use different instance types and compute solutions
- Can make monetary commitment to use compute over 1 or 3 year term

### Spot Instances Use Cases
- Flexibile start and end
- Only feasible at very low compute
- Fault-Tolerant/stateless workload
- Only use for non-critical jobs

### Reserved Instances Use Cases
- Business critical event requiring capacity
- Regulatory requirement for high availability
- Disaster Recovery

### Dedicated Hosts Use Cases
- Regulatory Requirement for no multi-tenancy
- Licensing does not support multi-tenancy or cloud deployments

## IAM Role
- Identity in IAM, similar to user
- A role can be temporarily assigned to a user or instance
- Allows temporary permissions

## EC2 Instance Types
- General purpose: Balance of compute, memory, networking
- Compute Optimized: Ideal
- Memory Optimized
- Accelerated Computing
- Storage Optimized

## Security Groups
- Virtual firewall for EC2 instances
- Can assign multiple EC2 instances to a security group
- Can assign multiple security groups to EC2 instance
- To let everything in use IP address range 0.0.0.0/0
- In production, you'd only open 0.0.0.0/0 to port 80 (HTTP) and to port 443 (HTTPS)

## EC2 Metadata
- Private IP, public IP, hostname, security groups, etc.

# EC2 Networking

## ENI - Elastic Network Interface
For basic day-to-day networking. Attached by default.

- Virtual network allowing
    * Private + public IPv4
    * MAC address
    * security groups, IPv6

- Use Cases
    * Create managed network
    * Network and security application in cloud
    * Low budget, high avail solution


## EN - Enhanced Networking
Uses a single root I/O virtualization to provide high performance.

- 10 to 100 gigabits per second capacity
- Uses single root I/O virtualization or SR-IOV

## EFA - Elastic Fabric Adapter
Machine Learning.

- Network device that you can attach to EC2 Instance to accelerate HPC and machine learning
- Faster than TCP transport.

## AWS Outposts
- Rack or server that brings AWS cloud to on-prem.
- Useful for classified or airgapped deployments that need AWS.

# EBS - Elastic Block Store
Storage volumes you can attach to EC2 instance (virutal hard drives)

- Same use case as system disk
    * Create file system
    * Run a database
    * Run an operating system
    * Store data
    * Install applications

## Features
- **Production workloads:** Designed for mission critial workloads.
- **Highly available:** Automatically replicated within a single AZ to protect against hardware failures.
- **Scalable:** Dynamically inscrease capacity and change the volume type with no downtime or performance impact to live systems.

## SSD-backed Storage
For transational workloads
### General purpose SSD (gp3, gp2)
budget option
- Use Cases
    * Boot volume
    * Tsmall database
    * virtual desktop
    * gaming apps

### Provisioned IPS SSD (io2 and io1)
Highest performance, dutability, expensive
- Use Cases
    * Large databases
    * Latency sensitive workloads

## HHD-backed storage
For throughput intensive workloads (MapReduce, Log processing)

### Throughput optimized HDD (st1)
Low-cost magnetic storage
- Use cases:
    * Frequently accessed, throughput intensive workloads
    * Amazon EMR
    * ETL
    * Data Warehousing
    * Log Processing
    * Cannot be boot volume

### Cold HDD (sc1)
Lowest cost magnetic storage
- Use Cases:
    * Large, less frequently accessed data
    * Clod-data workloads

# IOPS vs Throughput

## IOPs

- Measure of number of read and write operations per second
- Important for quick transactions, low latency apps
- Ability to read and write very quickly

## Throughput
- Measure of number of bits read/written per second (MB/s)
- Important for large datasets, large size

# Volumes vs Snapshots

## Volumes
- Exist on EBS
- Virtual hard disks
- Need a minimum of 1 volume per EC2 instance
- OS is installed
- Same AZ as EC2 instance
- resize on the fly
- switch type on fly (ex: gp3 to io2)

## Snapshots
- Exist on S3
- Point-in-time copy of a volume

## Protecting EBS volumes with encryption
- Encrypted by default with AES-256
- uses AWS KMS and CMK to store key

## EC2 hibernation
- Data is kept on EBS when EC2 instance is stopped
- Data is destoryed when EC2 instance is terminated

## AMI
- Information required to launch an instance
- **Must specify:** Region, OS, 32 or 64 bit, launch permissions, root storage

# EFS - Elastic File System

- Managed network file system (NFS) that can be mounted on multiple EC2 instances
- Works with EC2 instances in multi-AZ
- High avail and scalable
- Expensive
- Native to Unix and Linux

## EFS Performance
- 1000s concurrent connections
- 10Gbps throughput
- Petabyte scaling

## EFS throughput
- Elastic: Spiky or unpredictable workloads
- Provisioned: Known workload requirements
- Bursting: throughput that scales

## EFS Storage Tiers
- EFS Standard
- EFS Standard-infrequent Access
- EFS intelligent-tiering
- EFS one zone
- EFIS one zone-infrequent access

# FSx for Windows File Server
Fully managed native microsoft file system
- runs windows server message block (SMB)
- Designed for windows and windows applications
- Supports AD user, ACLs, groups and security policies

# FSx for Lustre
- store directly on S3
- Use cases:
    * High performance compute
    * Machine learning
    * Media Data processing
    * Electronic Design automation