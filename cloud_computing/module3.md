# S3 - Simple Storage Service

## What is S3
- Object storage in cloud
- Manages data as objects rather than in file systems or data blocks

### Basics
- Unlimited Storage: Total volume of data and objects is unlimited
- Objects up to 5TB in size
- Buckets instead of folders

## Working with S3
- Universal Namespace
    * All AWS accounts share same S3 namespace
    * Each S3 bucket is globally unique
- Example S3 URL: https://cs7346smu2023.s3.us-east-1.amazonaws.com/test.txt
- Server responds with HTTP 200 if upload successful

## Key-Value Store
- Key: Name of object
- Value: Data itself
- Version: store multiple versions of same object
- Metadata: content-type, last-modified, etc

## Availability and Durability
- Data is spread across multiple devices and zones
- 99.95% - 99.99% service availability
- Designed for 99.999999999% durability

## Standard S3
- Data stored in >=3 AZs
- Designed for frequent access
- Suitable for most workloads
    * Websites
    * Content distribution
    * Mobile and gaming apps

## Characteristics
- Tiered Storage
- Lifecycle Management: Can auto transition objects to cheaper storage tiers after time
- Versioning: All objects version are stored and retrievable

## Security
- Server-side encryption: Set default encryption on bucket
- Access Control List (ACLs): Define which accounts or groups are granted access
- Bucket Policies: Specify actions allowed or denied

## Storage Classes
- Frequenctly Accessed objects
    * S3 Standard
    * Reduced Redundency
- Automatically optimized: S3 Intelligent tiering
- Infrequently Accessed objects
    * S3 Standard-IA
    * S3 One Zone-IA
- Archiving Objects
    * S3 Glacier (Instant, Flexibile, or deep archive)

# S3 Object Lock
used for write once, read many (WORM)
- Prevent objects from being deleted or modified for a fixed time
- regulatory requirements if WORM is required
- Extra layer of protection

### 2 lock modes
- Governance Mode: User needs special permissions to modify
- Compliance mode: Users cannot overwrite
- Retention period for fixed time of protection
- Legal Hold: Prevent object from being overwritten

## Encryption
- Encryption in Transit: SSL, TLS, HTTPS
- Encryption at Rest (enabled by default)
    * SSE-S3: S3 managed keys using AES256
    * SSE-KMS: amazon managed keys
    * SSE-C: Customer provided keys
- Encryption at Rest
    * client side encryption
    * Encrypt before upload to S3