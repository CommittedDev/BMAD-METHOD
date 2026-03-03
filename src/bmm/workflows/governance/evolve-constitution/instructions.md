<workflow>

<step n="1" goal="Load current constitution and understand proposed changes">
  <action>Load the current constitution from {governance_artifacts}/constitution.md</action>
  <check if="no constitution found">
    <action>Inform user: No constitution found. Use [GI] Governance Init to create one first.</action>
    <action>Exit workflow</action>
  </check>
  <action>Parse current version number and evolution history from frontmatter</action>
  <ask>What changes would you like to propose to the constitution? Describe the changes, the reason for them, and which section(s) they affect.</ask>
</step>

<step n="2" goal="Analyze proposed changes against existing policies">
  <action>Map the proposed changes to specific constitution sections</action>
  <action>Check for conflicts with existing policies in other sections:</action>
  <action>- Does this change conflict with organizational directives?</action>
  <action>- Does this change affect quality gate thresholds?</action>
  <action>- Does this change impact compliance requirements?</action>
  <action>- Does this change weaken any security or privacy policies?</action>
  <action>Present analysis to user with any conflicts or concerns identified</action>
  <check if="conflicts found">
    <ask>Conflicts detected. Would you like to: [R] Resolve conflicts and proceed, [M] Modify the proposal, or [C] Cancel?</ask>
  </check>
</step>

<step n="3" goal="Apply changes and update evolution log">
  <action>Apply the approved changes to the relevant constitution sections</action>
  <action>Increment the version number (minor version bump for non-breaking changes, major for structural changes)</action>
  <action>Add new evolution log entry with:</action>
  <action>- Version: incremented version number</action>
  <action>- Date: {{date}}</action>
  <action>- Author: {{user_name}}</action>
  <action>- Category: which section(s) were modified</action>
  <action>- Change Summary: what was changed and why</action>
  <action>- Impact Assessment: what workflows or processes are affected</action>
  <action>Update the lastUpdated date in frontmatter</action>
</step>

<step n="4" goal="Validate and save the evolved constitution">
  <action>Run quick structural validation to ensure changes did not break constitution structure</action>
  <action>Present the changes summary: sections modified, new version, evolution log entry</action>
  <action>Save the updated constitution to {governance_artifacts}/constitution.md</action>
  <action>Suggest: Run [GV] Governance Validate for a full consistency check after significant changes.</action>
</step>

</workflow>
