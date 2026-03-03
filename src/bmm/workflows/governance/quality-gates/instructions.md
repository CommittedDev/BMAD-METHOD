<workflow>

<step n="1" goal="Load current quality gate configuration">
  <action>Load the current constitution from {governance_artifacts}/constitution.md</action>
  <check if="no constitution found">
    <action>Inform user: No constitution found. Use [GI] Governance Init to create one first.</action>
    <action>Exit workflow</action>
  </check>
  <action>Load gate-definitions.csv for reference on standard gate categories</action>
  <action>Extract Section 3 (Quality Gate Definitions) from the constitution</action>
  <action>Present current SYNC and ASYNC gate configurations in a comparison table</action>
</step>

<step n="2" goal="Review and adjust quality gate thresholds">
  <ask>What would you like to do?
  [1] Adjust SYNC mode thresholds
  [2] Adjust ASYNC mode thresholds
  [3] Add a new quality gate
  [4] Update override policies
  [5] Review and confirm current configuration</ask>

  <check if="user selected 1 or 2">
    <action>For each gate in the selected mode, present current threshold and ask if adjustment needed</action>
    <action>Validate that SYNC thresholds remain >= ASYNC thresholds for each gate</action>
    <action>Warn if proposed thresholds are unusually low or high compared to defaults</action>
  </check>

  <check if="user selected 3">
    <action>Ask for new gate: name, description, SYNC threshold, ASYNC threshold, category</action>
    <action>Validate new gate does not duplicate an existing one</action>
  </check>

  <check if="user selected 4">
    <action>Present current override policies from Section 3.3</action>
    <action>Ask what changes to override conditions, approval requirements, or escalation paths</action>
  </check>

  <check if="user selected 5">
    <action>Present full gate configuration for review</action>
    <ask>Are you satisfied with the current configuration? [Y] Yes, [N] No, make changes</ask>
  </check>
</step>

<step n="3" goal="Apply changes and update constitution">
  <action>Update Section 3 of the constitution with the new quality gate configuration</action>
  <action>Add evolution log entry documenting the quality gate changes</action>
  <action>Increment constitution version number</action>
  <action>Save the updated constitution to {governance_artifacts}/constitution.md</action>
  <action>Present summary of changes made to quality gates</action>
</step>

</workflow>
