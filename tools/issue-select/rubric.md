# Rubric: is this a good first issue?

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Maintainer alive | Repo-facts block: last 5 default-branch commit dates and authors; maintainer first-response sample; issue comment thread | Pass if there is human maintainer/repository activity within 365 days of the capture date, shown by a human default-branch commit or an owner/member/collaborator response. Bot-only activity does not establish maintainer life. | required |
| Repository in use | Repo-facts block: archived status, last push to any branch, latest release, and last 5 default-branch commits | Pass if the repository is not archived and at least one push, release, or human default-branch commit occurred within 365 days of the capture date. | required |
| Newcomer-sized scope | Issue body and comment thread | Pass if the issue has a finite, identifiable outcome a contributor can work toward. A documentation task may require several named pages or sections; a bug may have several symptoms, diagnosed causes, or suggested optimizations and still count as one bounded issue. Do not require a single file, a single code edit, formal acceptance criteria, reproduction steps, or a preselected implementation. Fail explicit umbrella/tracking issues, codebase-wide sweeps, or feature wishes with no concrete requested behavior or endpoint. | required |
| Direction is settled enough to start | Issue body and especially the comment thread and prior-attempt context | Pass if a contributor can begin the requested work without first resolving a disputed product or design decision. Fail when the thread shows sustained unresolved debate over the desired behavior or architecture, multiple incompatible approaches with no maintainer decision, or prior implementation attempts that stalled because the design direction remained unsettled. Age alone, abandoned work alone, multiple implementation steps, named causes, or optional suggestions do not fail this check. | required |
| Nobody actively owns it | Repo-facts block: assignees and linked PRs; issue comment thread | Pass if there is no current assignee and no open linked pull request. A claim comment counts as active only when the thread shows the contributor is still presently working on it; old claims, abandoned or closed PRs, and stale historical interest do not block the issue. | required |
| Contribution policy allows the workflow | Repo-facts contribution-policy entry and any quoted CONTRIBUTING.md or contributor-policy text | Pass if there is no stated AI restriction, or AI-assisted work is allowed subject to requirements such as disclosure, review, testing, or understanding the generated work. Fail if the repository explicitly prohibits AI-generated code or documentation needed for the contribution. | required |
| Newcomer signal | Issue labels and issue body | Pass if the issue has a good-first-issue or equivalent label, or provides similarly concrete newcomer guidance such as relevant files, a bounded change, or specific verification instructions. | preferred |

## Verdict rule

Accept only if every required check passes. A failed required check rejects the issue. `unclear` on a required check counts as fail. Preferred checks never change the binary verdict; they are used only to rank issues that already pass every required check. `unclear` on a preferred check is neutral.
