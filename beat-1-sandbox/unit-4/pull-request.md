# Unit 4 — Test and Submit

Path: `beat-1-sandbox/unit-4/pull-request.md`

## Your pull request

**Pull request**

https://github.com/codepath/pathreview-ai301-fa26-s3/pull/257

**Branch**

`fix/73-openrouter-env-example`

## Eval iterations

**Run history**

1. Full run: `13/20`
2. Partial run (`pkg-02,pkg-05,pkg-04,pkg-01`): `4/4`
3. Partial run (`pkg-08,pkg-11,pkg-13,pkg-16,pkg-19,pkg-07,pkg-20,pkg-03,pkg-12`): `8/9`
4. Partial run (`pkg-16,pkg-03`): `2/2`
5. Final full run: `20/20`

Final recorded agreement:

> `agreement: 20/20 scored items  (bar: 18/20: PASS)`

**Package analysis**

I used `pkg-16`.

The final eval result was:

> `pkg-16  clear-accept    accept  accept   yes`

My rubric therefore decided `accept`, and the gold label was also `accept`.

The package's accepted plan explicitly said:

> "make the failure visible on the `image load` path without changing the start path's semantics."

It also stated:

> "Deliberately deferred, stated in the plan: the start-time loading path (multi-node, where a per-node failure may genuinely be non-fatal) keeps its current tolerant behavior"

The candidate PR matched that boundary and repeated it clearly:

> "Deliberately out of scope (recorded in the plan and discussed with @nirs on the thread): the start-time image loading path keeps its tolerant behavior"

My rubric initially rejected this package because it treated possible effects on the shared `DoLoadImages` code path as silent drift. That was too speculative. The package itself showed that the changed behavior was intentional, bounded, and consistent with the accepted plan, so the final rubric correctly accepted it.

**Check rationale**

The final Plan fidelity check in `rubric.md` reads:

> `| Plan fidelity | Read the branch diff's changed files and substantive hunks against the final plan's scope, implementation steps, and \`## Deviations\`. Also compare the PR description's claims with the plan and diff. | Passes if the substantive work shown in the diff stays within the plan or an explicitly recorded deviation, and the description accurately represents what the diff demonstrates. A planned item may be deferred without failing when the deferral is explicitly recorded in the plan or deviations and honestly disclosed in the description. Fail for demonstrated silent extra work, silently omitted planned work, or fidelity claims contradicted by the diff. Do not infer silent drift solely from hypothetical or transitive effects on callers or code paths that the package does not show; grade the behavior and changes evidenced in the package. | required |`

I revised this check after `pkg-16` was incorrectly rejected. The important addition was:

> "Do not infer silent drift solely from hypothetical or transitive effects on callers or code paths that the package does not show"

That keeps the check focused on demonstrated plan-versus-diff drift instead of rejecting a PR because of a possible downstream effect that the package does not actually show.

**Trade-offs**

The trade-off is that this version of Plan fidelity is less aggressive about inferring indirect effects. A real transitive behavior change could be missed when the package does not provide evidence of it. I accepted that trade-off because the skill is supposed to grade the supplied PR package, not invent unsupported failure modes.

I re-ran the relevant canary with:

> `--only pkg-16,pkg-03`

That run scored:

> `2/2`

This showed that the revision fixed the false rejection on the clear-accept `pkg-16` while still rejecting the silent-drift package `pkg-03`.
