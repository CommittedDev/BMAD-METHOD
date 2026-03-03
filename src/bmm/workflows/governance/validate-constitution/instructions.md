<workflow>

<step n="1" goal="Load constitution and validation checklist">
  <action>Load the current constitution from {governance_artifacts}/constitution.md</action>
  <check if="no constitution found">
    <action>Inform user: No constitution found. Use [GI] Governance Init to create one first.</action>
    <action>Exit workflow</action>
  </check>
  <action>Load the validation checklist from {installed_path}/checklist.md</action>
  <action>Load architecture and PRD documents for cross-reference validation</action>
</step>

<step n="2" goal="Structural Validation - verify all required sections are present and well-formed">
  <action>Check each required section exists and has meaningful content (not just placeholder comments):</action>
  <action>- Section 1: Organizational Directives (1.1-1.4)</action>
  <action>- Section 2: Project-Level Directives (2.1-2.4)</action>
  <action>- Section 3: Quality Gate Definitions (3.1-3.3)</action>
  <action>- Section 4: Compliance Requirements (4.1-4.2)</action>
  <action>- Section 5: Evolution History</action>
  <action>Flag any missing or empty sections as findings</action>
</step>

<step n="3" goal="Consistency Validation - check for internal policy conflicts">
  <action>Analyze all policies across layers for contradictions:</action>
  <action>- Org-level vs project-level conflicts (project can be MORE restrictive but not LESS)</action>
  <action>- Quality gate thresholds that conflict with stated testing requirements</action>
  <action>- Security policies that conflict with technology constraints</action>
  <action>- SYNC vs ASYNC gate definitions that overlap or leave gaps</action>
  <action>Flag any conflicts as findings with suggested resolutions</action>
</step>

<step n="4" goal="Alignment Validation - cross-reference with architecture and PRD">
  <check if="architecture document is available">
    <action>Verify technology constraints match architecture technology choices</action>
    <action>Verify architecture boundaries align with stated patterns</action>
    <action>Verify security architecture aligns with security policies</action>
  </check>
  <check if="PRD is available">
    <action>Verify testing requirements cover PRD acceptance criteria</action>
    <action>Verify compliance requirements cover PRD regulatory mentions</action>
  </check>
  <action>Flag any misalignments as findings</action>
</step>

<step n="5" goal="Report validation results">
  <action>Present validation report organized by severity:</action>
  <action>- CRITICAL: Missing required sections, policy conflicts, security gaps</action>
  <action>- WARNING: Weak coverage, potential misalignments, incomplete areas</action>
  <action>- INFO: Suggestions for improvement, best practice recommendations</action>
  <action>Provide overall constitution health score (percentage of checklist items passing)</action>
  <action>Suggest next steps: [GE] to evolve and fix issues, or [GQ] to adjust quality gates</action>
</step>

</workflow>
