# Procedure: how this skill grades a plan package

## Read order

1. Read the Issue first. Record the reported problem, expected behavior, and any constraints or maintainer guidance.
2. Read the Repro evidence next. Record the reproduced steps, observed behavior, and any evidence that supports or rules out possible causes.
3. Read the Candidate plan. Record its diagnosis, scope, files or components to change, implementation approach, test plan, risks, and unknowns.
4. Read the Candidate plan comment, Thread highlights, and Repo facts/contribution policy last. Record any maintainer requests, repository conventions, or disclosure requirements that the plan and comment must follow.
5. Do not grade any check until the Issue, Repro evidence, and Candidate plan have all been read.

## Evidence gathering

1. For Diagnosis grounding, compare the Candidate plan's stated cause with the Issue and Repro evidence. Record whether the reproduced behavior supports, contradicts, or does not establish the proposed cause.
2. For Scope control, record what the plan says it will change, the files or components named, what it excludes, and whether those changes stay focused on the supported cause.
3. For Executable approach, record the concrete implementation steps, code path or component involved, and whether Repo facts provide enough information for another developer to begin the work.
4. For Verification, compare the test plan with the original Repro steps and expected/actual behavior. Record what observable result the plan expects after the fix and whether the reported problem is directly exercised.
5. For Thread and conventions, compare the Candidate plan comment with the Candidate plan, Thread highlights, Repo facts, and contribution policy. Record any relevant maintainer guidance, repository conventions, or disclosure requirements and whether the comment follows them.
6. Use only evidence present in the package or, in live mode, the sources allowed by the evidence guide. Do not invent missing evidence.

## Check execution

1. Grade the checks in this order: Diagnosis grounding, Scope control, Executable approach, Verification, then Thread and conventions.
2. For each check, apply the exact pass condition from rubric.md to the evidence gathered for that check.
3. Grade a check pass only when the available evidence satisfies the pass condition.
4. Grade a check fail when the evidence contradicts the pass condition or clearly shows the requirement is not met.
5. Grade a check unclear when the evidence needed to decide is genuinely missing or ambiguous. Do not assume missing details are true.
6. A specific or detailed plan does not automatically pass. The evidence still has to support what the plan claims.
7. Once the relevant evidence for a check has been gathered, grade that check from those recorded facts rather than reinterpreting unrelated parts of the package.

## Verdict assembly

1. Apply the verdict rule in rubric.md after every check has been graded.
2. Accept the plan only if every required check passes.
3. Reject the plan if any required check fails.
4. Treat unclear on a required check as a fail, so the final verdict is reject.
5. Preferred checks, if any are added later, do not change the final verdict.
6. In the output, give the grade and short evidence-based reason for every check.
7. For a reject verdict, quote or identify the evidence for at least one required check that caused the rejection.
8. End with the final verdict required by the skill: accept for ready or reject for hold.
