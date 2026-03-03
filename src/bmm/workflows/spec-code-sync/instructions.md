<workflow>

<step n="1" goal="Load all specifications and scan codebase structure">
  <action>Load PRD, architecture, epics, and UX design documents via discover_inputs protocol</action>
  <check if="no spec documents found">
    <action>Inform user: No specification documents found. Create specs first (CP for PRD, CA for Architecture).</action>
    <action>Exit workflow</action>
  </check>
  <action>Scan the project codebase to understand current implementation state:</action>
  <action>- Read package.json/requirements.txt/go.mod for technology stack</action>
  <action>- Analyze directory structure for architecture alignment</action>
  <action>- Check for API route definitions, database models, test files</action>
  <action>- Load project-context.md if available for additional context</action>
  <action>Load the drift detection checklist for structured validation</action>
</step>

<step n="2" goal="Compare architecture constraints against actual implementation">
  <template-output section="Architecture Drift">
    <action>For each architecture claim, verify against codebase:</action>
    <action>- Technology stack: Do package files match architecture technology choices?</action>
    <action>- Directory structure: Does file organization match architecture module structure?</action>
    <action>- API design: Do actual endpoints match architecture API specifications?</action>
    <action>- Data model: Do database schemas/models match architecture data design?</action>
    <action>- Dependencies: Are dependency choices aligned with architecture constraints?</action>
    <action>- Deployment: Do config files match architecture deployment specifications?</action>
    <action>For each finding: classify severity (critical/warning/info) and propose spec update</action>
  </template-output>
</step>

<step n="3" goal="Compare PRD requirements against implemented features">
  <template-output section="Requirements Drift">
    <action>For each PRD requirement category, check implementation status:</action>
    <action>- Functional requirements: Are required features implemented?</action>
    <action>- Non-functional requirements: Are performance, security, accessibility targets met?</action>
    <action>- User journeys: Are all specified user flows implemented end-to-end?</action>
    <action>- Integration requirements: Are third-party integrations in place?</action>
    <action>Also check for code that has NO spec backing (orphaned implementations)</action>
    <action>For each finding: classify severity and propose PRD update or code change</action>
  </template-output>
</step>

<step n="4" goal="Compare epic stories against implementation completeness">
  <template-output section="Epic/Story Drift">
    <action>For each epic and its stories:</action>
    <action>- Are all stories implemented per their acceptance criteria?</action>
    <action>- Are there implemented features not covered by any story?</action>
    <action>- Do story descriptions still match what was actually built?</action>
    <action>- Are there stories marked as done that have incomplete implementations?</action>
    <action>For each finding: classify severity and propose epic/story update</action>
  </template-output>
</step>

<step n="5" goal="Generate drift report summary and recommendations">
  <template-output section="Summary and Recommendations">
    <action>Calculate overall drift score (0-100, where 0 = perfectly aligned, 100 = completely drifted)</action>
    <action>Count findings by severity: critical, warning, info</action>
    <action>Generate ordered list of recommended actions:</action>
    <action>1. Critical items: spec claims that are factually wrong about the codebase</action>
    <action>2. Warning items: areas where spec and code have diverged but neither is wrong</action>
    <action>3. Info items: minor inconsistencies or documentation improvements</action>
    <action>Suggest next steps: update specs, fix code, or schedule a course correction (CC)</action>
  </template-output>

  <action>Save drift report to {planning_artifacts}/drift-report-{{date}}.md</action>
  <action>Report: Drift analysis complete. Overall drift score: X/100. Y critical, Z warning findings.</action>
</step>

</workflow>
