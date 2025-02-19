# AWS-Portfolio

graph TB
    subgraph "Global Edge Network"
        CF[CloudFront Distribution]
    end

    subgraph "EC2"
        EC2[DJANGO APP]
        CF --> EC2
    end


    subgraph "DNS & SSL"
        NAMECHEAP[NAMECHEAP]
        ACM[ACM Certificate]
    end

    CF --> EC2    
    NAMECHEAP --> CF
    ACM --> CF
