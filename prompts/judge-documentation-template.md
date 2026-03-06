# Documentation Validation Report

## Executive Summary

**Overall Status**: [PASS / WARN / FAIL]
**Overall Score**: [X/100] (weighted average of all document scores)
**Documents Reviewed**: [N]
**Critical Issues Found**: [N]

## Document Scores

| Document           | Score (1-10) | Status                        | Key Issue                                      |
| ------------------ | ------------ | ----------------------------- | ---------------------------------------------- |
| AGENTS.md          | [X]          | [✅ Pass / ⚠️ Warn / ❌ Fail] | [One-line summary of top issue or "No issues"] |
| DDD Analysis       | [X]          | [Status]                      | [Summary]                                      |
| Dictionary         | [X]          | [Status]                      | [Summary]                                      |
| Quality Assessment | [X]          | [Status]                      | [Summary]                                      |
| Refactoring Plan   | [X]          | [Status]                      | [Summary]                                      |
| README             | [X]          | [Status]                      | [Summary]                                      |

**Scoring thresholds**: Pass ≥ 7, Warn 5-6, Fail ≤ 4

## Detailed Findings

### Hallucinations

| Severity               | Document   | Claim                 | Reality                        | Location               |
| ---------------------- | ---------- | --------------------- | ------------------------------ | ---------------------- |
| [Critical/Major/Minor] | [Doc name] | [What the doc claims] | [What the code actually shows] | [File:line or section] |

### Cross-Document Inconsistencies

| Documents         | Inconsistency      | Details                               |
| ----------------- | ------------------ | ------------------------------------- |
| [Doc A] ↔ [Doc B] | [What contradicts] | [Specific quotes from both documents] |

### Technical Inaccuracies

| Document | Section   | Issue           | Correct Information                              |
| -------- | --------- | --------------- | ------------------------------------------------ |
| [Doc]    | [Section] | [What is wrong] | [What it should say, with source file reference] |

### Completeness Gaps

| Document | Missing Section/Topic | Impact                        | Priority          |
| -------- | --------------------- | ----------------------------- | ----------------- |
| [Doc]    | [What is missing]     | [How this affects usefulness] | [High/Medium/Low] |

## Cross-Reference Verification

| Claim Category      | Verified | Unverified | Fabricated |
| ------------------- | -------- | ---------- | ---------- |
| File references     | [N]      | [N]        | [N]        |
| Technology versions | [N]      | [N]        | [N]        |
| Architecture claims | [N]      | [N]        | [N]        |
| Code patterns       | [N]      | [N]        | [N]        |
| Build commands      | [N]      | [N]        | [N]        |

## Recommendations

### Critical Fixes (must address)

1. [Specific fix with exact location and corrected content]

### Suggested Improvements (should address)

1. [Specific improvement with reasoning]

### Nice-to-Have Enhancements

1. [Optional enhancement]
