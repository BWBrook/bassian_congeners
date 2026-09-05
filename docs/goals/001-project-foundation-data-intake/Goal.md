# Goal 001: Project foundation and data intake

**Status:** Complete
**Date opened:** 2026-07-16
**Date completed:** 2026-07-16

## Completed-state objective

Goal 001 is complete when Bassian Congeners has a minimal repo-local operating
foundation and a decision-ready camera-data intake questionnaire that lets the
orchestrator frame a later, separately authorised data audit without Goal 001
inspecting or processing any real dataset.

## Why this matters

The private camera network is the project's primary empirical asset, but its
location, structure, authority, privacy, and derivation boundaries have not
been established in this repository. A compact human-and-custodian intake gate
prevents data archaeology, accidental exposure, and premature scientific or
technical decisions while preserving the camera-first, Tasmania-first
comparative question.

## Scope

Goal 001 may read only:

- docs/bassian_congener_QA_summary_transcript.md
- docs/bassian_congener_partitioning_project_plan.md
- docs/bassian_novelty_check.md
- files created within this goal's authorised write set

It may create or edit only:

- AGENTS.md
- README.md
- docs/data_intake_questionnaire.md
- docs/decisions.md
- docs/goals/001-project-foundation-data-intake/Goal.md
- docs/goals/001-project-foundation-data-intake/Plan.md
- docs/goals/001-project-foundation-data-intake/Runbook.md
- docs/goals/001-project-foundation-data-intake/Log.md

## Non-goals

- Inspecting, locating, opening, copying, querying, or summarising real data.
- Creating code, schemas, data directories, generated outputs, an R project,
  renv, targets, or dependencies.
- Public-data, modelling, GIS, remote/HPC, or manuscript work.
- Selecting analysis units, event rules, confidence thresholds, models,
  environmental variables, or compute architecture.
- Staging, committing, pushing, publishing, or changing Git history.

## Main review surface

docs/data_intake_questionnaire.md is the primary scientific and operational
deliverable. Barry's immediate review is limited to the compact Goal 002
authorisation gate. Technical metadata are explicitly assigned to the data
custodian and become pre-execution conditions. The recommended smallest safe
first slice remains a proposal for approval or amendment, not a decision.

docs/decisions.md is the secondary review surface. It separates supported
direction, provisional hypotheses, deferred choices, and non-goals.

## Deliverables

1. A repo-local AGENTS.md covering private data, scientific claims, authority,
   escalation, Git safety, and completion evidence.
2. A concise README.md describing purpose, concept-stage status, source notes,
   repository map, and the Goal 001 to human answers to Goal 002 sequence.
3. A complete, owner-tagged camera-data intake questionnaire.
4. A decision register containing only supported direction and explicit
   deferrals.
5. This durable Goal.md, Plan.md, Runbook.md, and Log.md packet.

## Authority

The executor may make documentation-only changes within the exact write set
above and run bounded read-only validation commands inside this repository.
The executor has no authority to inspect data, read other repositories or
unrelated files, expose information externally, or stage/commit/push changes.

Barry retains material scientific decisions. Barry and the data custodian
jointly own access, rights, privacy, output, execution-location, and first-slice
approval. A later Goal 002 packet must restate all granted authority; answers
to the questionnaire do not by themselves authorise data access.

## Validation

- All eight authorised files exist and agree on scope and sequence.
- The questionnaire covers all required intake topics without invented
  answers and makes owner/priority explicit.
- The immediate Barry gate is easy to scan and distinct from custodian-owned
  pre-execution metadata.
- The proposed first slice is clearly labelled as a proposal.
- No real dataset, code, environment, public-data, modelling, GIS, compute, or
  manuscript work appears in the change footprint.
- git diff --check exits successfully.
- git diff --stat and git status --short --branch are inspected.
- The final status contains only the eight authorised untracked files.

## Stop conditions

Stop and report uncertainty if:

- the authorised notes conflict materially;
- a required answer needs out-of-repository reading or data inspection;
- an internally consistent packet requires a new scientific decision;
- any unexpected pre-existing or concurrent worktree change appears; or
- validation reveals a path outside the authorised write set.
