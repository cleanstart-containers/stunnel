# CleanStart Stunnel Container

## Overview

Stunnel is a proxy that adds TLS/SSL encryption to existing TCP connections without modifying application code. This CleanStart container provides a production-ready, security-hardened stunnel image optimized for enterprise environments. Built on a minimal base OS with comprehensive security hardening, this image delivers reliable SSL/TLS tunneling with advanced security features.

## What is Stunnel?

Stunnel uses the OpenSSL library to wrap existing TCP connections with SSL/TLS encryption. It can act as either an SSL server (accepting encrypted connections) or an SSL client (creating encrypted connections), making it ideal for adding encryption to legacy applications and services.

### Basic Concepts

**Server Mode**: Accepts SSL/TLS encrypted connections and forwards decrypted traffic to backend service

**Client Mode**: Accepts plain connections and forwards encrypted traffic to SSL/TLS server

## About CleanStart

CleanStart is a comprehensive container registry providing security-hardened, enterprise-ready container images. Our images are designed with security-first principles, featuring minimal attack surfaces, regular security updates, and compliance with industry standards.

### About CleanStart Images

CleanStart images are built on secure, minimal base operating systems and optimized for production environments. Each image undergoes rigorous security testing, vulnerability scanning, and compliance validation to ensure enterprise-grade security and reliability.

## Key Features

### Security & Compliance
- **Security-First Design**: Built with minimal attack surfaces and security hardening
- **Enterprise Compliance**: Meets industry standards including FIPS, STIG, and CIS benchmarks
- **Regular Updates**: Automated security patches and vulnerability management
- **Production Ready**: Optimized for enterprise deployment and scaling

### Technical Capabilities
- **Multi-Architecture Support**: Available for AMD64 and ARM64 architectures
- **SSL/TLS Encryption**: Powered by OpenSSL library for robust encryption
- **Flexible Deployment**: Supports both server and client modes
- **Comprehensive Documentation**: Detailed guides and best practices

## Use Cases

- Add SSL/TLS encryption to legacy applications without code modifications
- Secure database connections (Redis, PostgreSQL, MySQL)
- Encrypt network services that don't natively support SSL
- Create secure tunnels between microservices
- Protect internal communications in distributed systems
- Enable compliance with encryption requirements

## Image Details

- **Base Image**: CleanStart security-hardened base image
- **Image Name**: `ghcr.io/cleanstart-containers/stunnel:latest-dev`
- **Registry**: `{registry.example.com}/stunnel`
- **Key Components**: Stunnel, OpenSSL library
- **Tags Available**: `latest`, `latest-dev`

## Quick Start

### Pull Commands
```bash
# Production image
docker pull ghcr.io/cleanstart-containers/stunnel:latest

# Development image
docker pull ghcr.io/cleanstart-containers/stunnel:latest-dev
```

### Run Commands
```bash
# Production deployment with security hardening
docker run -d --name stunnel-prod \
  --read-only \
  --security-opt=no-new-privileges \
  --user 1000:1000 \
  -v /path/to/stunnel.conf:/etc/stunnel/certs.pem/stunnel.conf:ro \
  -v /path/to/certs:/etc/stunnel/certs:ro \
  ghcr.io/cleanstart-containers/stunnel:latest
```

```bash
# Development/testing
docker run -it --name stunnel-test
   -v /path/to/stunnel.conf:/etc/stunnel/certs.pem/stunnel.conf:ro
   ghcr.io/cleanstart-containers/stunnel:latest-dev
```

## Architecture Support

CleanStart Stunnel images support multiple architectures to ensure compatibility across different deployment environments:

- **AMD64**: Intel and AMD x86-64 processors
- **ARM64**: ARM-based processors including Apple Silicon and ARM servers

### Architecture-specific Pull Commands
```bash
# AMD64
docker pull --platform linux/amd64 ghcr.io/cleanstart-containers/stunnel:latest

# ARM64
docker pull --platform linux/arm64 ghcr.io/cleanstart-containers/stunnel:latest
```

## Directory Structure
```
stunnel/
├── kubernetes - AWS/       # Kubernetes deployment manifests for AWS EKS
├── sample-project/         # Docker-based sample project with Redis example
└── README.md              # This file
```

## Documentation & Examples

### Quick Links

- **[Sample Project](sample-project/)** - Docker-based examples with configuration files
- **[Kubernetes Deployment](kubernetes%20-%20AWS/)** - Deploy stunnel on AWS EKS with Redis example

### Detailed Documentation

For detailed deployment instructions and examples, refer to:

- [Sample Project README](sample-project/README.md) - Docker-based setup and configuration examples
- [Kubernetes README](kubernetes%20-%20AWS/README.md) - Kubernetes deployment guides for AWS EKS

## Requirements

### Prerequisites

- Docker or container runtime environment
- SSL/TLS certificates (self-signed or CA-signed)
- Configuration file defining connection endpoints
- Backend service to encrypt/decrypt traffic for

### Configuration

Stunnel requires a configuration file that defines:
- Service endpoints (accept/connect)
- SSL/TLS certificate paths
- Encryption protocols and ciphers
- Connection modes (client/server)

Example configuration structure available in the sample-project directory.

## Resources

### Official Links

- **Official Documentation**: https://example.com/docs/stunnel
- **Provenance / SBOM / Signature**: https://images.cleanstart.com/images/stunnel
- **CleanStart All Images**: https://images.cleanstart.com
- **CleanStart Community Images**: https://hub.docker.com/u/cleanstart
- **Docker Hub**: https://hub.docker.com/r/cleanstart/stunnel

## Vulnerability Disclaimer

CleanStart offers Docker images that include third-party open-source libraries and packages maintained by independent contributors. While CleanStart maintains these images and applies industry-standard security practices, it cannot guarantee the security or integrity of upstream components beyond its control.

Users acknowledge and agree that open-source software may contain undiscovered vulnerabilities or introduce new risks through updates. CleanStart shall not be liable for security issues originating from third-party libraries, including but not limited to zero-day exploits, supply chain attacks, or contributor-introduced risks.
