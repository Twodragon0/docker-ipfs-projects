# Docker & IPFS Projects

> Consolidated repository for Docker and IPFS infrastructure projects

## 📋 Overview

This repository consolidates various Docker and IPFS-related projects, including containerization tools, IPFS deployments, and infrastructure automation.

## 🏗️ Architecture

### Docker & IPFS Infrastructure Architecture

```mermaid
graph TB
    subgraph "Development Environment"
        DEV[Developer<br/>Local Machine]
        DOCKER_BUILD[Docker Build<br/>docker-tools]
    end
    
    subgraph "Container Registry"
        REGISTRY[Docker Registry<br/>Public/Private]
    end
    
    subgraph "Orchestration Layer"
        K8S[Kubernetes<br/>ipfs-kubernetes]
        SWARM[Docker Swarm<br/>raspi-docker-stacks<br/>Multi-arch: arm/amd64]
    end
    
    subgraph "IPFS Network"
        IPFS_CLUSTER[IPFS Cluster<br/>Collaborative Nodes]
        IPFS_NODES[IPFS Nodes<br/>Distributed Storage]
        IPFS_GATEWAY[IPFS Gateway<br/>DNSLink]
    end
    
    subgraph "Edge Devices"
        RASPI[Raspberry Pi<br/>OpenWrt IPFS]
        JETSON[NVIDIA Jetson<br/>docker-jetson]
        PICAM[Pi Camera<br/>picam-ipfs]
    end
    
    DEV --> DOCKER_BUILD
    DOCKER_BUILD --> REGISTRY
    REGISTRY --> K8S
    REGISTRY --> SWARM
    K8S --> IPFS_CLUSTER
    SWARM --> IPFS_CLUSTER
    IPFS_CLUSTER --> IPFS_NODES
    IPFS_NODES --> IPFS_GATEWAY
    RASPI --> IPFS_CLUSTER
    JETSON --> SWARM
    PICAM --> IPFS_NODES
    
    style DEV fill:#e1f5ff
    style REGISTRY fill:#fff4e1
    style IPFS_CLUSTER fill:#e8f5e9
    style K8S fill:#f3e5f5
```

### Docker Tools Architecture

```mermaid
graph LR
    subgraph "Docker Tools"
        TERRAFORM[Terraform/Terragrunt<br/>IaC Containers]
        NODEJS[Node.js<br/>v12/v13/v14]
        SECURITY[Security Tools<br/>c7n-mailer<br/>githound]
        K8S_TOOLS[K8s Tools<br/>kubectl/helm/az]
        LOAD_TEST[Artillery.io<br/>Load Testing]
    end
    
    subgraph "Build Pipeline"
        BUILD[Build Scripts<br/>bin/build.sh]
        PUSH[Push Scripts<br/>bin/push.sh]
        VERSION[Version Management<br/>bin/version.sh]
    end
    
    TERRAFORM --> BUILD
    NODEJS --> BUILD
    SECURITY --> BUILD
    K8S_TOOLS --> BUILD
    LOAD_TEST --> BUILD
    BUILD --> VERSION
    VERSION --> PUSH
    
    style BUILD fill:#e1f5ff
    style PUSH fill:#fff4e1
```

## 📁 Projects

### Docker Tools

- **[docker-tools](./docker-tools/)** - Docker tooling for multiple use cases
  - Kerberos Docker images
  - Terraform/Terragrunt containers
  - Node.js containers (v12, v13, v14)
  - Security tools (c7n-mailer, githound)
  - Kubernetes tools (kubectl, helm, az)
  - Artillery.io for load testing

### IPFS Projects

- **[ipfs-kubernetes](./ipfs-kubernetes/)** - Dockerized IPFS using Kubernetes
- **[ipfs-cluster](./ipfs-cluster/)** - Collaborative clusters and DNSLink for IPFS-based Web
- **[OpenWRT-IPFS](./OpenWRT-IPFS/)** - IPFS in Raspberry Pi based on OpenWrt/Untangle/pfsense
- **[picam-ipfs](./picam-ipfs/)** - Raspberry Pi camera data repository using IPFS

### Infrastructure

- **[raspi-docker-stacks](./raspi-docker-stacks/)** - Collection of Docker Stacks for multi-architecture Docker Swarm cluster (arm, amd64)
- **[docker-jetson](./docker-jetson/)** - Docker images for NVIDIA Jetson devices

## 🚀 Quick Start

### Prerequisites

- Docker installed
- Docker Compose (for some projects)
- Kubernetes cluster (for IPFS Kubernetes deployment)

### Building Docker Images

Navigate to the specific project directory and follow the build instructions in each project's README.

Example:

```bash
cd docker-tools/terraform
docker build -t terraform:latest .
```

### IPFS Setup

For IPFS-related projects, ensure IPFS is installed and running:

```bash
ipfs init
ipfs daemon
```

## 📖 Project Structure

```
docker-ipfs-projects/
├── docker-tools/          # Various Docker tooling
│   ├── kerberos/
│   ├── terraform/
│   ├── nodejs/
│   └── ...
├── ipfs-kubernetes/       # Kubernetes IPFS deployment
├── ipfs-cluster/          # IPFS cluster setup
├── OpenWRT-IPFS/          # OpenWrt IPFS integration
├── picam-ipfs/            # Raspberry Pi camera IPFS
├── raspi-docker-stacks/   # Multi-arch Docker stacks
└── docker-jetson/         # Jetson Docker images
```

## 🔧 Features

- **Multi-architecture Support**: ARM and AMD64 support for Raspberry Pi and x86_64 systems
- **Security Tools**: Integration of security scanning and monitoring tools
- **Infrastructure Automation**: Terraform and Terragrunt containers for IaC
- **IPFS Integration**: Various IPFS deployment patterns and use cases

## 📚 Documentation

Each project contains its own README with detailed documentation:
- [docker-tools](./docker-tools/) - Docker tooling documentation
- [ipfs-cluster](./ipfs-cluster/) - IPFS cluster setup guide
- [OpenWRT-IPFS](./OpenWRT-IPFS/) - OpenWrt IPFS integration guide

## 🔒 Security Considerations

- All Docker images should be built from trusted base images
- Regularly update base images for security patches
- Use secrets management for sensitive configuration
- Follow Docker security best practices

## 📝 License

Please refer to individual project licenses.

## 👤 Author

**Twodragon**
- GitHub: [@Twodragon0](https://github.com/Twodragon0)
- Blog: [twodragon.tistory.com](https://twodragon.tistory.com)

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

---

**Last updated:** 2025-12-27
