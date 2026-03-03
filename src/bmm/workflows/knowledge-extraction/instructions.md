<workflow>

<step n="1" goal="Load all session traces and retrospectives for analysis">
  <action>Load all session trace files from {trace_artifacts}/</action>
  <action>Load all retrospective files from {implementation_artifacts}/</action>
  <check if="no traces AND no retrospectives found">
    <action>Inform user: No session traces or retrospectives found to analyze. Run workflows with session tracing enabled, or complete a retrospective first.</action>
    <action>Exit workflow</action>
  </check>
  <action>Load current constitution if available (for cross-referencing proposed updates)</action>
  <action>Load project context if available (for context-aware learning extraction)</action>
  <action>Load knowledge-categories.csv for categorization framework</action>
  <action>Present summary: "Found X traces and Y retrospectives spanning [date range]. Ready to extract knowledge."</action>
</step>

<step n="2" goal="Analyze patterns across traces and retrospectives">
  <action>Analyze all loaded traces and retrospectives to identify:</action>

  <template-output section="1. Pattern Discoveries">
    <action>SUCCESSFUL PATTERNS (Repeat These):</action>
    <action>- Identify decisions that consistently led to good outcomes</action>
    <action>- Find workflow approaches that reduced rework or improved quality</action>
    <action>- Note technology choices that worked well in this project context</action>
    <action>- Identify testing strategies that caught real bugs</action>

    <action>ANTI-PATTERNS (Avoid These):</action>
    <action>- Identify decisions that led to rework, bugs, or scope creep</action>
    <action>- Find workflow steps that were consistently problematic</action>
    <action>- Note approaches that were tried and abandoned</action>
    <action>- Identify recurring blockers or pain points</action>
  </template-output>
</step>

<step n="3" goal="Generate proposals for constitution, project context, and agent behavior updates">
  <template-output section="2. Rule Proposals">
    <action>PROPOSED CONSTITUTION UPDATES:</action>
    <action>- Based on discovered patterns, propose new policies or policy modifications</action>
    <action>- For each proposal: what to add/change, which section, rationale from evidence</action>
    <action>- Flag if any proposed changes conflict with existing policies</action>

    <action>PROPOSED PROJECT CONTEXT UPDATES:</action>
    <action>- Identify coding patterns, conventions, or architectural decisions that should be documented</action>
    <action>- Propose additions to project-context.md for future AI agent context</action>

    <action>PROPOSED AGENT BEHAVIOR UPDATES:</action>
    <action>- Identify workflow improvements based on trace analysis</action>
    <action>- Suggest quality gate threshold adjustments based on actual pass/fail rates</action>
  </template-output>

  <template-output section="3. Reusable Examples">
    <action>CODE PATTERNS WORTH REUSING:</action>
    <action>- Extract code patterns from traces that solved common problems well</action>

    <action>DECISION TEMPLATES WORTH REUSING:</action>
    <action>- Extract decision frameworks from traces that led to good outcomes</action>
    <action>- Create reusable decision templates for common architecture/technology choices</action>
  </template-output>
</step>

<step n="4" goal="Present proposals and apply approved changes">
  <template-output section="4. Cross-Project Applicability">
    <action>Categorize all findings by scope:</action>
    <action>- ORGANIZATION-LEVEL: Learnings that apply to all projects (propose constitution updates)</action>
    <action>- TEAM-LEVEL: Learnings specific to this team's workflow preferences</action>
    <action>- PROJECT-SPECIFIC: Learnings that only apply to this project (propose project-context updates)</action>
  </template-output>

  <action>Present summary of all proposals with recommended actions</action>
  <ask>Which proposals would you like to apply?
  [1] Apply constitution updates (will invoke GE - Governance Evolve)
  [2] Apply project context updates
  [3] Apply both
  [4] Save knowledge packet only (apply later)
  [5] Review and select individual proposals</ask>

  <check if="user selected 1 or 3">
    <action>Prepare constitution evolution with proposed changes</action>
    <action>Suggest user run [GE] Governance Evolve with the proposed changes</action>
  </check>
  <check if="user selected 2 or 3">
    <action>Update project-context.md with approved additions</action>
  </check>

  <action>Save knowledge packet to {project_knowledge}/knowledge-packet-{{date}}.md</action>
  <action>Report: Knowledge packet saved. X patterns discovered, Y proposals generated.</action>
</step>

</workflow>
