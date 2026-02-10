# Firefly ECM Library

[![CI](https://github.com/fireflyframework/fireflyframework-ecm/actions/workflows/ci.yml/badge.svg)](https://github.com/fireflyframework/fireflyframework-ecm/actions/workflows/ci.yml)

> **Enterprise Content Management Port Interfaces for the Modern Era**

A comprehensive, production-ready Enterprise Content Management (ECM) **port interface library** built on hexagonal architecture principles. This library provides the **core port interfaces** (business contracts) for document management, digital signatures, and intelligent document processing. Adapter implementations are provided in separate libraries, allowing you to choose and integrate only the providers you need.

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![Java](https://img.shields.io/badge/Java-21+-orange.svg)](https://openjdk.java.net/)
[![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.0+-green.svg)](https://spring.io/projects/spring-boot)

## 🎯 Purpose & Vision

The Firefly ECM Library solves the challenge of **vendor lock-in** and **integration complexity** in enterprise content management by providing a **stable, vendor-agnostic interface layer**. This library contains:

- **Port Interfaces**: Business contracts defining ECM operations (document management, eSignatures, IDP)
- **Domain Models**: Core entities and value objects for ECM operations
- **Adapter Infrastructure**: Framework for registering and selecting adapter implementations
- **Auto-Configuration**: Spring Boot auto-configuration for seamless integration

Organizations can:

- **Switch between storage providers** without changing business logic
- **Integrate multiple eSignature providers** through a unified API
- **Process documents intelligently** with various IDP providers
- **Scale horizontally** with cloud-native, reactive architecture
- **Maintain compliance** with built-in audit trails and security features
- **Future-proof applications** with a stable, vendor-agnostic interface

**Adapter implementations** are provided in separate libraries (see [Available Adapters](#-available-adapters) below).

## 🏗️ Architecture Overview

This library implements **Hexagonal Architecture** (Ports and Adapters pattern), providing clean separation between business logic and external systems.

**Key Benefits**: Pluggable adapters, testable design, scalable architecture, reactive programming, vendor independence

### Library Structure

This is a **single-module library** containing:

```
fireflyframework-ecm/                         # Port Interfaces Library
├── src/main/java/
│   └── org.fireflyframework.ecm/
│       ├── port/                # Port Interfaces (business contracts)
│       │   ├── document/        # Document management ports
│       │   ├── folder/          # Folder management ports
│       │   ├── security/        # Security and permissions ports
│       │   ├── audit/           # Audit and compliance ports
│       │   ├── esignature/      # Digital signature ports
│       │   └── idp/             # Intelligent Document Processing ports
│       ├── domain/              # Domain Models and DTOs
│       ├── adapter/             # Adapter infrastructure (registry, selector)
│       ├── config/              # Spring Boot auto-configuration
│       └── service/             # Core services (EcmPortProvider)
└── pom.xml
```

### Adapter Libraries (Separate Repositories)

Adapter implementations are provided in separate libraries that you add as dependencies:

```
Document Storage Adapters:
├── fireflyframework-ecm-adapter-s3           # Amazon S3 adapter
├── fireflyframework-ecm-adapter-azure-blob   # Azure Blob Storage adapter
├── fireflyframework-ecm-adapter-minio        # MinIO adapter
└── fireflyframework-ecm-adapter-alfresco     # Alfresco Content Services adapter

eSignature Adapters:
├── fireflyframework-ecm-adapter-docusign     # DocuSign adapter
├── fireflyframework-ecm-adapter-adobe-sign   # Adobe Sign adapter
└── fireflyframework-ecm-adapter-logalty      # Logalty adapter (eIDAS-compliant)

IDP Adapters:
├── fireflyframework-ecm-adapter-aws-textract      # AWS Textract adapter
├── fireflyframework-ecm-adapter-azure-form-recognizer  # Azure Form Recognizer adapter
└── fireflyframework-ecm-adapter-google-document-ai     # Google Document AI adapter
```

## 🚀 What's Included in This Library

### ✅ Port Interfaces (Business Contracts)

This library provides **complete port interface definitions** for:

#### **Document Management Ports**
- ✅ **DocumentPort**: Document CRUD operations (create, read, update, delete)
- ✅ **DocumentContentPort**: Binary content storage and streaming
- ✅ **DocumentVersionPort**: Version management and history
- ✅ **DocumentSearchPort**: Search and query capabilities

#### **Folder Management Ports**
- ✅ **FolderPort**: Folder CRUD and organization
- ✅ **FolderHierarchyPort**: Hierarchical folder operations

#### **Security & Permissions Ports**
- ✅ **PermissionPort**: Access control and permissions
- ✅ **DocumentSecurityPort**: Document-level security operations

#### **Audit & Compliance Ports**
- ✅ **AuditPort**: Audit logging and compliance tracking

#### **eSignature Ports**
- ✅ **SignatureEnvelopePort**: Envelope lifecycle management
- ✅ **SignatureRequestPort**: Signature request operations
- ✅ **SignatureValidationPort**: Signature verification
- ✅ **SignatureProofPort**: Signature proof and evidence

#### **Intelligent Document Processing (IDP) Ports**
- ✅ **DocumentExtractionPort**: OCR and text extraction
- ✅ **DocumentClassificationPort**: Document type classification
- ✅ **DataExtractionPort**: Structured data extraction
- ✅ **DocumentValidationPort**: Document validation and quality checks

### ✅ Core Infrastructure

- ✅ **Domain Models**: Complete entity definitions with validation
- ✅ **Adapter Infrastructure**: Registry, selector, and validation framework
- ✅ **Auto-Configuration**: Spring Boot auto-configuration
- ✅ **Reactive Support**: Full Project Reactor integration
- ✅ **Graceful Degradation**: No-op adapters for missing implementations
- ✅ **Comprehensive Javadoc**: Fully documented APIs

### 🧪 Test Coverage

| **Component** | **Tests** | **Success Rate** | **Status** |
|---------------|-----------|------------------|------------|
| **Core Library** | 11 | ✅ **100%** | Production Ready |
| **Port Interfaces** | - | ✅ **Complete** | All defined |
| **Domain Models** | - | ✅ **Complete** | Fully validated |

## 📦 Available Adapters

Adapter implementations are provided in **separate libraries**. Add the adapters you need as Maven dependencies:

### Document Storage Adapters

| Adapter | Artifact ID | Status | Repository |
|---------|-------------|--------|------------|
| **Amazon S3** | `fireflyframework-ecm-adapter-s3` | ✅ Available | [firefly-oss/fireflyframework-ecm-adapter-s3](https://github.org/fireflyframework-oss/fireflyframework-ecm-adapter-s3) |
| **Azure Blob** | `fireflyframework-ecm-adapter-azure-blob` | ✅ Available | [firefly-oss/fireflyframework-ecm-adapter-azure-blob](https://github.org/fireflyframework-oss/fireflyframework-ecm-adapter-azure-blob) |
| **MinIO** | `fireflyframework-ecm-adapter-minio` | 🔜 Planned | - |
| **Alfresco** | `fireflyframework-ecm-adapter-alfresco` | 🔜 Planned | - |

### eSignature Adapters

| Adapter | Artifact ID | Status | Repository |
|---------|-------------|--------|------------|
| **DocuSign** | `fireflyframework-ecm-adapter-docusign` | ✅ Available | [firefly-oss/fireflyframework-ecm-adapter-docusign](https://github.org/fireflyframework-oss/fireflyframework-ecm-adapter-docusign) |
| **Adobe Sign** | `fireflyframework-ecm-adapter-adobe-sign` | ✅ Available | [firefly-oss/fireflyframework-ecm-adapter-adobe-sign](https://github.org/fireflyframework-oss/fireflyframework-ecm-adapter-adobe-sign) |
| **Logalty** | `fireflyframework-ecm-adapter-logalty` | 🔜 Planned | - |

### IDP Adapters

| Adapter | Artifact ID | Status | Repository |
|---------|-------------|--------|------------|
| **AWS Textract** | `fireflyframework-ecm-adapter-aws-textract` | 🔜 Planned | - |
| **Azure Form Recognizer** | `fireflyframework-ecm-adapter-azure-form-recognizer` | 🔜 Planned | - |
| **Google Document AI** | `fireflyframework-ecm-adapter-google-document-ai` | 🔜 Planned | - |

> **Legend:** ✅ = Available | 🔜 = Planned

## 🚀 Quick Start

### 1. Add Dependencies

Add the **core library** (port interfaces) and your chosen **adapter libraries** to your Spring Boot project:

```xml
<!-- Core ECM Library (Port Interfaces) - REQUIRED -->
<dependency>
    <groupId>org.fireflyframework</groupId>
    <artifactId>fireflyframework-ecm</artifactId>
    <version>1.0.0-SNAPSHOT</version>
</dependency>

<!-- Add adapter implementations as needed -->

<!-- Amazon S3 Adapter (optional) -->
<dependency>
    <groupId>org.fireflyframework</groupId>
    <artifactId>fireflyframework-ecm-adapter-s3</artifactId>
    <version>1.0.0-SNAPSHOT</version>
</dependency>

<!-- DocuSign Adapter (optional) -->
<dependency>
    <groupId>org.fireflyframework</groupId>
    <artifactId>fireflyframework-ecm-adapter-docusign</artifactId>
    <version>1.0.0-SNAPSHOT</version>
</dependency>

<!-- Azure Blob Storage Adapter (optional) -->
<dependency>
    <groupId>org.fireflyframework</groupId>
    <artifactId>fireflyframework-ecm-adapter-azure-blob</artifactId>
    <version>1.0.0-SNAPSHOT</version>
</dependency>
```

### 2. Configure Your Adapters

Configure the adapters you've added via `application.yml`:

#### Example: S3 + DocuSign Configuration

```yaml
firefly:
  ecm:
    # Select document storage adapter
    adapter-type: s3

    # Select eSignature provider
    esignature:
      provider: docusign

# S3 adapter configuration
firefly:
  ecm:
    adapter:
      s3:
        bucket-name: ${S3_BUCKET_NAME}
        region: ${AWS_REGION}
        access-key: ${AWS_ACCESS_KEY_ID}
        secret-key: ${AWS_SECRET_ACCESS_KEY}

# DocuSign adapter configuration
firefly:
  ecm:
    adapter:
      docusign:
        integration-key: ${DOCUSIGN_INTEGRATION_KEY}
        user-id: ${DOCUSIGN_USER_ID}
        account-id: ${DOCUSIGN_ACCOUNT_ID}
        private-key: ${DOCUSIGN_PRIVATE_KEY}
```

### 3. Use Port Interfaces in Your Application

Inject and use the port interfaces - the framework automatically provides the configured adapter implementation:

```java
@Service
@RequiredArgsConstructor
public class DocumentService {

    private final EcmPortProvider portProvider;

    public Mono<Document> uploadDocument(String name, byte[] content) {
        // Get the configured DocumentPort implementation
        DocumentPort documentPort = portProvider.getDocumentPort()
            .orElseThrow(() -> new IllegalStateException("No document adapter configured"));

        Document document = Document.builder()
            .name(name)
            .mimeType("application/pdf")
            .size((long) content.length)
            .build();

        return documentPort.createDocument(document, content);
    }

    public Mono<SignatureEnvelope> sendForSignature(UUID documentId, List<String> signers) {
        // Get the configured SignatureEnvelopePort implementation
        SignatureEnvelopePort signaturePort = portProvider.getSignatureEnvelopePort()
            .orElseThrow(() -> new IllegalStateException("No eSignature adapter configured"));

        // Create and send envelope
        SignatureEnvelope envelope = SignatureEnvelope.builder()
            .documentId(documentId)
            .signers(signers)
            .build();

        return signaturePort.createEnvelope(envelope)
            .flatMap(signaturePort::sendEnvelope);
    }
}
```

## 📋 Port Interface Capabilities

This library defines port interfaces for the following ECM capabilities. Actual functionality depends on the adapter implementations you choose:

### Document Management Ports
- **DocumentPort**: Create, read, update, delete documents
- **DocumentContentPort**: Binary content storage with streaming support
- **DocumentVersionPort**: Complete document version history
- **DocumentSearchPort**: Full-text and metadata search capabilities

### Folder Management Ports
- **FolderPort**: Folder CRUD operations
- **FolderHierarchyPort**: Nested folder organization and path management

### Security & Permissions Ports
- **PermissionPort**: Fine-grained access control (read, write, delete, share)
- **DocumentSecurityPort**: Document encryption and security operations

### Digital Signature Ports
- **SignatureEnvelopePort**: Envelope lifecycle management
- **SignatureRequestPort**: Signature request operations
- **SignatureValidationPort**: Signature verification and validation
- **SignatureProofPort**: Signature proof and audit trails

### Intelligent Document Processing (IDP) Ports
- **DocumentExtractionPort**: OCR and text extraction
- **DocumentClassificationPort**: Automatic document type detection
- **DataExtractionPort**: Forms, tables, key-value pairs extraction
- **DocumentValidationPort**: Business rules and quality checks

### Audit & Compliance Ports
- **AuditPort**: Complete audit trail for all operations
- **Compliance tracking**: Regulatory compliance and reporting

> **Note**: Port interfaces define the contracts. Actual features depend on the adapter implementations you add to your project.

## 🔧 Adapter Integration Guides

Detailed guides for integrating adapter libraries are available in the [docs/guides](docs/guides) directory:

**Document Storage Adapters:**
- **[Amazon S3 Integration](docs/guides/s3-integration.md)** - How to add and configure the S3 adapter
- **[Azure Blob Storage](docs/guides/azure-integration.md)** - How to add and configure the Azure Blob adapter
- **[MinIO Integration](docs/guides/minio-integration.md)** - How to add and configure the MinIO adapter (planned)
- **[Alfresco Integration](docs/guides/alfresco-integration.md)** - How to add and configure the Alfresco adapter (planned)

**eSignature Adapters:**
- **[DocuSign Integration](docs/guides/docusign-integration.md)** - How to add and configure the DocuSign adapter

**IDP Adapters (Planned):**
- **[AWS Textract Integration](docs/idp/aws-textract-integration.md)** - AWS Textract adapter integration
- **[Azure Form Recognizer Integration](docs/idp/azure-form-recognizer-integration.md)** - Azure Form Recognizer adapter integration
- **[Google Document AI Integration](docs/idp/google-document-ai-integration.md)** - Google Document AI adapter integration

## 📚 Documentation

### Core Library Documentation
- **[Architecture Guide](docs/architecture.md)** - Hexagonal architecture and design principles
- **[Configuration Reference](docs/configuration.md)** - Configuration options and properties
- **[API Reference](docs/api/)** - Port interface documentation

### Adapter Integration Guides
- **[S3 Adapter Guide](docs/guides/s3-integration.md)** - Amazon S3 adapter integration
- **[Azure Blob Adapter Guide](docs/guides/azure-integration.md)** - Azure Blob Storage adapter integration
- **[DocuSign Adapter Guide](docs/guides/docusign-integration.md)** - DocuSign adapter integration
- **[Alfresco Adapter Guide](docs/guides/alfresco-integration.md)** - Alfresco adapter integration (planned)
- **[MinIO Adapter Guide](docs/guides/minio-integration.md)** - MinIO adapter integration (planned)

### IDP Adapter Guides
- **[IDP Overview](docs/idp/)** - Intelligent Document Processing overview
- **[AWS Textract](docs/idp/aws-textract-integration.md)** - AWS Textract adapter (planned)
- **[Azure Form Recognizer](docs/idp/azure-form-recognizer-integration.md)** - Azure Form Recognizer adapter (planned)
- **[Google Document AI](docs/idp/google-document-ai-integration.md)** - Google Document AI adapter (planned)

### Development
- **[Examples](docs/examples/)** - Working code examples
- **[Testing Guide](docs/testing.md)** - Testing strategies and examples

## 🤝 Contributing

We welcome contributions to the Firefly ECM Library!

### Contributing to Core Library (Port Interfaces)
- New port interface definitions
- Domain model enhancements
- Infrastructure improvements
- Documentation updates

### Contributing Adapter Implementations
Adapter implementations are in separate repositories. See the [Available Adapters](#-available-adapters) section for repository links.

Please see our [Contributing Guide](CONTRIBUTING.md) for details on:
- Code style and conventions
- Testing requirements
- Pull request process
- Issue reporting

## 📄 License

Licensed under the Apache License, Version 2.0. See [LICENSE](LICENSE) for details.

## 🆘 Support

- **Documentation**: [Firefly ECM Wiki](https://github.org/fireflyframework-oss/fireflyframework-ecm/wiki)
- **Issues**: [GitHub Issues](https://github.org/fireflyframework-oss/fireflyframework-ecm/issues)
- **Discussions**: [GitHub Discussions](https://github.org/fireflyframework-oss/fireflyframework-ecm/discussions)
- **Enterprise Support**: Contact [support@getfirefly.io](mailto:support@firefly-oss.org)

---

**Built with ❤️ by the Firefly OpenCore Platform Team**
