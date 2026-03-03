---
date: '{{date}}'
project: '{{project_name}}'
driftScore: 0
criticalCount: 0
warningCount: 0
infoCount: 0
---

# Spec-Code Drift Report — {{project_name}}

**Date:** {{date}}
**Author:** {{user_name}}

---

## Summary

- **Overall Drift Score:** {{driftScore}}/100 (0 = perfectly aligned, 100 = completely drifted)
- **Critical Drifts:** {{criticalCount}}
- **Warning Drifts:** {{warningCount}}
- **Info Items:** {{infoCount}}

---

## Architecture Drift

| # | Spec Claim | Actual State | Severity | Proposed Update |
|---|-----------|-------------|----------|-----------------|

---

## Requirements Drift

| # | PRD Requirement | Implementation State | Severity | Proposed Update |
|---|----------------|---------------------|----------|-----------------|

---

## Epic/Story Drift

| # | Story | Spec State | Code State | Severity | Proposed Update |
|---|-------|-----------|------------|----------|-----------------|

---

## Recommended Actions

<!-- Ordered by severity: critical first, then warning, then info -->

1. **CRITICAL:**
2. **WARNING:**
3. **INFO:**

---

## Next Steps

<!-- Suggested workflows to run based on drift findings -->
