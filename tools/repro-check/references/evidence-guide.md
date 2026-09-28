# Evidence guide: where proof lives in a reproduction package

## Environment

Where it lives: In eval packages, read the issue context and repo-facts block first, then the environment section of the repro report. In live mode, compare the draft report with the issue thread, repository setup documentation, dependency files, and the environment actually used.

What good looks like: The report records the environment details needed to interpret the result, such as operating system, runtime, relevant dependency/tool versions, or configuration when those details affect the issue. If the environment differs from the issue's stated target, the report says so rather than silently treating it as equivalent.

## Steps

Where it lives: In the repro report's setup and reproduction steps, including commands, file edits, configuration values, inputs, and starting state. In live mode, verify those steps against the repository's own setup documentation.

What good looks like: Another contributor can start from the stated state and execute the sequence without guessing a critical missing action. The steps reach the exact trigger being tested, not merely repository startup or a nearby workflow.

## Behavior shown

Where it lives: In terminal excerpts, logs, screenshots, generated files, HTTP responses, test output, or other artifacts included in the repro report. Read those artifacts against the behavior described in the issue.

What good looks like: The artifact visibly demonstrates the issue's target behavior or, for a cannot-reproduce result, demonstrates that the exact trigger was attempted and produced different behavior. Evidence of an adjacent error does not count as evidence of the reported issue.

## Honesty

Where it lives: Compare the report's stated result and conclusion with the artifacts and steps that precede it.

What good looks like: The wording stays within what the evidence proves. "Reproduced" is used only when the target behavior is actually shown; "could not reproduce" is acceptable when the attempted conditions and observed result are documented. Uncertainty or environment differences are stated instead of hidden.

## Comms

Where it lives: In the claim comment and repro comment, read alongside the issue thread, contribution documentation, templates, repo-facts block, and any repository AI-assistance policy.

What good looks like: The claim identifies the specific issue and promises only the investigation/reproduction work being started. The repro comment reports what was actually observed and includes enough proof to support it. Always read the repository's AI policy. For eval packages, treat the work as AI-assisted when applying a policy that requires AI disclosure. If that policy requires disclosure, the candidate comment must explicitly provide it; silence is a failure even when every reproduction check passes. If the repository does not require disclosure, do not invent that requirement.
