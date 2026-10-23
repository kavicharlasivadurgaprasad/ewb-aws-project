# AWS VPC Peering Project — EWB Cloud Labs

## Project Overview

This project demonstrates private communication between two Amazon Virtual Private Clouds (VPCs) using AWS VPC Peering. The infrastructure was configured in the AWS Mumbai Region (`ap-south-1`).

## Architecture

The project consists of two VPCs connected through an active VPC Peering connection.

- **VPC A:** `10.10.0.0/16`
- **VPC B:** `10.20.0.0/16`
- **VPC A public subnet:** `10.10.1.0/24`
- **VPC A private subnet:** `10.10.2.0/24`
- **VPC B private subnet:** `10.20.1.0/24`

### EC2 Instances

| Instance | Private IP | Purpose |
|---|---|---|
| Bastion host | `10.10.1.10` | Secure administrative access |
| App-A | `10.10.2.10` | Private application server in VPC A |
| App-B | `10.20.1.10` | Private application server in VPC B |

The EC2 instances were launched using Ubuntu 26.04.1 LTS.

## AWS Services Used

- Amazon VPC
- VPC Peering
- Amazon EC2
- Internet Gateway
- Route Tables
- Security Groups
- SSH and ICMP connectivity testing

## Implementation Steps

1. Created two VPCs with non-overlapping CIDR ranges.
2. Created public and private subnets.
3. Launched a bastion host and two private EC2 instances.
4. Created and activated the VPC Peering connection.
5. Added routes to enable communication between the VPCs.
6. Configured security groups to restrict SSH and ICMP traffic.
7. Connected to the private instances through the bastion host.
8. Tested connectivity in both directions.
9. Removed an ICMP rule temporarily to verify that connectivity failed, then restored the rule and confirmed connectivity recovered.

## Validation Results

- App-A to App-B ping: Successful.
- App-B to App-A ping: Successful.
- SSH access through the bastion host: Successful.
- Removing the relevant ICMP rule: Ping failed.
- Restoring the ICMP rule: Connectivity recovered.

## Security Considerations

- SSH access to the bastion host was restricted to the administrator's public IP.
- Private EC2 instances did not have public IPv4 addresses.
- Security groups allowed only the required administrative and ICMP traffic.
- Private subnets were configured without a NAT Gateway.
- AWS credentials and private SSH keys must never be committed to this repository.

## Project Outcome

Successfully established and tested private network communication between two AWS VPCs using VPC Peering, route-table configuration, and security-group rules.

## Important Note

This project used Ubuntu 26.04.1 LTS rather than the Amazon Linux 2023 AMI specified in the workbook. The network connectivity objectives were completed and verified.

## Author

**Siva Durga Prasad Kavicharla**

Project: EWB Cloud Labs — AWS VPC Peering