# Unit 1 — Issue Selection

Path: `beat-1-sandbox/unit-1/selection.md`

Record of the issue carried into Unit 2, and of the evaluation runs that produced
`eval-run.txt`. This file is graded at the path above; a copy kept anywhere else in
the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the
wrong label is not graded.

---

## Selected issue

**Issue link**

https://github.com/codepath/pathreview-ai301-fa26-s3/issues/73

**Verdict output**

Live state re-verified: #73 is open, no assignee, no open linked PR (the only comments are student claim/repro posts, which the Path Review house rule tells me to ignore). Repo-level facts are unchanged from this session: not archived, last push 2026-09-16, human default-branch commits by Aburke225 through 2026-09-16 (within 365 days of the 2026-09-27 capture), and docs/CONTRIBUTING.md welcomes contributions with no AI restriction.

#73 — README vs .env.example env-var mismatch → accept
- Maintainer alive: pass — human commits within 365 days
- Repository in use: pass — not archived, pushed 2026-09-16
- Newcomer-sized scope: pass — make two named files (README.md, .env.example) agree on OPENROUTER_API_KEY/LLM_PROVIDER
- Direction settled: pass — body states the exact outcome; no design debate
- Nobody actively owns it: pass — no assignee, no open PR; the many claim comments are neutralized by the house rule
- Contribution policy: pass — no AI ban, AI-assisted course
- Newcomer signal (preferred): pass — good first issue/docs/tier-1 labels, relevant files listed

A clean fit for the profile: a bounded docs/config mismatch across two files, reproducible in minutes, with no competing PR.

```json
{
  "item": "https://github.com/codepath/pathreview-ai301-fa26-s3/issues/73",
  "checks": [
    {"name": "Maintainer alive", "grade": "pass", "evidence": "Human default-branch commits by Aburke225 through 2026-09-16, within 365 days of the 2026-09-27 capture."},
    {"name": "Repository in use", "grade": "pass", "evidence": "Not archived; last push 2026-09-16, within 365 days."},
    {"name": "Newcomer-sized scope", "grade": "pass", "evidence": "Bounded: 'Make the two files agree' on OPENROUTER_API_KEY/LLM_PROVIDER across README.md and .env.example."},
    {"name": "Direction is settled enough to start", "grade": "pass", "evidence": "Body prescribes the desired outcome; thread shows no design dispute."},
    {"name": "Nobody actively owns it", "grade": "pass", "evidence": "No assignee and no open linked PR; only student claim comments, which the house rule neutralizes."},
    {"name": "Contribution policy allows the workflow", "grade": "pass", "evidence": "docs/CONTRIBUTING.md welcomes contributions with no AI ban; AI-assisted course."},
    {"name": "Newcomer signal", "grade": "pass", "evidence": "Labels good first issue/docs/tier-1; relevant files listed in body."}
  ],
  "verdict": "accept"
}
```

---

## Eval iterations

Quote source text directly in each field below. Paraphrase does not satisfy them.

**Run history**

`agreement: 16/20 scored items  (bar: 18/20: below the bar)`

`agreement: 1/4 scored items`

`agreement: 4/5 scored items`

`agreement: 18/20 scored items  (bar: 18/20: PASS)`

**Issue analysis**

`issue-15  reject  accept   NO     graded accept`

My rubric decided `accept`, while the gold label was `reject`. I treated the requested outcome as finite and bounded, but my rubric did not weigh the long unresolved design history strongly enough. Because of that, the settled-direction check still allowed the issue even though the gold label treated it as unsuitable for a first issue.

**Check rationale**

> `Direction is settled enough to start | Issue body and especially the comment thread and prior-attempt context | Pass if a contributor can begin the requested work without first resolving a disputed product or design decision. Fail when the thread shows sustained unresolved debate over the desired behavior or architecture, multiple incompatible approaches with no maintainer decision, or prior implementation attempts that stalled because the design direction remained unsettled. Age alone, abandoned work alone, multiple implementation steps, named causes, or optional suggestions do not fail this check. | required`

I separated this from the general scope check because the earlier scope wording was rejecting valid bounded issues when they contained several edits, causes, or suggestions. This check focuses specifically on whether the direction is settled enough to begin.

**Trade-offs**

The targeted run after that change showed:

`issue-01  accept  accept   yes`

`issue-05  reject  reject   yes`

`issue-19  accept  accept   yes`

`issue-20  reject  reject   yes`

The trade-off is that `issue-15` still remained a false accept. I kept the revised check because it corrected the overly strict behavior on valid bounded issues, preserved the reject canaries, and the final complete run reached 18/20.

---

## Selection rationale

Graded on whether all three are answered, in your own words. Not on how good the
reasoning is, and not on length — a short honest answer to each earns the full marks.
This is also the basis for the claim comment you write in Unit 2.

**Selection rationale**

1. I chose issue #73 because it is a small documentation/configuration mismatch between `README.md` and `.env.example`. It only involves two named files, is estimated at 1–2 hours, and fits my experience with configuration and debugging while also fitting the time I have available.

2. The verdict correctly identified that the issue is bounded, has a clear outcome, has no assignee or open PR, and has good-first-issue signals. I also weighed that a two-file documentation/configuration issue should be faster for me to understand and reproduce than the runtime Python bugs I compared it against.

3. I expect claiming it to be straightforward because the requested work is specific and there is no competing open PR. I still need to post my own claim in Unit 2 before reproducing it.

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/issue-select/`.
