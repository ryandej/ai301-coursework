# Procedure: how this tool grades a PR package

## Read order

1. Read the final plan first. Record the reported problem, planned scope, files or components to change, implementation approach, test plan, risks, and any `## Deviations`.
2. Read the issue and relevant issue-thread context next. Record the reported behavior, expected outcome, maintainer guidance, and any constraints that apply to the change.
3. Read the complete branch diff after the plan. Record every changed file and the substantive purpose of each hunk. Compare the diff with the plan before reading the PR description so the description does not bias the implementation review.
4. Read the test evidence next. Record the bug-specific reproduction result, before/after behavior when available, regression tests in the diff that directly assert the planned behavior, and the reported outcomes of repository-required checks.
5. Read the PR title and description after the underlying evidence. Record its scope claims, issue reference, testing claims, changelog or checklist statements, disclosures, and any stated shortfall or deviation.
6. Read the applicable repository standards last: the PR template, `docs/CONTRIBUTING.md`, relevant issue-thread guidance, and any stated AI-use or disclosure policy.
7. Do not grade a rubric check until the evidence needed for that check has been read.

## Evidence gathering

1. For Plan fidelity, list each substantive changed file and hunk from the diff. Match it to the final plan's scope, implementation steps, or `## Deviations`.
2. Record any planned work that does not appear in the diff. Determine whether it was explicitly deferred or otherwise explained in the plan or deviations and accurately disclosed in the PR description.
3. Compare the PR description's claims about implementation and scope with the actual diff. Record any silent extra work, silent omission, or fidelity claim contradicted by the branch.
4. For Test evidence, identify the reported bug or behavior the plan says must be verified. Record the strongest evidence showing that behavior was actually exercised after the change.
5. Bug-specific evidence may include concrete before/after output, a specific reproduced result, or a regression test in the diff that directly asserts the expected behavior. Do not require a full raw transcript for every secondary test when the package gives a specific result that can be evaluated.
6. Distinguish bug-specific evidence from generic statements. Claims such as "tested locally," "works," or "all tests pass" do not by themselves prove that the reported failure mode was exercised.
7. Record any material controls or repository-required checks named by the plan, PR template, or contribution rules. In live mode, use the actual captured command output in `test_evidence.md`. In eval mode, use the evidence supplied by the bundle and do not demand evidence the bundle format does not require.
8. A failing check still counts as evidence when the real failure or specific outcome is honestly disclosed. Do not convert an honest failure into a pass; record what it proves.
9. For Diff quality, inspect every changed hunk for debugging leftovers, commented-out experiments, dead code, unrelated cleanup, avoidable formatting or import churn, or other changes that do not contribute to the planned fix or a recorded deviation.
10. For Standards and comms, record the substance of the repository's stated requirements: issue-linking, requested template information, changelog or checklist expectations, contribution rules, maintainer direction, and AI-use disclosure where required.
11. Check whether the PR satisfies those substantive requirements. Do not fail a PR merely because its wording or section formatting differs from the template unless the repository explicitly requires that exact format.
12. In eval mode, gather evidence only from the package bundle. In live mode, use the files and repository sources named by `SKILL.md` and `references/evidence-guide.md`. Never invent missing evidence.

## Check execution

1. Grade the checks in rubric order: Plan fidelity, Test evidence, Diff quality, then Standards and comms.
2. For each check, apply the exact pass condition in `rubric.md` to the evidence gathered for that check.
3. Grade a check `pass` only when the evidence satisfies its pass condition.
4. Grade a check `fail` when the evidence contradicts the pass condition or clearly shows that the requirement was not met.
5. Grade a check `unclear` only when the evidence needed to decide is genuinely missing or ambiguous. Do not assume an unsupported claim is true.
6. Do not fail Test evidence merely because every secondary command lacks a full transcript. Decide whether the reported problem itself was specifically exercised and whether material required checks are accounted for.
7. Do not pass Test evidence when the package gives only generic testing language, exercises the wrong behavior, tests only a control path while omitting the reported failure mode, or omits a required material check without disclosure.
8. An honestly disclosed shortfall or deviation does not automatically fail Plan fidelity or Standards and comms. Apply the rubric to whether the plan, diff, description, and evidence agree about what is actually being delivered.
9. Once the relevant evidence for a check has been gathered, grade that check from those recorded facts rather than reinterpreting unrelated parts of the package.
10. For every check, record one concise evidence line naming the fact, quote, diff finding, concrete test result, or missing evidence that decided the grade.

## Verdict assembly

1. Apply the verdict rule in `rubric.md` after every check has been graded.
2. Return `accept` only if every required check passes.
3. Return `reject` if any required check fails.
4. Treat `unclear` on a required check as a failure.
5. Preferred checks, if any are added later, never change the final verdict.
6. In the readable summary, report every check's grade with its evidence-based reason.
7. If the verdict is `reject`, identify the first failing required check in rubric order as the primary deciding failure and also report any additional failing checks.
8. End with the exact fenced JSON block required by `SKILL.md`, using only `accept` or `reject`, and place nothing after it.
