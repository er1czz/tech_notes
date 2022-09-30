# Infrastructure Protection
## Protection via Isolation
Infrastructure protection ensures that systems and resources within your workloads are protected against unintended and unauthorized access, and other potential vulnerabilities. Amazon Virtual Private Cloud (Amazon VPC) allows you to isolate your AWS resources in the cloud. A VPC enables you to launch resources into a virtual network that you've defined and that closely resembles a traditional network that you'd operate in your own data center. 

### Common VPC features (defense-in-depth approach)
- Subnet routing: subnets enable you to group instance and AWS resources based on your security and operational needs.
- Network ACLs: Access Control List, optional layer of security for VPC as a firewall for controlling traffic at the subnet level.
- Security group: acts as a virtual firewalll for instance to control inbound and outbound traffic. When you lauch an instance in a VPC, you must specify a security group for the instance. ... Traffic can be restricted by IP protocol, service port, and source/destination IP address.
- Additional AWS services: AWS Firewall Manager, AWS Direct Connect, AWS CloudFormation.

### AWS Systems Manager Features
- Automation, inventory, patch manager, parameter store, run command, session manager
- Amazon Inspector: an automated security assessment service
    - Using Amazon Inspector with AWS Lambda allows you to automate certain security tasks.

# Data Protection
### protection in transit
- Any data that gets transmitted from one system to another is considered data in transit.
- AWS services provide HTTPS endpoints using TLS for communication, thus providing end-to-end encryption when communicating with the AWS APIs.
- Use AWS to generate, deploy, and manage public and private certificates used for TLS encryption in web-based workloads.
- Use IPsec with VPN connectivity into AWS to facilitate encryption of traffic.
- Additional: 
    -  AWS CloudHSM (Hardware Security Modules): generate, store, import, export, and manage cryptographic keys.
    -  Amazon S3 glacier: infrequently used data, archiving and backup
    -  AWS Certificate Manager (ACM): create and manage public SSL/TLS certificate, can issue private SSL/TLS X.509 certificate.
    -  Amazon Macie: use ML to discover, classify, and protect sensitive data (such as personally identifiable info, PII) in AWS.

### DDOS Mitigation
- AWS Edge locations provide an additional layer of network infrastructure that increases your ability to absorb DDoS attacks and to isolate faults while minimizing availability impact. 
- Edge locations are physical data centers located in key cities, that are different from Availability Zones. 
- out-of-region protection
    - Amazon Route 53: highly available and scalable DNS service that can be used to direct traffic to your web application. 
    - Amazon CloudFront: content delivery network (CDN) service that can be used to deliver data, including your entire website, to end users. 
    - AWS Shield: a managed DDoS protection service that safeguards web applications that run on AWS.
    - AWS Web Application Firewall (WAF)

### AWS Well-Architected Tool
- a self-service tool that is designed to help customers review AWS workloads at any time, without the need for an AWS Solutions Architect.
- five pillars: Operational Excellence, Security, Reliability, Performance Efficiency, and Cost Optimization. 
- no charge for the AWS Well-Architected Tool; you pay only for any AWS resources that you consume.
