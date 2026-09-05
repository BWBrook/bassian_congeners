# Bassian Congeners: clean-start handover

**Prepared:** 2026-09-05
**Audience:** the next lead Codex agent starting directly in this repository

## Start here

This is a nascent, camera-first comparative ecology project. The scientific
question is whether two unrelated congeneric bird pairs repeatedly partition
Tasmanian landscapes along a shared ecosystem-structure axis, while differing
in their mode of overlap:

- Brush versus Common Bronzewings (*Phaps elegans*, *P. chalcoptera*)
- Black versus Grey Currawongs (*Strepera fuliginosa*, *S. versicolor*)

The preferred working hypothesis is that Brush Bronzewings and Black
Currawongs favour the denser, mesic end of a structural gradient, while Common
Bronzewings and Grey Currawongs favour more open, xeric environments.
Bronzewings may coexist locally; Currawongs may show stronger local dominance,
transience, or temporal replacement. These are hypotheses, not results.

The contribution is not four static SDMs or another wet-versus-dry habitat
description. The high-value scientific object is a comparative, detection-aware,
scale-explicit and temporally explicit test of repeated congeneric
partitioning. Tasmania and the private camera network are the empirical core;
mainland and Bassian comparisons are secondary unless evidence later earns a
larger role.

## Live repository state at handover

- Repository: `/Users/bwbrook/papers/bassian_congeners`
- Branch: `main`, tracking `origin/main`
- HEAD: `3ea6cf3` (`Initial commit`)
- The three original concept notes are tracked under `docs/`.
- Goal 001 produced a repo contract, README, decision register, data-intake
  questionnaire, and an execution record. Those files are currently untracked,
  not committed or published. Treat them as active work, not disposable files.
- This handover is also untracked when first written.
- No real camera dataset has been opened, located, queried, copied, transformed,
  or summarised in the work recorded here.

Before changing anything, read the live global instructions, this repository's
`AGENTS.md`, `README.md`, `docs/decisions.md`, and
`docs/data_intake_questionnaire.md`, then inspect `git status`. Preserve the
untracked bootstrap work. Read the three concept notes only as needed; the
1,200-line project plan is broad ideation, not a specification.

## What has been established

1. The comparative two-pair framing is the project's centre. Do not collapse
   it into independent species models.
2. The design must retain spatial grain and temporal structure. Same-camera,
   local-cluster, landscape, and regional overlap have different meanings.
3. Site-season detection/non-detection is a plausible primary analytical unit;
   daily occupancy rate may be a secondary activity proxy. Neither is frozen
   until the data audit shows what the records support.
4. Passive main-island deployments must not be naively pooled with baited King
   and Flinders Island deployments.
5. Competition, hybridisation, abundance, and causal mechanism cannot be
   inferred from camera co-occurrence alone. Currawong identification
   uncertainty and camera-clock reliability need explicit treatment.
6. Novelty depends on resolving gradient, scale, detection, and dynamics.
   Loyn (2002) and species accounts already establish broad habitat
   segregation as prior knowledge.
7. Public occurrence data, environmental layers, modelling, HPC, and manuscript
   construction are deliberately deferred. None should begin merely because
   the eventual project may need them.

## Current decision point

The project is ready for a human-and-data-custodian intake discussion, not a
data analysis. `docs/data_intake_questionnaire.md` is intentionally unanswered.
Barry previously proposed working through its four summary gates in chat, one
at a time:

1. **Authority and access:** identify the accountable custodian and approve a
   bounded read-only route (R1 and R3).
2. **Rights and outputs:** settle ownership, privacy, coordinate handling, and
   what may be copied, derived, retained, or committed (R4, R5, and R10).
3. **Execution boundary:** approve compute and storage location and restrictions
   (R24).
4. **First slice:** approve or amend the smallest safe first slice, permitted
   outputs, and deletion rule (R25).

Recommended next move: discuss gate 1 with Barry. Do not ask him to answer the
custodian's full technical questionnaire. Once the four summary gates are
resolved, frame the smallest bounded data-audit tranche and state unresolved
technical metadata as entry conditions. Do not open any dataset until the
relevant authority, privacy, copying, output, and execution rules are explicit.

## How to run the work

Use
[`twilight-laboratory`](/Users/bwbrook/.codex/skills/twilight-laboratory/SKILL.md)
as the primary collaboration discipline: align on consequential scientific
choices, work autonomously on reversible details, use native subagents for
bounded independent work when they add value, inspect their evidence directly,
and report at a meaningful scientific checkpoint rather than after every
mechanical stage.

Use
[`kill-your-darlings`](/Users/bwbrook/.codex/skills/kill-your-darlings/SKILL.md)
selectively once implementation or analysis machinery exists. Make every
module, dependency, test, output, and model earn its recurring complexity.
Build the smallest coherent path from authorised inputs to decision-relevant
evidence; do not preserve speculative features or obsolete formats. This lens
must never weaken source integrity, privacy, data recovery, or inferential
validity.

The governing contract with Barry is:

> Rigour at the scientific decision boundary; proportional engineering
> everywhere else.

Prespecify comparisons that could change the scientific conclusion, protect
data and provenance, and verify consequential claims. Elsewhere, prefer the
smallest clear implementation that answers the current question. Perform one
focused review and repair pass, then stop when more work is mainly polish or
unlikely to change a decision. Bring Barry substantive scientific, strategic,
public-release, resource, or risk trade-offs; make routine reversible choices
yourself.

## Important reset from the old workflow

Earlier files and conversation used Chief-of-Staff worktrees, a named action
agent (`bronzewing`), and four-file goal packets. Those are retired workflow
defaults under the current global instructions. Work directly in this owning
repository using current native tools and a proportionate planning surface.
The old Goal 001 packet remains useful evidence of what was done and checked,
but it is not mandatory machinery for future work. Preserve its genuine
scientific, private-data, Git, and publication boundaries.

## Near-term success condition

The next tranche succeeds when the four intake gates are answered clearly
enough to define a safe, minimal data audit with explicit inputs, allowed
operations, outputs, validation, and no-publish boundary. It does not need to
design the eventual modelling pipeline. The audit should first determine
whether effort, joins, identifiers, labels, coverage, and repeated site-seasons
can support the central comparative question. Let that evidence determine what
comes next.
