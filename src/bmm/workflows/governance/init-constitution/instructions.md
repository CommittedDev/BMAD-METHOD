<workflow>

<step n="1" goal="Discovery - Check existing governance state and organizational context">
  <action>Check if a constitution already exists at {governance_artifacts}/constitution.md</action>
  <check if="constitution exists">
    <action>Load existing constitution and present summary to user</action>
    <ask>A constitution already exists. Would you like to: [R] Replace it entirely, [E] Evolve it (use GE workflow instead), or [C] Cancel?</ask>
    <check if="response is E or C">
      <action>Exit workflow with appropriate guidance</action>
    </check>
  </check>
  <action>Scan for any existing governance-related files in the project (CLAUDE.md, .cursorrules, team-ai-directives, etc.)</action>
  <action>Load project context if available for understanding the project landscape</action>
  <action>Load architecture and PRD documents if available for alignment context</action>
  <action>Present discovery findings to user: what existing policies were found, what project context is available</action>
</step>

<step n="2" goal="Layer Assembly - Build the multi-layer policy structure through collaborative interview">
  <action>Load default-policies.csv for reference on standard policy categories</action>

  <template-output section="1. Organizational Directives">
    <action>Interview user about organization-wide policies:</action>
    <action>- Team AI Directives: What rules should ALL AI agents follow in your organization?</action>
    <action>- Coding Standards: What coding conventions are mandatory? (languages, patterns, linting)</action>
    <action>- Security Policy: What security requirements exist? (auth, encryption, secrets, PII handling)</action>
    <action>- Documentation Standards: What documentation is required for all projects?</action>
    <action>If existing org policies were found in discovery, incorporate and validate them</action>
    <action>Generate the Organizational Directives section</action>
  </template-output>

  <template-output section="2. Project-Level Directives">
    <action>Interview user about project-specific constraints:</action>
    <action>- Technology Constraints: What technologies are approved or forbidden?</action>
    <action>- Architecture Boundaries: What architectural patterns must be followed?</action>
    <action>- Testing Requirements: What test coverage and types are required?</action>
    <action>- Deployment Policies: What are the deployment environment requirements?</action>
    <action>If architecture and PRD documents were loaded, cross-reference for alignment</action>
    <action>Generate the Project-Level Directives section</action>
  </template-output>
</step>

<step n="3" goal="Quality Gate Configuration - Define measurable thresholds for SYNC and ASYNC modes">
  <action>Load quality-gate-defaults.csv for reference thresholds</action>

  <template-output section="3. Quality Gate Definitions">
    <action>Explain the dual execution model to the user:</action>
    <action>- SYNC Mode: Human reviews each workflow step, higher quality bar</action>
    <action>- ASYNC Mode: Agent proceeds autonomously, reviewed at completion</action>
    <action>For each quality gate category, ask user to confirm or adjust thresholds:</action>
    <action>- Test coverage thresholds (SYNC default: 80%, ASYNC default: 60%)</action>
    <action>- Code review requirements (SYNC: mandatory per-step, ASYNC: consolidated)</action>
    <action>- Documentation completeness requirements</action>
    <action>- Security scan pass requirements</action>
    <action>Generate the Quality Gate Definitions section with SYNC and ASYNC columns</action>
  </template-output>
</step>

<step n="4" goal="Compliance Mapping - Optional regulatory framework integration" optional="true">
  <ask>Does your project need to comply with regulatory frameworks? Select all that apply:
  [1] SOC 2 Type II
  [2] HIPAA
  [3] ISO 27001
  [4] GDPR
  [5] None / Skip this step</ask>

  <check if="user selected one or more frameworks">
    <action>Load the selected compliance checklist CSV files</action>
    <template-output section="4. Compliance Requirements">
      <action>For each selected framework, generate a requirements mapping:</action>
      <action>- Map framework requirements to BMAD artifacts (constitution sections, workflows, gates)</action>
      <action>- Identify which requirements are already covered by existing policies</action>
      <action>- Flag gaps that need additional policy entries</action>
      <action>- Set audit trail requirements for each framework</action>
      <action>Generate the Compliance Requirements section</action>
    </template-output>
  </check>
</step>

<step n="5" goal="Validate and Save - Structural validation and finalization">
  <action>Run structural validation on the assembled constitution:</action>
  <action>- Verify all required sections are present</action>
  <action>- Check for conflicting policies across layers</action>
  <action>- Validate quality gate thresholds are reasonable</action>
  <action>- Ensure evolution history is initialized</action>

  <template-output section="5. Evolution History">
    <action>Create the initial evolution log entry:</action>
    <action>- Version: 1.0</action>
    <action>- Date: {{date}}</action>
    <action>- Author: {{user_name}}</action>
    <action>- Change Summary: Initial constitution creation</action>
    <action>Generate the Evolution History section</action>
  </template-output>

  <action>Present final constitution summary to user</action>
  <action>Save completed constitution to {governance_artifacts}/constitution.md</action>
  <action>Report: Constitution created successfully. Use [GV] to validate or [GE] to evolve it over time.</action>
</step>

</workflow>
