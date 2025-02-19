

# AWS-Portfolio

This repository showcases a portfolio of AWS services used to host a Django application. The repo contains vivid illustration, which can be followed to host a website on cloud.

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
        
    end

    subgraph "DNS & SSL"
        
        NAMECHEAP[NAMECHEAP]
        ACM[ACM Certificate]
    end

    CF --> |HTTPS| EC2
    NAMECHEAP --> CF
    ACM --> CF
    
</div>


## Important Components

### 1. CloudFront
AWS CloudFront is used to distribute content globally with low latency. It acts as a CDN that caches content at edge locations.


### 2. VPC and Security Group
The EC2 instance is hosted within a Virtual Private Cloud (VPC) and associated with a Security Group to control inbound and outbound traffic.

### 4. DNS & SSL
- **Namecheap**: Domain management and DNS settings are configured using Namecheap.
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

    subgraph "Portfolio Application"
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


#### Portfolio Application Technical Stack
- **EC2 Django App**: Runs the Django 4 application on a specific port within a VPC. This instance serves as the origin for CloudFront.
  - **Django 4**: The backend framework used for the application.
  - **HTML5**: The standard markup language for creating web pages.
  - **Bootstrap 5**: The front-end framework used for responsive design and styling.
  - **Sass**: A preprocessor scripting language that is interpreted or compiled into CSS.

By following this setup, you can ensure a secure, scalable, and efficient architecture for your Django application with the specified technologies.

### NOTE -> Since the site does not expect a lot of traffic, an application load balancer is not used. This helps to reduce complexity and costs while still providing the necessary functionality.

Let me know if you need further assistance or have any other questions!
