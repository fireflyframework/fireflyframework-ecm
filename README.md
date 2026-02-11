# Firefly Framework - Enterprise Content Management (ECM)

[![CI](https://github.com/fireflyframework/fireflyframework-ecm/actions/workflows/ci.yml/badge.svg)](https://github.com/fireflyframework/fireflyframework-ecm/actions/workflows/ci.yml)
[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](LICENSE)
[![Java](https://img.shields.io/badge/Java-21%2B-orange.svg)](https://openjdk.org)
[![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.x-green.svg)](https://spring.io/projects/spring-boot)

> ECM core library providing document management, e-signature, intelligent document processing, and folder security through a port/adapter architecture.

---

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Requirements](#requirements)
- [Installation](#installation)
- [Quick Start](#quick-start)
- [Configuration](#configuration)
- [Documentation](#documentation)
- [Contributing](#contributing)
- [License](#license)

## Overview

Firefly Framework ECM provides Enterprise Content Management capabilities through a hexagonal (port/adapter) architecture. It defines ports for document management, e-signature workflows, intelligent document processing (IDP), folder management, audit trails, and document security, which are implemented by provider-specific adapter modules.

The core module includes the adapter registry and selection mechanism, enabling runtime adapter discovery and multi-provider support. It provides domain models for documents, signature envelopes, folders, permissions, and audit events, along with comprehensive enumerations for document statuses, signature states, and processing workflows.

Storage adapters (AWS S3, Azure Blob) and e-signature adapters (Adobe Sign, DocuSign, Logalty) are published as separate standalone modules that plug into the ECM core.

## Features

- Hexagonal architecture with port/adapter pattern
- Document management ports: content, metadata, versioning, search
- E-signature ports: envelope management, signature requests, validation, proof
- Intelligent document processing ports: classification, extraction, validation
- Folder management with hierarchical structure and permissions
- Audit trail with event type and severity tracking
- Adapter registry with profile-based selection
- NoOp adapters for testing and development
- Local document search and permission adapters
- Resilience configuration for adapter operations
- Auto-configuration via `EcmAutoConfiguration`
- Configurable via `EcmProperties`

## Requirements

- Java 21+
- Spring Boot 3.x
- Maven 3.9+

## Installation

```xml
<dependency>
    <groupId>org.fireflyframework</groupId>
    <artifactId>fireflyframework-ecm</artifactId>
    <version>26.01.01</version>
</dependency>
```

## Quick Start

```java
import org.fireflyframework.ecm.port.document.DocumentContentPort;
import org.fireflyframework.ecm.port.esignature.SignatureEnvelopePort;

@Service
public class DocumentService {

    private final DocumentContentPort documentPort;
    private final SignatureEnvelopePort signaturePort;

    public Mono<Document> uploadAndSign(byte[] content, SignatureRequest sigRequest) {
        return documentPort.store(content)
            .flatMap(doc -> signaturePort.createEnvelope(doc, sigRequest));
    }
}
```

## Configuration

```yaml
firefly:
  ecm:
    storage:
      provider: aws-s3  # aws-s3, azure-blob
    esignature:
      provider: docusign  # adobe-sign, docusign, logalty
```

## Documentation

Additional documentation is available in the [docs/](docs/) directory:

- [Architecture](docs/architecture.md)
- [Configuration](docs/configuration.md)
- [Configuration Reference](docs/configuration-reference.md)
- [Testing](docs/testing.md)

## Contributing

Contributions are welcome. Please read the [CONTRIBUTING.md](CONTRIBUTING.md) guide for details on our code of conduct, development process, and how to submit pull requests.

## License

Copyright 2024-2026 Firefly Software Solutions Inc.

Licensed under the Apache License, Version 2.0. See [LICENSE](LICENSE) for details.
