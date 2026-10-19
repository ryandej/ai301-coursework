# Evidence guide: where evidence lives in a PR package

## Plan fidelity (harness category: silent-drift)

**Where it lives**

- **Eval mode:** compare the plan-context block's stated scope, files, implementation boundary, test plan, and any deviation notes with the candidate PR's unified diff. Also compare any fidelity claims in the candidate PR description with what the diff actually contains.
- **Live mode:** compare `plan.md`, including `## Deviations`, with the committed branch diff from `git diff main...HEAD`. Then compare the scope and implementation claims in `pr_draft.md` with both the plan and the diff.

**What good looks like**

Every substantive changed file and hunk is covered by the final plan or by an explicitly recorded deviation. The PR description accurately represents what the branch actually delivers.

Silent drift includes extra unplanned work, planned work silently missing from the diff, or a description that claims more or less than the diff shows. An honestly recorded deviation or shortfall may still be acceptable when the plan or deviations and the PR description clearly agree about what changed and why.

## Test evidence (harness category: not-tested)

**Where it lives**

- **Eval mode:** read the plan-context block's test plan and reproduction steps against the candidate PR's Test evidence section, testing claims in the description, and regression tests shown in the diff when they directly assert the planned behavior.
- **Live mode:** compare the test plan in `plan.md` and the original reproduction evidence with the commands and printed output in `test_evidence.md`. Also compare the Testing section of `pr_draft.md` with that evidence and with any regression tests added in the branch diff.

**What good looks like**

There is specific, observable evidence that the reported bug or behavior was actually exercised after the change and produced the planned outcome.

Good evidence can be concrete before/after output, a specific repro result, or an equivalent regression test that directly asserts the expected behavior. Every secondary command does not need a complete raw transcript when its result is specifically reported and the package gives enough evidence to evaluate what was tested.

Generic claims such as "tested locally," "works," or "all tests pass" are not enough by themselves. Testing only a control or unrelated path while never exercising the reported failure mode is also insufficient. Material controls and repository-required checks should be accounted for when the plan or repository requires them.

In live mode, use the actual command output captured in `test_evidence.md` for the repository's required checks. A failing check still counts as evidence when the failure and its output are honestly shown.

## Diff quality (harness category: unreviewable)

**Where it lives**

- **Eval mode:** inspect the candidate PR's unified diff and commit information for every changed file and substantive hunk.
- **Live mode:** inspect the complete committed branch diff from `git diff main...HEAD`. Use the commit list only as supporting context; grade the actual diff.

**What good looks like**

The intended fix is easy to identify and the diff contains only work needed for the planned change or a recorded deviation.

There are no leftover debug prints, commented-out experiments, dead code, unrelated cleanup, drive-by edits, or unnecessary formatting or import churn that obscures the change. A diff can be small or large and still be reviewable; the key question is whether the substantive changes belong to the planned work and unrelated debris is absent.

## Standards and comms (harness category: standards-wall)

**Where it lives**

- **Eval mode:** read the repo-facts block for the repository's PR-template asks, contribution instructions, issue-linking requirements, changelog or checklist requirements, and stated AI-use or disclosure policy. Compare those asks with the candidate PR title and description and any relevant maintainer guidance included in the bundle.
- **Live mode:** read `.github/PULL_REQUEST_TEMPLATE.md`, `docs/CONTRIBUTING.md`, the issue thread, and any other stated repository policy that applies to the PR. Compare those requirements with the title and description in `pr_draft.md`.

**What good looks like**

The PR substantively satisfies the repository's stated asks that apply to it. This can include identifying the issue, providing requested change-type or changelog information, accounting for required testing or contribution expectations, and disclosing AI use when required.

Exact template wording or formatting is not required unless the repository explicitly requires it. The deciding question is whether the required information is actually present and accurate.

Do not invent requirements the repository does not state, and do not treat generic boilerplate as satisfying a specific requirement when the repository asks for concrete information.
