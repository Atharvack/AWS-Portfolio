

# AWS-Portfolio

This repository showcases a easy walkthrough of AWS services used to host a Django application. This architecture has been followed by me to host my own portfolio website. 

## Architecture

<script>
  (function() {
    var script = document.createElement("script");
    script.src = "https://cdn.jsdelivr.net/npm/mermaid@9/dist/mermaid.min.js";
    script.onload = function() {
      mermaid.initialize({ startOnLoad: true });
    };
    document.head.appendChild(script);
  })();
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
        NAMECHEAP[NAMECHEAP (Custom domain)]
        ACM[ACM Certificate]
    end

    CF --> |HTTPS| --> EC2
    NAMECHEAP --> CF
    ACM --> CF
</div>


## Important Components

### 1. CloudFront
AWS CloudFront is used to distribute content globally with low latency. It acts as a CDN that caches content at edge locations.


### 2. VPC and Security Group
The EC2 instance is hosted within a Virtual Private Cloud (VPC) and associated with a Security Group to control inbound and outbound traffic.

### 3. DNS & SSL
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
- **EC2 Django App**: Running on a custom port. This instance serves as the origin for CloudFront.
- **Django 4**: The backend framework used for the application.
- **HTML5**: The standard markup language for creating web pages.
- **Bootstrap 5**: The front-end framework used for responsive design and styling.
- **Sass**: A preprocessor scripting language that is interpreted or compiled into CSS.



### NOTE -> Since the site does not expect a lot of traffic, an application load balancer is not used. This helps to reduce complexity and costs while still providing the necessary functionality.

By following this setup, you can ensure a secure, scalable, and efficient architecture for your Django application with the specified technologies.

Let me know if you need further assistance or have any other questions!

## Contact
For any questions or inquiries, please contact:

- **LinkedIn**: [Your LinkedIn Profile](https://www.linkedin.com/in/atharvack)
- **GitHub**: [Your GitHub Profile](https://github.com/atharvack)

## License
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.


