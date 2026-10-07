# Evidence guide: where evidence lives in a plan package

## Diagnosis and grounding

**Where it lives**
- Eval package: read the Candidate plan's stated cause against the Issue and Repro evidence.
- Live mode: read the diagnosis in `plan.md` against the GitHub issue and the reproduction comment posted in Unit 2.

**What good looks like**
The stated cause explains the behavior the reproduction actually shows and is not contradicted by it. If the evidence does not establish a cause, the plan should state that uncertainty instead of presenting a guess as fact.

## Scope

**Where it lives**
- Eval package: read the Candidate plan's change, files/components, in-scope work, and stated exclusions. Compare them with the Issue, Repro evidence, and supported diagnosis.
- Live mode: read the scope and files-to-change sections of `plan.md` against the reproduced issue and the repository.

**What good looks like**
The plan describes one bounded change aimed at the supported problem, identifies the files or components involved, and makes clear what related work is not included. It does not expand into unrelated cleanup or broader rewrites.

## Executability

**Where it lives**
- Eval package: read the Candidate plan's implementation approach and named files/components, then use Repo facts for repository-specific context.
- Live mode: read the approach in `plan.md` and confirm the named files, components, and code paths exist in the repository.

**What good looks like**
Another developer could begin implementing the plan without having to invent the core approach. The plan identifies where the change happens and what behavior or code path will be changed.

## Test plan

**Where it lives**
- Eval package: read the Candidate plan's test instructions against the steps, expected behavior, and actual behavior in Repro evidence.
- Live mode: read the test plan in `plan.md` against the Unit 2 reproduction steps and evidence.

**What good looks like**
The test exercises the reported problem and states an observable result that would show the fix worked. It should reuse the reproduction when possible and include an automated regression test when appropriate.

## Honesty

**Where it lives**
- Eval package: read the Candidate plan for risks, unknowns, assumptions, or uncertainty. If deviations are provided, compare them with the original plan.
- Live mode: read the risks and unknowns in `plan.md` and, after implementation, the `## Deviations` section.

**What good looks like**
Uncertain or unverified claims are identified as such rather than stated as facts. If the implementation differs from the plan, the deviation is recorded clearly with what changed and why.

## Comms

**Where it lives**
- Eval package: read the Candidate plan comment against the Candidate plan, Thread highlights, and Repo facts, including contribution-policy or disclosure requirements.
- Live mode: read `comment.md` against the GitHub issue thread, the posted reproduction, repository contribution documentation, and `plan.md`.

**What good looks like**
The comment accurately represents the plan, addresses relevant maintainer or thread guidance, and follows the repository's stated contribution conventions. It should be specific to the issue rather than generic boilerplate and should disclose AI assistance when the repository requires it.
