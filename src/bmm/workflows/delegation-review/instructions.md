<workflow>

<step n="1" goal="Load all delegation context files from async workflow executions">
  <action>Scan {implementation_artifacts}/delegation/ for all .yaml delegation context files</action>
  <check if="no delegation files found">
    <action>Inform user: No delegation context files found. ASYNC workflows have not been run yet, or delegation files have already been reviewed and archived.</action>
    <action>Exit workflow</action>
  </check>
  <action>List all found delegation files with workflow name, date, and status</action>
  <ask>Which delegation(s) would you like to review? [A] All pending, or specify workflow name/date</ask>
</step>

<step n="2" goal="Present consolidated macro-review for each selected delegation">
  <iterate>For each selected delegation context file:</iterate>
  <action>Load the full delegation context</action>
  <action>Present a structured review:</action>
  <action>1. WORKFLOW SUMMARY: What workflow was executed, when, with what inputs</action>
  <action>2. DECISIONS MADE: Table of all decisions the agent made autonomously</action>
  <action>   - Decision description, category, choice made, alternatives considered, rationale</action>
  <action>3. ARTIFACTS PRODUCED: List of all output files with locations</action>
  <action>4. QUALITY GATE RESULTS: How the output scored against async quality thresholds</action>
  <action>5. FLAGGED ITEMS: Any decisions or outputs that were borderline or uncertain</action>
  <ask>For this delegation: [A] Approve all, [R] Request revision on specific items, [D] Reject and re-run in SYNC mode</ask>
</step>

<step n="3" goal="Process review decisions and archive">
  <check if="user approved">
    <action>Mark delegation context as reviewed and approved</action>
    <action>Move delegation file to {implementation_artifacts}/delegation/reviewed/</action>
  </check>
  <check if="user requested revisions">
    <action>Document which items need revision</action>
    <action>Suggest running the specific workflow section in SYNC mode for those items</action>
  </check>
  <check if="user rejected">
    <action>Mark delegation as rejected</action>
    <action>Suggest re-running the workflow in SYNC mode for full human review</action>
  </check>
  <action>Report review completion summary</action>
</step>

</workflow>
