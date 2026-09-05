# Camera-data intake questionnaire

**Purpose:** Collect the human decisions and metadata needed to frame Goal 002
without exposing or inspecting the camera dataset during Goal 001.

**Status:** Unanswered review surface. No answer is inferred from the concept
notes.

## How to answer

Short answers are welcome; "unknown", "not applicable", and "ask [name]" are
useful answers because they expose a real dependency. Do not place passwords,
tokens, or other credentials in this document. If a location or permission is
sensitive, name the custodian and secure handoff method instead.

Ownership and priority tags mean:

- **[Barry]** - scientific or scope decision for Barry.
- **[Data custodian]** - technical metadata the custodian can supply.
- **[Barry + custodian]** - authority or risk boundary requiring both views.
- **[Gate]** - needed to authorise and frame Goal 002.
- **[Pre-execution]** - may be completed after authorisation, but must be
  resolved before Goal 002 opens the dataset.
- **[Later]** - useful after the audit contract is settled.

## Barry's immediate Goal 002 gate

Barry does not need to complete every technical item below. Goal 002 can be
framed once these four decisions are recorded:

- [ ] **Authority and access:** approve the accountable custodian and bounded
  read-only access route (R1 and R3).
- [ ] **Rights and outputs:** approve ownership/privacy constraints and what
  may be copied, derived, retained, or committed (R4, R5, and R10).
- [ ] **Execution boundary:** approve the compute/storage location and
  restrictions (R24).
- [ ] **First slice:** approve or amend the proposed smallest safe first slice,
  its outputs, and its deletion rule (R25).

The data custodian can complete the remaining **[Pre-execution]** metadata
while Goal 002 is being framed. Unresolved items become explicit entry
conditions; they do not all require Barry to research or answer them.

## Intake questions

### Authority, location, and access

**R1. [Barry + custodian] [Gate] Who owns and who currently custodians each
relevant camera-data component?** Who can approve read access, derived outputs,
and any later image review?

Response:

**R2. [Data custodian] [Pre-execution] What is the canonical source for each
component?** Identify the storage
system and canonical location for site, deployment, effort/downtime,
event/image, and label data. Which copies are authoritative, and are any
mirrors stale or incomplete?

Response:

**R3. [Barry + custodian] [Gate] How should Goal 002 access the source?** Specify
the approved account or role, local/mounted/database access method, read-only
requirement, access window, and any custodian who must be present. Keep
credentials outside Git.

Response:

**R4. [Barry + custodian] [Gate] What ownership, ethics, contractual, or licence
conditions apply?** State who owns the records and images, whether partner
programmes impose different terms, and what acknowledgement, retention, or
onward-sharing rules must be followed.

Response:

**R5. [Barry + custodian] [Gate] What may be copied, derived, retained, and
committed?** Answer separately
for raw tables, image binaries, exact coordinates, de-identified extracts,
schema descriptions, checksums, row counts, aggregate diagnostics, plots,
logs, and code. State where approved temporary and durable outputs may live
and how temporary material must be deleted.

Response:

### Physical structure and joins

**R6. [Data custodian] [Pre-execution] What formats and approximate scale
should Goal 002 expect?** For each
component, give format or database engine, compression, approximate file/table
size, row or image count if known, and whether data are partitioned across
files, databases, programmes, or years.

Response:

**R7. [Data custodian] [Pre-execution] What are the logical tables or file
groups?** Name their roles without
pasting data: sites, cameras, deployments, operating intervals, downtime,
events/sequences, images, labels, taxonomy, programmes, and any bridge or
lookup tables. Is there a current data dictionary?

Response:

**R8. [Data custodian] [Pre-execution] How are those entities joined?** List
primary/foreign keys, expected
one-to-one or one-to-many relationships, bridge tables, version fields, and
known orphan or duplicate-key problems. Which table is authoritative when
fields disagree?

Response:

**R9. [Data custodian] [Pre-execution] What does each identifier mean and where
is it unique?** Cover site,
station, physical camera, programme, deployment, operating interval,
event/sequence, image, label, and taxon identifiers. Explain whether cameras
move, sites are renamed, IDs are reused, or legacy and current IDs require a
crosswalk.

Response:

### Coordinates, programmes, and effort

**R10. [Barry + custodian] [Gate] Where do coordinates attach and how must privacy
be handled?** State whether coordinates belong to sites or deployments, their
CRS, precision, datum, missing-value conventions, and known corrections.
Identify sensitive locations and the permitted precision or regional
replacement for working extracts, diagnostics, maps, logs, and committed
outputs.

Response:

**R11. [Data custodian] [Pre-execution] How is deployment effort represented?**
Identify planned and observed
start/end fields, active-camera days, operating intervals, downtime, failure,
battery/card changes, servicing, partial days, and never-activated
deployments. What evidence determines a defensible non-detection denominator?

Response:

**R12. [Data custodian] [Pre-execution] Which camera programmes or surveys
contributed records?** For each,
state its purpose, date range, region, sampling design, site-selection process,
and whether programme membership changes identifier, effort, or access rules.

Response:

**R13. [Data custodian] [Pre-execution] Which camera models and settings vary
materially?** Cover sensor/model,
firmware if relevant, placement/height, orientation, trigger sensitivity,
burst size, inter-trigger delay, image/video mode, flash mode, and setting
changes within deployment. Where are these fields recorded, and which are
missing?

Response:

**R14. [Data custodian] [Pre-execution] Which deployments were passive and
which were baited or lured?** State
how status, bait/lure type, timing, replenishment, and changes are recorded.
Can passive main-island and baited island deployments be separated
unambiguously? Are any other programmes non-passive?

Response:

### Taxonomy, labels, and identity

