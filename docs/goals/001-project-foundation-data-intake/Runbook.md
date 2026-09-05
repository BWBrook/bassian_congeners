# Goal 001 runbook

Run these checks from a zsh shell. They are deliberately bounded to repository
state, the three authorised source notes, and the eight Goal 001 files.

## 1. Confirm location and Git baseline

    cd /Users/bwbrook/papers/bassian_congeners
    pwd
    git rev-parse --show-toplevel
    git branch --show-current
    git rev-parse HEAD
    git status --short --branch --untracked-files=all

Expected baseline identity: repository root shown above, branch main, and
starting HEAD 3ea6cf35f66895cd5ba6e8dc0c081c25971189bb. Stop if any unexpected
path is modified or untracked.

## 2. Verify the exact deliverable set

    files=(
      AGENTS.md
      README.md
      docs/data_intake_questionnaire.md
      docs/decisions.md
      docs/goals/001-project-foundation-data-intake/Goal.md
      docs/goals/001-project-foundation-data-intake/Plan.md
      docs/goals/001-project-foundation-data-intake/Runbook.md
      docs/goals/001-project-foundation-data-intake/Log.md
    )
    for file in "${files[@]}"; do
      test -f "$file" || { print -u2 "missing: $file"; exit 1; }
    done

Expected outcome: exit 0 and no output.

## 3. Review questionnaire gate and coverage

    questionnaire=docs/data_intake_questionnaire.md
    markers=(
      "## Barry's immediate Goal 002 gate"
      "[Barry]"
      "[Data custodian]"
      "[Barry + custodian]"
      "[Gate]"
      "[Pre-execution]"
      "This is a proposal"
    )
    for marker in "${markers[@]}"; do
      if ! rg -q --fixed-strings "$marker" "$questionnaire"; then
        print -u2 "missing questionnaire marker: $marker"
        exit 1
      fi
    done
    joint_gate_questions=(1 3 4 10 24)
    for number in "${joint_gate_questions[@]}"; do
      expected="**R$number. [Barry + custodian] [Gate]"
      if ! rg -q --fixed-strings "$expected" "$questionnaire"; then
        print -u2 "joint gate ownership missing: R$number"
        exit 1
      fi
    done
    required_topics=(
      "canonical source"
      "formats and approximate scale"
      "logical tables"
      "joined"
      "identifier"
      "coordinates"
      "effort"
      "camera programmes"
      "camera models"
      "passive"
      "baited"
      "taxonomy"
      "provenance"
      "Currawong"
      "date/time"
      "time zone"
      "clock"
      "duplicate"
      "independent-event"
      "temporal coverage"
      "spatial clusters"
      "licence"
      "ownership"
      "copied, derived, retained, and committed"
      "compute and storage"
      "exclusions or quality issues"
      "smallest safe first slice"
    )
    questionnaire_text=$(tr '\n' ' ' < "$questionnaire" | tr -s ' ')
    for topic in "${required_topics[@]}"; do
      if ! print -r -- "$questionnaire_text" |
          rg -qi --fixed-strings "$topic"; then
        print -u2 "missing required topic: $topic"
        exit 1
      fi
    done

Expected outcome: exit 0 and no output. Topic matching normalises Markdown line
breaks before checking, so wrapping does not change the result.

## 4. Scan the eight files for unfinished or malformed text

    unfinished_pattern='TB''D|TO''DO|FIX''ME'
    if rg -n "$unfinished_pattern" "${files[@]}"; then
      print -u2 "unfinished marker found"
      exit 1
    fi
    if rg -n '[[:blank:]]+$' "${files[@]}"; then
      print -u2 "trailing whitespace found"
      exit 1
    fi

Expected outcome: exit 0 and no matches.

## 5. Confirm the authorised source notes are unchanged

    source_notes=(
      docs/bassian_congener_QA_summary_transcript.md
      docs/bassian_congener_partitioning_project_plan.md
      docs/bassian_novelty_check.md
    )
    git diff --quiet -- "${source_notes[@]}"

Expected outcome: exit 0 and no output.

## 6. Run final Git checks

    git diff --check
    git diff --stat
    git status --short --branch --untracked-files=all

git diff --check and git diff --stat inspect tracked changes only. Because Goal
001 creates untracked files and staging is prohibited, a blank diff/stat is
expected; the status output is the authoritative footprint and must list
exactly the eight authorised files. Do not stage files merely to produce a
stat. Record the observed outputs in Log.md.
