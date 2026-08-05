

Assessment test
## Networking
VPC: Amazon VPC (Virtual Private Cloud) is a logical boundary isolated with network, within
the aws cloud. Users can launch and manage aws resources securely.
## Compute
Instance type :
- An EC2 Instance Type defines the hardware configuration of an Amazon EC2 virtual
machine.
- It specifies the CPU, memory, storage, and networking capacity available to the
instance.
- Balanced compute, memory, and networking.
- Examples: t3, m5.
## Auto Scaling:
- Auto Scaling in AWS automatically adjusts the number of EC2 instances (or other
resources) in response to changing demand.
- It ensures applications have the right amount of capacity at the right time, improving
availability and cost efficiency.
## Storage
Differentiate S3/EBS/EFS and use cases
Feature Amazon S3 Amazon EBS Amazon EFS
Type Object Storage Block Storage File Storage (NFS)
Access Accessible via APIs,
SDKs, or web
Attached to a single
EC2 instance
Shared access across
multiple EC2 instances
Persistence Independent of EC2
lifecycle
Persists independently
of EC2 lifecycle
Persists independently,
scales automatically
## Scope Global (region-wide,
accessible anywhere)
Single Availability Zone Multi-AZ (replicated
across AZs)
Performance High durability,
scalable throughput
High IOPS, low latency Scalable throughput,
elastic capacity

Assessment test
Use Cases Backups, static website
hosting, data lakes,
media storage
Databases, boot
volumes, transactional
workloads
Shared web content,
container clusters, big
data analytics
Cost Model Pay per GB stored +
requests
Pay per GB provisioned Pay per GB stored +
throughput

EFS Sharing
- Amazon Elastic File System (EFS) is a fully managed, scalable file storage service that can
be mounted on multiple EC2 instances simultaneously. It uses the NFS (Network File
System) protocol, allowing shared access to files across instances in a VPC.
How EFS Sharing Works
- First creating EFS file
- Mounting is created in the AZ of the VPC
- EC2 connected to EFS by mounting NFS mount command
- Multiple EC2 can read/write to same files
- Data is replicated automatically in AZ with durability and availability.
Static website Hosting
- Firstly creating s3 Bucket and Enabling the static website hosting.
- To access publicly unblock all the public access
- Specifying the index document (e.g: index.html)
- Adding bucket policy to grant s3.GetObject
- After enabling hosting, AWS provides a website endpoint (e.g., http://your-bucket-
name.s3-website-us-east-1.amazonaws.com).
## Troubleshooting
- I have gone through private server deploying later I have researched in AI and
resolved it.
- EFS mounting troubleshooted by entering in the server and file sharing in two
IP’s.
- S3 bucket creation and Enabling static website hosting .
- Blocking public access in s3 permission and resolved the public access.
- Cloudflare deployment and website url pasting in the browser.