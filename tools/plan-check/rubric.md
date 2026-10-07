# Rubric: is this plan ready to post and build from?

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Diagnosis grounding | Read the Candidate plan's stated cause against the Issue and Repro evidence, including the reproduced steps and expected/actual behavior. | Passes if the diagnosis explains the reproduced behavior and is not contradicted by the reproduction evidence. If the cause is still uncertain, the plan must say so instead of presenting an unsupported cause as fact. | required |
| Scope control | Read the Candidate plan's scope, files/components, and stated exclusions against the diagnosis, Issue, and Repro evidence. | Passes if the proposed work is a bounded change aimed at the supported cause, identifies the files or components it will change, and avoids unrelated work or scope creep. | required |
| Executable approach | Read the Candidate plan's proposed change and implementation approach against the Repo facts and the evidence supporting the diagnosis. | Passes if another developer could begin the work without having to invent the core approach, including where the change happens and what behavior or code path will change. | required |
| Verification | Read the Candidate plan's test plan against the Repro evidence's steps and expected/actual behavior. | Passes if the planned checks exercise the reported problem and state an observable result that would show the fix worked. The verification should use an automated regression test when appropriate and may include manual checks. | required |
| Thread and conventions | Read the Candidate plan comment against the Thread highlights, Repo facts and contribution policy, and the Candidate plan itself. | Passes if the comment matches the plan and evidence, responds to relevant maintainer or thread guidance, and follows the repository's stated contribution and disclosure conventions. | required |

## Verdict rule

Accept (ready) only if every required check passes. A fail on any required check means reject (hold). An unclear grade on a required check also counts as a fail and means reject (hold). Preferred checks, if added later, never change the final verdict.
