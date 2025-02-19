

# AWS-Portfolio

This repository showcases a portfolio of AWS services used to host a Django application. The setup includes CloudFront for content delivery, an EC2 instance for hosting the application, and Namecheap for custom domain.

## Architecture

```mermaid
graph TB
    subgraph "Global Edge Network"
        CF[CloudFront Distribution]
    end

    subgraph "VPC"
        EC2[DJANGO APP]
        SG[Security Group]
        EC2 --> SG
    end

    subgraph "DNS & SSL"
        Route53[Route53 DNS]
        NAMECHEAP[NAMECHEAP]
        ACM[ACM Certificate]
    end

    CF --> |HTTPS| EC2
    NAMECHEAP --> Route53
    Route53 --> CF
    ACM --> CF
