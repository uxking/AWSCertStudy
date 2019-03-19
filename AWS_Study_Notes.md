# AWS Study Notes

## Security Features that AWS Provides and Best Practices 

## Network Security
- Secure network access - https/tls  
- Egress and ingress filtering via NACL (stateless)
- Instance security groups (stateful)
- Private subnets
- Add IPSEC VPN tunnels
- End to end encrypted transmissions
- Dedicated connection options
    - Direct connect (both public and private addresses)
- Advanced cipher suites
    - ELB and CloudFront can utilize and provide Perfect Forward Secrecy
## Access Control
- API request authentication
- SSH access to instances
    - RSA keys
- Unique users
    - IAM 
- MFA
    - root, IAM users can - use with CloudTrail, CloudWatch, SNS
- S3 bucket and object fine grained access
- IAM for local account
- ACLs for access from other AWS accounts
- CloudFront - geo restriction, Signed URLs
- Temporary access - AD on premis - 1 to 12 hours and will expire
## Monitoring and Logging
- Asset identification and config
- CloudConfig monitors for changes
- Not all resources supported
- Security Logs - CloudTrail logs all api calls
- CloudWatch - set alarms/monitor resources
    - Can centralize (apache, other type to CloudWatch)
- Logging of S3 bucket access (access logs)
    - request type, request source, IP, date/time
- Trusted Advisor
    - Open ports, unrestricted access, MFA, IAM passwords, CloudTrail, Route 53 SPF/MX, ELB Listener and ELB Security groups
## Backup and Replication
- EBS Data backups (snapshots)
    - multiple physical locations
    - encrypted if ebs volume is encrypted
    - stored in S3
- Redshift snapshots 
- RDS db instance replication
    - Multi-AZ failover, synchrous replication to a standby in other AZ
- S3 versioning
- Automated archiving to Glacier
- MFA accidental deletion
- Backups for on-premise
    - AWS Storage Gateway to S3

## Data Encryption
- Encrypted data storage - EBS, S3, Glacier, Redshift, SQLServer, MySQL
- Centralized key managment
    - AWS Key Managment
- Dedicated  CloudHSM hardware-based crytpo key storage

## Best Practices
- Limit ports
- Users use IAM - enforce passwords
- Least privilege
- RDS security groups lock down to the same region and utilize HTTPS
- CloudTrail enabled
- ELB security permissions and HTTPS/TLS
- Use IAM roles for EC2 (S3 buckets, SNI, etc..)
- Policy conditions for extra security
- Rotate API keys no less than once a year

# Elasticity and Scalability
## Definitions
- Elasticity - growna nd expande based on conditions
    - Time/schedule
    - Load
## S3
    - Unlimited number of files in any bucket same for bytes
    - Distribution of redundant copies
    - S3 Asynchronuse upload
    - Bandwidth
## Glacier
    - 4TBs of data storage
    - Unlimited number of archives
## EBS
- Easilty add new EBS
- Resize existing volumes via a snapshot (now able to modify without detaching the volume or stopping the instance)
- Redundantly replicated on different hardware in the same AZ
## AWS Import/Export
- Snail mail HD for import
- S3 files sizes can be 5 TB
- Glacier files are 4TBs
## Storage Gateway
- Connect on premise HW with AWS Cloud Storage S3
- Gateway-cached/gateway-stored volume configs allow unlimited files in S3
## CloudFront
- CDN
- Edge Locations
- Increased connections automatically based on demand
