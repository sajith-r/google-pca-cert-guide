# Networking in Google Cloud: Network Architecture

## Introduction

- Key considerations
    - Scalability
    - Security and compliance
    - Performance
    - Cost efficiency

## Topologies

- Hub-and-spoke
    - VPC peering
    - Cloud VPN
    - Network Connectivity Center
        - VPC Spoke
        - Hybrid Spoke

- Mesh
    - Full mesh
    - Partial mesh

- Mirrored

- Gating --> fine-grained control over traffic flow
    - Gated ingress
    - Gated egress
    - Gated ingress and egress

# Best practices

- Meets the required SLA for performance and uptime
- Scale hub-and-spoke architecture with centralized hybrid connectivity
- Expose apps through APIs using API gateway or LB
- When using LB, utilize its app capacity optimization feature
- Use two authoritative DNS systems
