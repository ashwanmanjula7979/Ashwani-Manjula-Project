

AWS Technical Discussion Answers
- Why Public vs. Private Subnets?
## Answer:
- Public Subnet: This is connected to an Internet Gateway (IGW), resources can be
accessed from the internet. It will route from internet gateway
- Use Cases: For web servers, load balancers, and bastion hosts.
- Private Subnet: It is not connected directly from internet access, uses internal
resources like databases. It is not a routed to IGW, but can we route through NAT
gateway for outbound traffic.
- Use cases: For databases, application servers, and backend services.

- Difference between EBS and EFS?
Feature Amazon EBS Amazon EFS
Type Block Storage Network File System (NFS)
Scope Single Availability Zone (AZ) Multi-AZ
## Access
Attached to a single EC2
instance
Concurrent access across 100s of
EC2s
## Performance
High IOPS for databases and
transactional workloads
Scalable throughput for shared file
storage
## Use Cases
Databases, application
servers,
Shared file storage, web content, big
Images, videos etc.
Mounting Attached as a block device Mounted via NFS protocol


- Why CloudFront?
CloudFront is a Content Delivery Network (CDN). It is a third-party Cloudflare.
- It is a server that delivers web content like ( images, videos, movies, etc.) to users.
Using a single origin for the users. CDN cache the content from all over the globe to
users.
- Edge Location: It is the nearest server that gives content to users in nearest places
like local areas
-  Lower Latency: Delivers content closer to the end user.
- Reduced Origin Load: Protects the backend S3 bucket or EC2 from direct traffic
spikes.

- EC2-EBS Communication?
- Amazon Elastic Block Store (EBS) provides block-level storage volumes for EC2
instances.
- Volumes are persistent and can be detached/reattached to different instances
within the same Availability Zone.
How EC2 Communicates with EBS
- When EBS volumes is attached to instances. it appears in block device (like a virtual
hard disk)
- The EC2 instance communicates with the EBS volume over the AWS internal
network within the same AZ
- Data transfer  via high-speed, low-latency connections, ensuring performance is
like local disks.
- The OS on EC2 uses standard disk I/O operations (read/write) to interact with the
EBS volume.
## Performance:
- General Purpose SSD (gp3/gp2) for balanced workloads.
- Provisioned IOPS SSD (io1/io2) for high-performance databases.



5.Purpose of vpc?
## Definition:
- Amazon VPC (Virtual Private Cloud) is a logical boundary isolated with network,
within the aws cloud. Users can launch and manage aws resources securely
Uses Within VPC
- You can define public and private subnets to control access to resources.
- Integrates with Security Groups and Network ACLs for traffic filtering.
- You can configure IP address ranges (CIDR blocks), route tables, and gateways.
- Enables fine-grained control over inbound and outbound traffic.
- You can create multiple subnets across Availability Zones for high availability.

- Secure EC2?
EC2(Elastic Cloud Compute) is like a clean slate. It is a resizable virtual server in the
cloud.
Securing EC2:
- Uses security group as virtual firewall to control inbound and outbound traffic.
- Apply Network ACLs (Access Control Lists) at the subnet level for additional
filtering.
- Other security level communication also can do it by using VPC Peering, VPN, or
Direct Connect. For secure purpose.
- Restrict SSH access using key pairs and limit source IPs in security groups.
- Enable CloudWatch for performance and security monitoring.
- Automate backups using Lifecycle Manager or AWS Backup.
## 7. Security Group?
## Definition:

A Security Group is a stateful firewall that controls traffic at the instance level, Security
Groups are used to define which traffic can reach specific EC2 instances.”
- It is a stateful because the return traffic is automatically allowed.
- All Rules evaluated together. No explicit denying.
- It cannot write explicit rules, it only allows.
- Default sg allows all outbound rules, deny Inbound rules until rules are added.

## 8. Route Tables.
## Definition:
A Route Table in AWS defines how network traffic is directed within a Virtual Private
Cloud (VPC).
It contains a set of rules (routes) that determine where network packets are sent —
whether to another subnet, an internet gateway, a NAT gateway, or a peering connection.
Purpose of RT:
- The route table is automatically created when you create a VPC.
- Custom RT can create by users not automatically created.
- RT is commonly used to separate public and private subnet routing.
- Route tables work with Security Groups and Network ACLs to control traffic flow.

## 9. Static Website Hosting.
## Definition:
Static website hosting refers to serving web pages that contain fixed content — HTML,
CSS, JavaScript, and media files — without server-side processing or dynamic database
interaction.
How it works:
- Create s3 bucket and upload files.
- Enabling static website hosting and specifying index document
- Configure Bucket Policy to allow public read access for website files.





## 10. Shared Storage Choices.
- EFS: Best for shared file storage across multiple EC2 instances.
- FSx: For specialized workloads (Windows file systems, Lustre for HPC).
- S3: For object storage and static content.
- Choice depends on workload:
o Shared web content → EFS
o High-performance computing → FSx Lustre
o Archival/static files → S3