**R15. [Data custodian] [Pre-execution] What is the canonical taxonomy and
species-code system?** Give the
authoritative code/name lookup, taxonomic version if known, treatment of
subspecies, spelling variants, unidentified birds, "no animal", and
non-focal taxa. Which codes represent the four focal species?

Response:

**R16. [Data custodian] [Pre-execution] What is the provenance of each label
and confidence field?** Distinguish
expert, contextual, automated/CNN, imported, and later-corrected labels.
Define confidence scales or thresholds, reviewer identity/role, review date,
label version, conflict resolution, and whether original labels remain
recoverable.

Response:

**R17. [Data custodian] [Pre-execution] How are ambiguous Black/Grey Currawong
records represented?** State
whether ambiguity has its own code, whether contextual inference overwrote an
original uncertain label, what visual/contextual evidence was used, whether
confidence is comparable across programmes, and whether a conservative
high-confidence subset can be reconstructed without opening images.

Response:

**R18. [Barry + custodian] [Pre-execution] Are there other focal-species
identification issues?** Cover
Bronzewing ambiguity, juveniles/sex labels, partial animals, multi-species
frames, same-frame Bronzewings, and any suspected label drift. Which fields
must be ignored unless separately validated?

Response:

### Time, events, and coverage

**R19. [Data custodian] [Pre-execution] Which date/time fields exist and how
reliable is each?** State source
time zone, daylight-saving handling, camera clock setup, known drift or reset
patterns, correction fields, date-versus-time reliability, midnight edge
cases, and whether original and corrected timestamps are both retained.

Response:

**R20. [Data custodian] [Pre-execution] What is the current duplicate and
independent-event rule?** Explain how
bursts become events, the time threshold and species dependence if any, how
repeat triggers or lingering individuals are treated, whether duplicate files
exist, and whether event definitions can be rebuilt from immutable image-level
records.

Response:

**R21. [Data custodian] [Pre-execution] What temporal coverage is actually
available?** Give programme-level
start/end dates, ongoing components, deployment-duration patterns, major gaps,
seasonal gaps, incomplete years, and any known periods with changed methods or
label quality.

Response:

**R22. [Data custodian] [Pre-execution] What spatial clusters and regions
already exist?** Define any
programme, site-cluster, grid, reserve, subregion, region, island, or IBRA
labels; who assigned them; whether membership can change; and whether a
crosswalk exists. Note isolated sites and known geographic coverage gaps
without supplying sensitive coordinates here.

Response:

### Quality, compute, and the first handoff

**R23. [Data custodian] [Pre-execution] What known exclusions or quality issues
must be honoured immediately?**
List test records, invalid or duplicate deployments, corrupted/missing files,
unresolved joins, impossible dates, coordinate errors, label migrations,
programme-specific caveats, embargoes, and any existing exclusion register.
State which are confirmed versus suspected.

Response:

**R24. [Barry + custodian] [Gate] What compute and storage constraints apply to
Goal 002?** State the approved machine/location, whether work must remain
beside the source, available read-only and scratch storage, memory/runtime
limits, backup policy, network/egress restrictions, encryption requirements,
and whether remote or cloud processing is prohibited.

Response:

**R25. [Barry + custodian] [Gate] Is the smallest safe first slice below
approved, or how should it change?** Name the custodian who will create or
expose it and confirm the allowed outputs and deletion rule.

Response:

## Recommended smallest safe first slice

This is a proposal for Barry and the data custodian to approve or amend, not a
claim about the current data.

1. Begin with schema/data-dictionary material and table-level metadata for
   only the entities needed to connect sites, deployments, operating effort,
   events/images, labels, taxonomy, and programmes.
2. Add a read-only, de-identified record extract from one approved passive
   main-island programme and only a small custodian-selected set of
   deployments. Where available, include ordinary operation plus examples
   that exercise downtime and uncertain Currawong labelling.
3. Retain the join keys, effort intervals, dates, taxonomy codes, label
   provenance, and confidence fields needed to test structure. Include enough
   event context to distinguish no focal-species detection from missing data.
4. Exclude image binaries, exact coordinates, public data, environmental
   layers, and unrelated species detail. Replace sensitive locations with an
   approved site token and coarse region if needed.
5. Keep the slice outside Git. Goal 002 should initially produce only the
   explicitly approved schema, join, missingness, effort, and provenance
   diagnostics. Expand access only after that structural check passes.

## Useful later

These questions need not delay the initial audit contract.

**L1. [Barry] [Later] Which temporal units should later feasibility checks
compare?** Examples
could include day, month, season, or rolling windows, but no unit is selected
by Goal 001.

Response:

**L2. [Barry] [Later] Which spatial grains are scientifically meaningful
beyond existing administrative labels?** Identify candidate same-camera,
local-cluster, landscape, and regional definitions and the human
decision-maker for each.

Response:

**L3. [Barry + custodian] [Later] Under what later conditions may image
binaries be reviewed?** Define the
trigger for expert re-review, who may see images, whether a blinded sample is
possible, and what corrected-label provenance would be required.

Response:

**L4. [Data custodian] [Later] Which existing site or deployment descriptors
may later help interpret coverage?** Identify internal habitat, access,
placement, vegetation, land-use, or programme fields and their provenance; do
not nominate external GIS sources here.

Response:

**L5. [Barry + custodian] [Later] Who should review Goal 002 outputs before any
wider access or analysis?**
Name the scientific, data-custodial, privacy, and programme contacts and the
decisions each owns.

Response:

**L6. [Barry] [Later] What would make the audit decision-ready?** Rank the
minimum tables, diagrams, quality summaries, and go/no-go decisions Barry
needs, and state any content that must stay outside the repository.

Response:
