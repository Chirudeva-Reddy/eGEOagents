## ADDED Requirements

### Requirement: Verified installation baseline
The project SHALL establish an isolated published-package and source baseline before selecting a new release scope.

#### Scenario: Wheel contains loop modules
- **WHEN** the published wheel contains loop code
- **THEN** the audit verifies documented behavior and packaged resources outside the source checkout rather than concluding either completeness or absence from version labels.

### Requirement: Valid measurement semantics
The proposed release SHALL distinguish error, empty, valid_absent and valid_present observations and preserve provenance without rewriting historical evidence.

#### Scenario: Empty answers
- **WHEN** a response has no usable answer
- **THEN** it is marked empty or error with diagnostic evidence and excluded from valid absence counts; the report displays missing coverage and cannot claim a complete visibility result.

#### Scenario: Rerun after an invalid snapshot
- **WHEN** an invalid measurement is rerun
- **THEN** the new run has a unique identity and the original record is retained with a separate invalidation reference.

### Requirement: Comparable segmented evidence
The proposed release SHALL distinguish branded, generic and technical queries and record query-set and provider configuration for comparisons.

#### Scenario: Changed query set or provider surface
- **WHEN** a comparison spans incompatible query definitions or provider surfaces
- **THEN** the report marks the incompatibility rather than presenting an unqualified trend.

### Requirement: Demand-based release decision
The owner SHALL review baseline evidence and external-use findings before approving a feature implementation scope.

#### Scenario: Interest without recurring use
- **WHEN** repository traffic grows but repeated useful use is unverified
- **THEN** the roadmap records adoption as unknown and does not unlock hosted development or a feature release from star counts.

### Requirement: Existing-loop reuse
The implementation proposal SHALL inventory and reuse the existing workspace, project contract, collectors and outcome ledger before introducing new infrastructure.

#### Scenario: Existing capability overlaps candidate feature
- **WHEN** an existing command or ledger fulfills a candidate requirement
- **THEN** the implementation plan extends or documents it instead of creating a parallel state system.

### Requirement: Explicit authorization and observational claims
The workflow SHALL require explicit owner approval for publication, merges, release and implementation scope, and SHALL describe before/after outcomes as observational unless stronger evidence exists.

#### Scenario: Owner does not respond
- **WHEN** an approval request receives no response
- **THEN** the action remains pending and is never authorized by elapsed time.

#### Scenario: Visibility rises after an intervention
- **WHEN** later observations show more mentions
- **THEN** the report links the intervention and observation evidence without asserting the intervention caused the increase.
