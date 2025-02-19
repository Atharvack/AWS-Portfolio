

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
        
        NAMECHEAP[NAMECHEAP]
        ACM[ACM Certificate]
    end

    CF --> |HTTPS| EC2
    NAMECHEAP --> CF
   
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

<div class ="mermaid">


graph TB
    subgraph "DNS Management"
        NAMECHEAP[Namecheap]
        
    end

    subgraph "Content Delivery Network"
        CF[CloudFront Distribution]
        ACM[ACM Certificate]
    end

    subgraph "Backend Application"
        EC2[EC2 Django App]
        DJANGO[Django 4]
        HTML5[HTML5]
        BOOTSTRAP[Bootstrap 5]
        SASS[Sass]
        
        EC2 --> DJANGO
        DJANGO --> HTML5
        DJANGO --> BOOTSTRAP
        DJANGO --> SASS
    end

    NAMECHEAP --> CF
    ACM --> CF
    CF --> EC2


</div>

### Explanation

#### 1. DNS Management
- **Namecheap**: Manages the domain and DNS settings.
- **Route53**: Provides DNS management within AWS, pointing the custom domain to the CloudFront distribution.

#### 2. Content Delivery Network
- **CloudFront (CF)**: Distributes content globally with low latency. Acts as the CDN and caches content at edge locations.
- **ACM Certificate**: AWS Certificate Manager provides SSL/TLS certificates to secure the CloudFront distribution.

#### 3. Backend Application
- **EC2 Django App**: Runs the Django 4 application on a specific port within a VPC. This instance serves as the origin for CloudFront.
  - **Django 4**: The backend framework used for the application.
  - **HTML5**: The standard markup language for creating web pages.
  - **Bootstrap 5**: The front-end framework used for responsive design and styling.
  - **Sass**: A preprocessor scripting language that is interpreted or compiled into CSS.

### Summary of Setup
1. **DNS Setup**:
   - Configure DNS settings in Namecheap.
   - Point the custom domain to Route53.
   - Use Route53 to manage DNS records and point to the CloudFront distribution.

2. **CloudFront Configuration**:
   - Create a CloudFront distribution and set the origin to the EC2 instance.
   - Attach the ACM certificate for SSL/TLS to secure the CloudFront distribution.

3. **EC2 Configuration**:
   - Launch an EC2 instance running the Django 4 app on a specific port.
   - Ensure the instance is within a VPC and has appropriate security group settings.
   - Utilize HTML5, Bootstrap 5, and Sass for front-end development.

4. **Traffic Flow**:
   - Users access the custom domain, which is managed by Namecheap and routed through Route53.
   - Route53 directs traffic to CloudFront, which serves content from the EC2 instance.
   - CloudFront uses the ACM certificate to secure HTTPS traffic.

By following this setup, you can ensure a secure, scalable, and efficient architecture for your Django application with the specified technologies.

Let me know if you need further assistance or have any other questions!

## Usage

To deploy the architecture, follow these steps:

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/yourusername/AWS-Portfolio.git
