<workflow>

<step n="1" goal="Discover and catalog project repositories">
  <action>Load architecture document for understanding system boundaries and service decomposition</action>
  <ask>How is your project structured? Describe the repositories, services, or packages that make up the system.</ask>
  <action>For each repository/service identified:</action>
  <action>- Name and location (path or URL)</action>
  <action>- Role (api, frontend, shared-lib, infra, docs, etc.)</action>
  <action>- Primary technology</action>
  <action>- Team owner (if applicable)</action>
</step>

<step n="2" goal="Map dependencies and coordination points">
  <template-output section="repositories">
    <action>For each repository, document:</action>
    <action>- Dependencies on other repositories (which services does it call?)</action>
    <action>- Shared contracts (API schemas, protobuf definitions, shared types)</action>
    <action>- Deployment order (which services must deploy first?)</action>
  </template-output>

  <template-output section="coordination">
    <action>Define coordination configuration:</action>
    <action>- Shared specs location (monorepo path or separate spec repo)</action>
    <action>- API contract location (OpenAPI specs, protobuf definitions)</action>
    <action>- Deployment order for safe rollouts</action>
    <action>- Cross-repo change coordination process</action>
  </template-output>
</step>

<step n="3" goal="Save manifest">
  <action>Validate manifest completeness: all repos listed, dependencies mapped, coordination defined</action>
  <action>Save multi-repo manifest to {governance_artifacts}/multi-repo-manifest.yaml</action>
  <action>Report: Multi-repo manifest created with X repositories and Y dependency mappings.</action>
  <action>Suggest: Reference this manifest when running architecture or sprint planning for cross-repo awareness.</action>
</step>

</workflow>
