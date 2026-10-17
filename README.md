# AWS Cloud Security Monitoring Lab

## Project Overview

This project documents a hands-on investigation of AWS account activity and network configuration using AWS CloudTrail, IAM, and Amazon VPC.

The objective is to develop practical cloud security skills by reviewing management events, interpreting AWS service activity, identifying security observations, and documenting recommendations.

## Objectives

- Investigate AWS management events using CloudTrail Event history.
- Analyse IAM API calls and assumed-role activity.
- Review VPC, subnet, route table, and internet gateway configuration.
- Distinguish expected service activity from events requiring further investigation.
- Document security findings and recommended remediation.
- Evaluate options for extending the investigation into continuous security monitoring.

## Environment

- Cloud provider: Amazon Web Services (AWS)
- Region: US East (N. Virginia), `us-east-1`
- Event investigation: AWS CloudTrail Event history
- Identity review: AWS Identity and Access Management (IAM)
- Network review: Amazon Virtual Private Cloud (VPC)

## Investigations Performed

### 1. CloudTrail Event Analysis

Reviewed management events, including:

- `AutomatedDefaultVpcCreation`
- `DescribeVpcs`
- `ListGroups`
- `AssumeRole`
- `CreateView`
- `SubscribeToURP`

### 2. IAM Activity

Investigated IAM group discovery and role-assumption events associated with AWS Resource Explorer.

The reviewed records identified AWS service-linked roles and read-only discovery operations consistent with Resource Explorer activity.

### 3. VPC Configuration Review

Inspected the default VPC and its network configuration.

Observations included:

- The VPC was in the Available state.
- Six subnets were listed for the VPC.
- The main route table contained a local route and an active default route to an internet gateway.
- The internet gateway was attached to the VPC.

An internet gateway route alone does not establish that a resource is publicly accessible. Public IP assignment, subnet routing, and security-group rules must also be assessed.

### 4. Security Recommendations

- Enable multi-factor authentication (MFA) for the root user.
- Continue reviewing management events for unexpected identity, network, and logging changes.
- Investigate unfamiliar source addresses and role assumptions in context.
- Avoid exposing access credentials or session tokens in screenshots and public repositories.
- Review service costs before enabling additional monitoring features.

## Findings and Limitations

The investigations described above were based on the AWS Console evidence reviewed during the lab.

No CloudTrail trail was configured during the documented investigation. The work therefore demonstrates retrospective event review, not continuous monitoring or automated alerting.

GuardDuty was not enabled as part of the documented work.

## Next Steps

- Review and document additional security-relevant events.
- Evaluate an appropriate logging and monitoring configuration.
- Implement a controlled test and verify the resulting evidence.
- Add sanitised screenshots and an investigation report.
- Document any costs, limitations, and remediation steps.

## Skills Demonstrated

AWS CloudTrail · IAM · Amazon VPC · Cloud Security Fundamentals · Log Analysis · Security Investigation · Network Configuration Review · Technical Documentation
This project uses an AWS account under the author's control for educational purposes. Findings reflect the configuration and events observed during the investigation and should not be interpreted as a complete security audit.
