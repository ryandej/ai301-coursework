---
name: pr-precheck
description: Grade a PR package (a candidate pull request read against the plan it claims to implement and the issue that plan belongs to) and decide whether it is ready to submit. Use when checking your own branch, draft PR title, and description before opening the pull request, or when grading an eval package bundle.
---

# pr-precheck: rubric-driven PR grading

## The question

Grade exactly one PR package and answer one question: is this pull
request ready to submit?

A PR package contains the candidate PR title and description, the
committed branch diff, test evidence, and the plan it claims to
implement, read against the issue that plan belongs to. Grade the PR
by executing the checks in `rubric.md` using the process in
`procedure.md` and the evidence locations in
`references/evidence-guide.md`. Do not grade from general impressions
or substitute a different question.

## Inputs and modes

Run in exactly one of two modes:

- **Live mode**: grade the student's own PR before it is opened. Read
  `plan.md`, including any `## Deviations` notes; the committed branch
  diff produced by `git diff main...HEAD`; the PR title and description
  in `pr_draft.md`; the command output and reproduction evidence in
  `test_evidence.md`; and the issue URL supplied by the student.
  Gather issue-side evidence from the scoped Path Review repository,
  including the issue thread, the repository's PR template, and
  `docs/CONTRIBUTING.md`. Treat `git diff main...HEAD` as the complete
  set of committed changes the branch makes relative to `main`; do not
  treat uncommitted working-tree files as part of the PR diff.
  For a house-chain student, use the house plan and house reproduction
  pack in place of the student's own plan and reproduction evidence,
  while grading the same evidence families with the same rubric.

- **Eval mode**: grade one supplied practice package bundle. Treat the
  bundle as the whole world. Use only facts contained in that bundle;
  do not fetch GitHub, inspect a working tree, or use outside evidence.
  Run every rubric check and apply the complete verdict rule.

## The scope seam (live mode only)

In live mode, read `scope.md` before grading anything else. Use its
`Repo:` line to determine the only repository this skill may grade and
apply the house rules recorded there.

Refuse to grade if the supplied issue or PR belongs outside the scoped
repository. If the `Repo:` line still contains an unfilled placeholder,
stop without grading and tell the student to fill it with their
section's Path Review repository. Never guess the scope.

In eval mode, ignore `scope.md` entirely.

## The voice seam (live mode only)

In live mode, read `voice-guide.md` and check the outgoing PR title and
description against it. Report any violated voice rule in the readable
summary and identify the rule that was broken.

The voice guide does not change the verdict by itself unless a check in
`rubric.md` explicitly uses it as evidence.

In eval mode, ignore `voice-guide.md` entirely.

## Component reads

Read `rubric.md` to determine the checks, the evidence each check
requires, its pass condition, its weight, and the final verdict rule.

Read `references/evidence-guide.md` to determine where each evidence
family lives in live mode and eval mode and what acceptable evidence
looks like.

Execute `procedure.md` exactly as written. It determines the read
order, evidence-gathering process, check execution, and verdict
assembly. Do not silently invent a missing procedure step. If the
procedure is silent where a step is needed, report that gap in the
summary.

If `rubric.md` contains no student-written checks, or `procedure.md`
contains no student-written steps, refuse to grade and say that the
skill cannot run without both a completed rubric and a completed
procedure.

## Verdict and output

Use only two verdicts:

- `accept`: the PR is ready to submit under the rubric's verdict rule.
- `reject`: the PR should be held under the rubric's verdict rule.

Before the JSON block, you may print a short readable summary with one
line per check and any live-mode voice-guide notes.

End every completed grading run with the following fenced JSON block.
It must be valid, must be the final thing in the reply, and nothing may
appear after it.

```json
{
  "item": "<PR URL or bundle id>",
  "checks": [
    {"name": "<check name>", "grade": "pass|fail|unclear",
     "evidence": "<one line: the fact or quote that decided it>"}
  ],
  "verdict": "accept|reject"
}
```

## Grading discipline

- Gather evidence before grading. Every check must identify the fact,
  quote, diff line, command output, or missing evidence that decided
  its grade. "Looks fine" is not evidence.
- Grade the PR itself, not how polished or confident its wording is. A
  concise PR can be complete, and a detailed PR can still contain
  silent drift, missing tests, unsupported claims, or repository-policy
  violations.
- Let `rubric.md` decide each grade and the final verdict. If a result
  feels wrong but follows the written pass condition, keep the result
  and report the tension rather than changing the rule during the run.
- Let `procedure.md` decide how grading is performed. Follow it as
  written and report gaps instead of improvising around them.
- Grade claims by comparing them with the underlying evidence. In live
  mode, compare the diff with the plan, the test evidence with the
  plan's test plan and reproduced issue, and the PR description with
  the actual diff and test results.
- Treat an `unclear` grade according to the verdict rule in
  `rubric.md`. If that rule does not specify what `unclear` means,
  treat it as a failure. An unverifiable required claim is not ready
  to submit.
