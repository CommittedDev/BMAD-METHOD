# Governance Standards Reference

## Constitution Structure

A well-formed constitution follows this hierarchy:

1. **Organizational Directives** - Company-wide policies that apply to all projects
2. **Team Directives** - Team-level policies and conventions
3. **Project Directives** - Project-specific constraints and requirements
4. **Quality Gate Definitions** - Measurable thresholds for SYNC and ASYNC modes
5. **Compliance Requirements** - Regulatory framework mappings
6. **Evolution History** - Versioned log of all changes with rationale

## Policy Categories

- **Security**: Authentication, authorization, data encryption, secrets management
- **Coding Standards**: Language conventions, patterns, testing requirements, documentation
- **Architecture Boundaries**: Approved technologies, forbidden patterns, integration constraints
- **Data Governance**: PII handling, retention policies, access controls
- **Deployment**: Environment policies, rollback procedures, approval chains
- **Documentation**: Required artifacts, update cadence, review processes

## Quality Gate Framework

### SYNC Mode (Human-Reviewed)
- Every workflow step requires explicit human approval
- Higher quality thresholds (default: 80%)
- Micro-review at each checkpoint
- Full audit trail of human decisions

### ASYNC Mode (Agent-Delegated)
- Agent proceeds autonomously through workflow
- Lower quality thresholds (default: 60%)
- Macro-review at workflow completion
- Delegation context captured for audit

## Compliance Framework Essentials

### SOC 2 Type II
- Control Environment (CC1)
- Information and Communication (CC2)
- Risk Assessment (CC3)
- Monitoring Activities (CC4)
- Logical and Physical Access (CC6)

### HIPAA
- Administrative Safeguards (§164.308)
- Physical Safeguards (§164.310)
- Technical Safeguards (§164.312)
- Breach Notification (§164.400)

### ISO 27001
- Context of the Organization (Clause 4)
- Leadership (Clause 5)
- Planning (Clause 6)
- Operation (Clause 8)
- Performance Evaluation (Clause 9)

### GDPR
- Data Processing Principles (Article 5)
- Lawful Basis (Article 6)
- Data Subject Rights (Articles 12-23)
- Data Protection by Design (Article 25)
- Data Protection Impact Assessment (Article 35)

## Evolution Log Format

Each evolution entry must contain:
- **Version**: Incremental version number
- **Date**: When the change was made
- **Author**: Who proposed the change
- **Category**: Which section was modified
- **Change Summary**: What was changed and why
- **Impact Assessment**: What workflows or processes are affected
