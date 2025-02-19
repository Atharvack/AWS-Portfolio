

# AWS-Portfolio

This repository showcases a portfolio of AWS services used to host a Django application. The setup includes CloudFront for content delivery, an EC2 instance for hosting the application, and Namecheap for custom domain.

## Architecture

<script type="module">
  import mermaid from 'https://cdn.jsdelivr.net/npm/mermaid@9/dist/mermaid.esm.min.mjs';
  mermaid.initialize({startOnLoad:true});
</script>

<div class="mermaid">
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
</div>

## Components

### 1. CloudFront
AWS CloudFront is used to distribute content globally with low latency. It acts as a CDN that caches content at edge locations.

### 2. EC2 Instance
An EC2 instance running a Django application serves as the origin for CloudFront. The instance is secured within a VPC.

### 3. VPC and Security Group
The EC2 instance is hosted within a Virtual Private Cloud (VPC) and associated with a Security Group to control inbound and outbound traffic.

### 4. DNS & SSL
- **Namecheap**: Domain management and DNS settings are configured using Namecheap.
- **Route53**: Amazon Route53 is used for DNS management and pointing the custom domain to the CloudFront distribution.
- **ACM**: AWS Certificate Manager is used to manage SSL/TLS certificates for securing the website.

## Usage

To deploy the architecture, follow these steps:

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/yourusername/AWS-Portfolio.git
