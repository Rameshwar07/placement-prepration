# AWS Cloud Interview Questions & Answers (3 Years Experience)

This document contains **50+ AWS interview questions with answers** tailored for 2–3 years of experience.  

---

## 🟢 AWS Basics

**1. What is AWS and why is it popular?**  
- AWS (Amazon Web Services) is the world’s largest cloud provider.  
- Provides on-demand compute, storage, networking, databases, DevOps, and AI/ML.  
- Popular due to scalability, pay-as-you-go pricing, and global reach.  

**2. Explain the AWS Global Infrastructure.**  
- **Regions** → Geographical locations (e.g., us-east-1).  
- **Availability Zones (AZs)** → Multiple data centers within a region.  
- **Edge Locations** → Used by CloudFront & Route53 for caching/DNS.  

**3. Difference between IaaS, PaaS, and SaaS with AWS examples.**  
- **IaaS** → EC2, EBS.  
- **PaaS** → Elastic Beanstalk, RDS.  
- **SaaS** → WorkMail, Chime.  

**4. What are the AWS Free Tier options?**  
- 12 months free (750 hrs EC2 t2.micro, 5 GB S3).  
- Always free (1M Lambda requests, 1M SNS, DynamoDB 25 GB).  

**5. Explain Shared Responsibility Model.**  
- **AWS** → Security *of* the cloud (hardware, network).  
- **Customer** → Security *in* the cloud (data, IAM, patching).  

---

## 🟡 EC2 (Elastic Compute Cloud)

**6. What is EC2?**  
- Virtual servers in AWS cloud.  

**7. How do you scale EC2 instances?**  
- **Vertical scaling** → Increase instance size.  
- **Horizontal scaling** → Use Auto Scaling Groups + Load Balancers.  

**8. Difference between On-Demand, Reserved, and Spot Instances.**  
- On-Demand → Pay as you go.  
- Reserved → 1/3 year commitment (cheaper).  
- Spot → Up to 90% cheaper, can be terminated.  

**9. How do you connect to an EC2 instance?**  
```bash
ssh -i mykey.pem ec2-user@<public-ip>
```

**10. What is a Security Group?**  
- Virtual firewall for EC2.  
- Controls inbound/outbound rules.  

**11. Difference between Security Group and NACL.**  
- SG → Stateful, instance-level.  
- NACL → Stateless, subnet-level.  

**12. How do you create a highly available EC2 setup?**  
- Use Auto Scaling across multiple AZs.  
- Attach Load Balancer.  

---

## 🔵 S3 (Simple Storage Service)

**13. What is Amazon S3?**  
- Object storage service for files.  

**14. Difference between S3 Standard, IA, and Glacier.**  
- Standard → Frequent access.  
- IA (Infrequent Access) → Cheaper, for backups.  
- Glacier → Archival, cheapest but slow retrieval.  

**15. How do you secure S3 data?**  
- Enable Bucket Policies, IAM roles.  
- Use Server-Side Encryption (SSE-S3, SSE-KMS).  
- Block Public Access.  

**16. What is S3 Versioning?**  
- Keeps multiple versions of the same object.  

**17. How do you enable static website hosting in S3?**  
- Enable "Static website hosting" option.  
- Upload HTML files.  
- Use bucket endpoint or Route53 custom domain.  

**18. How do you transfer large files to S3?**  
- Use Multipart Upload API.  
- Use AWS CLI:  
```bash
aws s3 cp largefile.zip s3://mybucket/
```

---

## 🟣 IAM (Identity & Access Management)

**19. What is IAM in AWS?**  
- Service to manage users, groups, roles, and permissions.  

**20. Difference between IAM User, Group, and Role.**  
- User → Individual identity.  
- Group → Collection of users.  
- Role → Temporary permissions, assumed by users or services.  

**21. How do you secure IAM accounts?**  
- Enable MFA.  
- Follow Least Privilege principle.  
- Rotate access keys.  

**22. What are IAM Policies?**  
- JSON documents that define permissions.  

