# Domain-Driven Design Analysis

## Executive Summary

[Brief overview of the domain landscape: how many bounded contexts were identified, what is the core domain, and the overall DDD maturity level (Nascent / Emerging / Established)]

## Subdomain Classification

| Subdomain | Type                        | Description                              | Key Modules/Packages |
| --------- | --------------------------- | ---------------------------------------- | -------------------- |
| [Name]    | Core / Supporting / Generic | [What business capability it represents] | [Paths]              |

## Context Map

[ASCII art diagram showing Bounded Contexts and their relationships]

```
┌─────────────────┐                                ┌─────────────────┐
│   Context A     │   Shared Kernel / ACL /        │   Context B     │
│                 │   Conformist / OHS             │                 │
│  ┌───────────┐  │ ─────────────────────────────► │  ┌───────────┐  │
│  │ Module 1  │  │                                │  │ Module 2  │  │
│  └───────────┘  │                                │  └───────────┘  │
└─────────────────┘                                └─────────────────┘
```

### Context Relationships

| Upstream    | Downstream  | Relationship Pattern                                          | Description                                |
| ----------- | ----------- | ------------------------------------------------------------- | ------------------------------------------ |
| [Context A] | [Context B] | [Shared Kernel / ACL / Conformist / OHS / Published Language] | [How the boundary is enforced or violated] |

## Strategic Design

[Analysis of the current strategic architecture: are boundaries clearly defined? Where are they violated? What should change?]

### Boundary Violations

- [Specific violation with file paths and explanation]

## Tactical Design

### Aggregate Inventory

| Aggregate Root | Bounded Context | Invariants                   | Value Objects     | Referenced Aggregates (by ID?) | Key Files |
| -------------- | --------------- | ---------------------------- | ----------------- | ------------------------------ | --------- |
| [Entity Name]  | [Context]       | [Business rules it enforces] | [VOs it contains] | [Yes/No + which]               | [Paths]   |

### Entity vs Value Object Assessment

- [Concept currently modeled as Entity that should be a Value Object, or vice versa, with reasoning]

### Domain Events Catalog

| Event Name         | Producer (Aggregate) | Consumers                 | Trigger Condition         | Payload (Key Fields)    | Currently Implemented? |
| ------------------ | -------------------- | ------------------------- | ------------------------- | ----------------------- | ---------------------- |
| [e.g. OrderPlaced] | [Order]              | [Inventory, Notification] | [When order is confirmed] | [orderId, items, total] | [Yes / No — suggested] |

### Domain Services

| Service | Stateless? | Purpose        | Should It Exist?                          |
| ------- | ---------- | -------------- | ----------------------------------------- |
| [Name]  | [Yes/No]   | [What it does] | [Yes / Move to Aggregate / Merge with...] |

## Anti-Corruption Layers

| External System / Context | Current Integration           | ACL Present? | Recommendation                      |
| ------------------------- | ----------------------------- | ------------ | ----------------------------------- |
| [e.g. Payment Gateway]    | [Direct API call from domain] | [No]         | [Introduce ACL adapter at boundary] |

## Ubiquitous Language Assessment

[Cross-reference with the Dictionary lens output if available]

### Naming Inconsistencies

| Term in Code | Expected Domain Term | Location    | Suggested Rename |
| ------------ | -------------------- | ----------- | ---------------- |
| [e.g. `usr`] | [User / Customer]    | [File path] | [`customer`]     |

## Refactoring Roadmap

### Phase 1: Quick Wins

- [Low-effort, high-impact DDD alignment changes]

### Phase 2: Structural Refactoring

- [Bounded Context extraction, Aggregate redesign]

### Phase 3: Strategic Evolution

- [Event-driven architecture, CQRS introduction, etc.]
