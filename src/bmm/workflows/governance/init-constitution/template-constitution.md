---
version: 1.0
lastUpdated: '{{date}}'
project: '{{project_name}}'
author: '{{user_name}}'
evolutionLog: []
complianceFrameworks: []
---

# Project Constitution — {{project_name}}

**Version:** {{version}}
**Author:** {{user_name}}
**Last Updated:** {{date}}

---

## 1. Organizational Directives

### 1.1 Team AI Directives

<!-- Organization-wide rules that ALL AI agents must follow -->

### 1.2 Coding Standards Policy

<!-- Mandatory coding conventions, languages, patterns, linting rules -->

### 1.3 Security and Privacy Policy

<!-- Authentication, authorization, encryption, secrets management, PII handling -->

### 1.4 Documentation Standards

<!-- Required documentation artifacts, update cadence, review processes -->

---

## 2. Project-Level Directives

### 2.1 Technology Constraints

<!-- Approved and forbidden technologies, version requirements -->

### 2.2 Architecture Boundaries

<!-- Architectural patterns to follow, integration constraints -->

### 2.3 Testing Requirements

<!-- Required test types, coverage targets, testing frameworks -->

### 2.4 Deployment Policies

<!-- Environment requirements, rollback procedures, approval chains -->

---

## 3. Quality Gate Definitions

### 3.1 SYNC Mode Gates (Human-Reviewed)

| Gate | Threshold | Description |
|------|-----------|-------------|
| Test Coverage | 80% | Minimum test coverage for SYNC execution |
| Code Review | Required per-step | Human reviews each workflow output |
| Documentation | Complete | All artifacts must be documented |
| Security Scan | Must pass | No critical/high vulnerabilities |

### 3.2 ASYNC Mode Gates (Agent-Delegated)

| Gate | Threshold | Description |
|------|-----------|-------------|
| Test Coverage | 60% | Minimum test coverage for ASYNC execution |
| Code Review | Consolidated | Macro-review at workflow completion |
| Documentation | Essential | Core artifacts documented |
| Security Scan | Must pass | No critical vulnerabilities |

### 3.3 Gate Override Policies

<!-- Conditions under which quality gates can be overridden, who can approve overrides -->

---

## 4. Compliance Requirements

### 4.1 Active Compliance Frameworks

<!-- List of active regulatory frameworks (SOC 2, HIPAA, ISO 27001, GDPR, etc.) -->

### 4.2 Audit Trail Requirements

<!-- What must be logged, retention periods, access controls for audit data -->

---

## 5. Evolution History

| Version | Date | Author | Category | Change Summary | Impact |
|---------|------|--------|----------|----------------|--------|
| 1.0 | {{date}} | {{user_name}} | All | Initial constitution creation | Baseline governance established |