**23. Difference between Inline Policy and Managed Policy.**  
- Inline → Directly attached to one user/role.  
- Managed → Reusable policy across accounts.  

---

## 🟤 VPC & Networking

**24. What is Amazon VPC?**  
- Virtual Private Cloud, isolated network in AWS.  

**25. What is a Subnet?**  
- Subdivision of a VPC, can be public or private.  

**26. Difference between Internet Gateway and NAT Gateway.**  
- IGW → Allows internet access for public subnets.  
- NAT GW → Allows private subnets to access internet.  

**27. How do you connect on-premises to AWS?**  
- VPN, Direct Connect.  

**28. What is VPC Peering?**  
- Connects two VPCs privately using AWS backbone.  

**29. What is Transit Gateway?**  
- Hub-and-spoke model to connect multiple VPCs and on-prem.  

---

## 🟠 Databases

**30. Difference between RDS and DynamoDB.**  
- RDS → Relational (SQL).  
- DynamoDB → NoSQL, key-value.  

**31. What is Multi-AZ in RDS?**  
- Automatic replication to standby in another AZ.  

**32. Difference between Read Replica and Multi-AZ.**  
- Read Replica → Scalability.  
- Multi-AZ → High Availability.  

**33. How do you encrypt RDS?**  
- Enable KMS encryption at creation.  

**34. How do you back up RDS?**  
- Automated backups + manual snapshots.  

---

## 🟢 Containers & DevOps

**35. What is ECS vs EKS?**  
- ECS → AWS managed container orchestration.  
- EKS → Managed Kubernetes.  

**36. What is Fargate?**  
- Serverless compute for containers (no EC2 needed).  

**37. How do you store container images in AWS?**  
- Amazon Elastic Container Registry (ECR).  

**38. How do you deploy a Kubernetes cluster in AWS?**  
- Use EKS with worker nodes (EC2 or Fargate).  

---

## 🟡 Monitoring & Security

**39. What is CloudWatch?**  
- Monitoring service (logs, metrics, alarms).  

**40. Difference between CloudTrail and CloudWatch.**  
- CloudTrail → Auditing API calls.  
- CloudWatch → Monitoring performance/logs.  

**41. How do you set up an alert in AWS?**  
- Create CloudWatch Alarm → SNS notification → Email/SMS.  

**42. What is AWS Config?**  
- Tracks AWS resource configurations & compliance.  

**43. What is GuardDuty?**  
- Threat detection service.  

**44. What is KMS?**  
- Key Management Service for encryption keys.  

---

## 🔵 High Availability & Scaling

**45. What is Auto Scaling?**  
- Automatically adjusts EC2 capacity.  

**46. What is Elastic Load Balancer (ELB)?**  
- Distributes traffic across multiple EC2 instances.  
- Types: Classic, ALB, NLB.  

**47. Difference between ALB and NLB.**  
- ALB → Layer 7 (HTTP/HTTPS).  
- NLB → Layer 4 (TCP/UDP).  

**48. What is Route 53?**  
- AWS DNS service with routing policies (simple, weighted, latency).  

**49. How do you achieve disaster recovery in AWS?**  
- Backup & Restore, Pilot Light, Warm Standby, Multi-Site.  

---

## 🟣 Advanced & Miscellaneous

**50. What is AWS Well-Architected Framework?**  
- 6 pillars: Operational Excellence, Security, Reliability, Performance Efficiency, Cost Optimization, Sustainability.  

**51. What is an AWS Landing Zone?**  
- Best practice multi-account setup with guardrails.  

**52. What is Organizations and SCPs?**  
- AWS Organizations → Manage multiple accounts.  
- SCPs → Service Control Policies for restricting accounts.  

**53. What is CloudFormation?**  
- Infrastructure as Code (IaC) service in AWS.  

**54. What is Elastic Beanstalk?**  
- PaaS for deploying applications quickly.  

**55. How do you migrate workloads to AWS?**  
- AWS Migration Hub, DMS (Database Migration Service), Server Migration Service.  

---
