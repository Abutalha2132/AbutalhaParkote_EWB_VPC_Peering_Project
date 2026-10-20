# AWS VPC Peering – Remote Access Using Bastion with Private Workloads

## Project Overview

This project demonstrates cross-region communication between two Amazon Virtual Private Clouds (VPCs) using **AWS VPC Peering**. A Bastion Host provides SSH access to private EC2 instances, while route tables and security groups control communication between workloads.

The project was completed as part of the **AWS Cloud Internship at EWB Courses**.

## Project Information

| Detail | Information |
|---|---|
| Project Title | AWS VPC Peering |
| Organization | EWB Courses |
| Program | AWS Cloud Internship |
| Intern | Abutalha Parkote |
| Region 1 | Mumbai (`ap-south-1`) |
| Region 2 | Ireland (`eu-west-1`) |
| Peering Connection ID | `pcx-00bbde40ea1696919` |

## Architecture Overview

![Uploading AWS VPC Peering Architecture Diagram.png…]()


The architecture consists of two VPCs deployed in separate AWS regions.

### 1. Mumbai Region – VPC A

**VPC Name:** `EWB-VPC-A`

**Subnets**

| Subnet Name | CIDR Block | Purpose |
|---|---|---|
| `EWB-A-Public` | `10.10.1.0/24` | Hosts the Bastion Host |
| `EWB-A-Private` | `10.10.2.0/24` | Hosts the private application instance |

**EC2 Instances**

| Instance Name | Private IP | Purpose |
|---|---|---|
| `EWB-Bastion` | As configured in AWS | SSH entry point |
| `EWB-App-A` | `10.10.2.28` | Private application workload |

**Route Tables**

- `EWB-A-PublicRT`
- `EWB-A-PrivatRT`

**Security Groups**

- `EWB-SG-Bastion`
- `EWB-SG-App-A`

### 2. Ireland Region – VPC B

**VPC Name:** `EWB-VPC-B`

**Subnet**

| Subnet Name | CIDR Block | Purpose |
|---|---|---|
| `EWB-B-Private` | `10.20.1.0/24` | Hosts the private application instance |

**EC2 Instance**

| Instance Name | Private IP | Purpose |
|---|---|---|
| `EWB-App-B` | `10.20.1.240` | Private workload accessible through permitted network paths |

**Route Table**

- `EWB-B-Private-RT`

**Security Group**

- `EWB-SG-App-B`

## AWS Services Used

- **Amazon VPC:** Created isolated virtual networks in two AWS regions.
- **Amazon EC2:** Hosted the Bastion Host and private application instances.
- **VPC Peering:** Enabled private routing between the two VPCs.
- **Route Tables:** Defined local and inter-VPC traffic routes.
- **Security Groups:** Controlled inbound and outbound instance traffic.
- **SSH:** Provided administrative access to permitted instances.
- **ICMP (Ping):** Used to test network connectivity.

## Implementation Steps

1. Created and configured VPCs in the Mumbai and Ireland regions.
2. Created public and private subnets according to the architecture.
3. Launched EC2 instances, including a Bastion Host and private workloads.
4. Configured the required route tables and subnet associations.
5. Established the VPC Peering connection between the two VPCs.
6. Configured routes for communication between the VPC CIDR ranges.
7. Configured security group rules for permitted SSH and ICMP traffic.
8. Tested connectivity and troubleshot routing and security configuration issues.
9. Reviewed resource cleanup and AWS cost-control practices.

## Connectivity and Testing

The project focuses on validating the following network paths:

- Administrative SSH access to the Bastion Host.
- SSH access from the Bastion Host to permitted private instances.
- Private-IP communication between `EWB-App-A` and `EWB-App-B`.
- Forward and return routing through the VPC Peering connection.
- Controlled ICMP failure and recovery by adjusting security group rules.

Actual test results should be confirmed using the terminal output and AWS console evidence included in the project report.

## Challenges and Troubleshooting

During implementation, connectivity issues required checking the configuration of both VPCs.

The troubleshooting process included:

- Verifying the VPC Peering connection status.
- Checking route tables and subnet associations.
- Reviewing security group inbound rules.
- Validating SSH access and ICMP permissions.
- Checking forward and return routes between the two VPCs.

## Key Learnings

- Understanding cross-region VPC Peering.
- Configuring public and private subnets.
- Managing route tables and subnet associations.
- Accessing private EC2 instances through a Bastion Host.
- Troubleshooting network connectivity using SSH and ICMP.
- Applying security group rules to control network access.
- Understanding the importance of AWS resource cleanup and cost management.

## Security Considerations

- Keep private instances without public IP addresses where required by the design.
- Restrict SSH access to trusted sources.
- Allow only the necessary traffic through security groups.
- Never upload private keys, passwords, access tokens, or credentials to GitHub.
- Review public IP addresses and other sensitive configuration details before publishing the repository.

## Project Report

The complete project report is available in this repository as a PDF.

**Suggested file name:** `AbutalhaParkote_EWB_VPC_Peering_Report.pdf`

The report includes the project overview, architecture diagram, resource inventory, networking configuration, security rules, testing procedures, screenshots, troubleshooting notes, and conclusion.

## Conclusion

This project provided practical experience in AWS networking and secure communication between VPCs across different regions. It strengthened my understanding of VPC Peering, route tables, private EC2 access, security groups, and network troubleshooting.

The project also highlighted the importance of validating configurations, following security best practices, and removing unused resources to manage AWS costs effectively.

---

**Project completed as part of the AWS Cloud Internship at EWB Courses.**
