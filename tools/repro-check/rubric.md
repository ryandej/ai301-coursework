# Rubric: is this reproduction package ready to post?

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Environment matches target | Repro report environment record read against the issue context and repo-facts block | Pass if the report identifies the environment needed to interpret the result, including relevant OS/runtime/tool or dependency versions when they affect the issue, and either matches the issue's stated target or explicitly calls out a meaningful difference. | required |
| Steps are reproducible | Repro report steps, starting state, commands/actions, and setup requirements | Pass if a stranger with the repository can follow the stated setup and actions from a defined starting state to the attempted trigger without having to invent a missing critical step, input, file, configuration value, or command. | required |
| Evidence shows the issue behavior | Repro report artifacts such as terminal output, logs, screenshots, file contents, or other observable results read against the issue description | Pass if the evidence demonstrates the behavior the issue actually describes, rather than only an adjacent symptom. For a cannot-reproduce result, pass if the evidence clearly shows the attempted trigger and the observed non-failure or different behavior. | required |
| Outcome matches evidence | Repro report conclusion and any claim about reproduced/cannot reproduce read against the supplied artifacts | Pass if the stated outcome is no stronger than the evidence supports. An evidenced cannot-reproduce passes; a confident reproduction claim fails when the artifact does not show the target behavior. | required |
| Repository conventions followed | Claim comment and repro report read against repo-facts, contribution instructions, comment templates, and any AI-assistance policy | First read the repository's stated contribution and AI policy. If that policy requires disclosure of AI use, treat an eval package as AI-assisted and fail this check unless the candidate comment explicitly includes the required disclosure; do not infer disclosure from course context or from the quality of the work. If the repository permits AI assistance without requiring disclosure, absence of disclosure does not fail. Also fail comments that violate another explicit repository convention or claim a fix, completion date, or work that has not been done. | required |
| Communication is issue-specific | Claim comment and repro report read against the issue title/body and thread | Pass if the writing names the specific issue behavior or investigation being performed and avoids generic boilerplate that could be pasted unchanged onto an unrelated issue. | preferred |

## Verdict rule

Accept only if every required check passes. A failed or unclear required check means reject/hold. Preferred checks may improve the assessment but never change the binary verdict.
