# AxiomID Technology Stack

**Status:** Proposed  
**Version:** 0.1.0  
**Date:** 2026-08-07

## 1. Purpose

This document records the initial technology choices for AxiomID.

Technology decisions are treated as engineering decisions rather than implementation preferences. Each choice should support the platform's functional requirements, security requirements, maintainability, scalability, and ability to demonstrate production-grade engineering practices.

---

## 2. Platform Architecture

AxiomID will initially follow a modular service-oriented architecture.

The system will be designed around clear boundaries between:

- Identity
- Authentication
- Authorization
- Tenant management
- Client/application management
- Token/session management
- Audit
- Administrative operations

The architecture should allow individual components to evolve without unnecessarily coupling unrelated domains.

---

## 3. Backend

**Primary language:** TypeScript

**Runtime:** Node.js

**Backend framework:** NestJS

### Rationale

TypeScript provides:

- Static typing
- Strong tooling
- Maintainable large-scale codebases
- Good ecosystem support
- Familiarity with modern backend development

NestJS provides:

- Modular architecture
- Dependency injection
- Clear application boundaries
- First-class TypeScript support
- Patterns suitable for enterprise backend systems

---

## 4. API

**Primary API style:** REST

**API format:** JSON

The API will follow explicit resource-oriented contracts.

API design will include:

- Versioning
- Authentication requirements
- Authorization requirements
- Validation
- Consistent error responses
- Request correlation
- Pagination where appropriate
- Idempotency where required

---

## 5. Database

**Primary database:** PostgreSQL

PostgreSQL will be used for durable transactional data.

Initial domain data is expected to include:

- Tenants
- Users
- Applications/clients
- Roles
- Permissions
- Sessions
- Refresh tokens
- Audit records

The final schema will be established during domain and data-model design.

---

## 6. Caching and Ephemeral Data

**Technology:** Redis

Redis may be used for:

- Short-lived authentication state
- Rate limiting
- Session-related ephemeral state
- Distributed coordination where required

Redis will not be treated as the system of record for durable identity data.

---

## 7. Authentication

AxiomID will support modern authentication mechanisms appropriate for B2B SaaS applications.

Initial design areas include:

- Password-based authentication
- Secure password hashing
- Session management
- Refresh-token rotation
- Multi-factor authentication as a future capability
- OAuth 2.0 / OpenID Connect integration as the platform evolves

Authentication and authorization will remain separate concerns.

---

## 8. Authorization

Authorization will be designed as a first-class platform capability.

The initial authorization model will support:

- Roles
- Permissions
- Role-to-permission relationships
- Tenant-aware authorization
- Resource-level authorization where required

The authorization model should be extensible toward more sophisticated policy-based authorization.

---

## 9. Security

Security is a foundational architectural concern.

The system will incorporate:

- Secure credential storage
- Input validation
- Authentication controls
- Authorization enforcement
- Rate limiting
- Audit logging
- Secure secret handling
- Security headers
- Dependency management
- Automated security checks
- Least-privilege principles

Secrets must never be committed to source control.

---

## 10. Testing

The project will use multiple levels of testing.

Expected testing layers include:

- Unit tests
- Integration tests
- API tests
- Security-focused tests
- End-to-end tests

Testing strategy will be defined more precisely during implementation planning.

---

## 11. CI/CD

GitHub Actions will initially provide continuous integration.

The CI pipeline will progressively include:

1. Dependency installation
2. Formatting checks
3. Static analysis
4. Type checking
5. Unit tests
6. Integration tests
7. Security checks
8. Build verification

Deployment automation will be introduced after the application architecture and deployment model have been established.

---

## 12. Documentation

Engineering documentation will remain version-controlled alongside the system.

Documentation will include:

- Product requirements
- Architecture Decision Records
- Architecture diagrams
- API contracts
- Domain models
- Security decisions
- Operational documentation

---

## 13. Design Principles

AxiomID development should follow these principles:

- Security by design
- Explicit boundaries
- Least privilege
- Defense in depth
- Separation of concerns
- Fail securely
- Observable systems
- Testable components
- Maintainable code
- Documented architectural decisions
- Backward-compatible evolution where practical

---

## 14. Decision Status

These technology choices establish the initial engineering baseline.

They may be revised through documented Architecture Decision Records when new evidence or requirements justify a change.
