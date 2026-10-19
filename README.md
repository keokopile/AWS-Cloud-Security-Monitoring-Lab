# AWS Cloud Security Monitoring Lab

## Project Overview

This project documents a practical AWS security review using CloudTrail, IAM, and Amazon VPC. It demonstrates how to inspect management events, interpret AWS activity, review network configuration, and identify security improvements.

## Objectives

- Investigate AWS CloudTrail management events.
- Interpret event names, sources, identities, regions, and read-only status.
- Inspect VPCs, subnets, route tables, and internet gateway configuration.
- Review IAM security recommendations and service-linked roles.
- Document findings and practical recommendations.

## Tools Used

- AWS CloudTrail
- AWS Identity and Access Management (IAM)
- Amazon Virtual Private Cloud (VPC)
- AWS Management Console

## Activities Performed

### CloudTrail Investigation

Reviewed events including `DescribeVpcs`, `AutomatedDefaultVpcCreation`, `ListGroups`, `AssumeRole`, and `CreateView`.

### Network Configuration Review

Inspected the default VPC, six listed subnets, the main route table, and an attached internet gateway. The route table included an active default route to the internet gateway.

An internet gateway alone does not prove that a workload is publicly accessible. Public exposure also depends on subnet settings, IP addressing, security groups, network ACLs, and other controls.

### IAM Security Review

Reviewed IAM security recommendations and service-linked roles. The captured IAM dashboard recommended enabling MFA for the root user; this remains a documented improvement, not a completed remediation.

## Findings and Recommendations

| Finding | Recommendation |
|---|---|
| Root-user MFA recommendation was displayed | Enable MFA and verify its status |
| No trails were listed on the reviewed CloudTrail Trails page | Assess whether a persistent trail is required |
| Default VPC has an internet gateway route | Review network exposure and access controls |
| AWS service-generated events appear in event history | Validate event context before treating activity as suspicious |

## Evidence

See the `screenshots/` folder for selected evidence from the lab.

## Limitations

This project documents the console evidence reviewed. It does not claim that automated alerts, GuardDuty detections, or a persistent multi-region trail were configured. The reviewed screenshots did not establish confirmed malicious activity.

## Future Improvements

- Complete root-user MFA setup.
- Review billing and service access before enabling additional services.
- Evaluate persistent CloudTrail logging and log protection.
- Add a documented detection-and-response exercise.
