# AxiomID Domain Model

**Status:** Proposed  
**Version:** 0.2.0  
**Date:** 2026-08-09

---

## 1. Purpose

This document defines the initial domain model for AxiomID.

The domain model establishes the core business concepts, their relationships, ownership boundaries, lifecycle responsibilities, and security invariants before implementation begins.

The model is intentionally independent of database tables, ORM entities, HTTP endpoints, and framework-specific implementation details.

AxiomID is designed as a multi-tenant identity and access management platform. The domain model therefore treats tenant isolation, identity, membership, authorization, and application integration as distinct but related concerns.

---

## 2. Domain Overview

AxiomID provides identity and access management capabilities for organizations operating multiple users, applications, roles, and organizational units.

The initial domain consists of:

- Identity
- Credential
- Tenant
- Membership
- Organization
- Role
- Permission
- Application
- Session
- Refresh Token
- Audit Record

These concepts are not interchangeable.

The most important distinction is between:

- **Identity** — who an actor is
- **Tenant** — which customer security boundary the actor is operating within
- **Membership** — the actor's relationship with a tenant
- **Role** — a tenant-scoped collection of permissions
- **Permission** — an allowed capability
- **Application** — a client system integrated with AxiomID

The domain must preserve these distinctions throughout implementation.

---

## 3. Identity

An **Identity** represents an actor known to AxiomID.

An identity is intentionally independent of tenant membership.

This allows a single identity to participate in multiple tenants without duplicating the underlying identity.

For example:


                       Identity
                          │
              ┌───────────┴───────────┐
              │                       │
          Credential(s)          Membership(s)
                                      │
                         ┌────────────┴────────────┐
                         │                         │
                      Tenant A                  Tenant B
