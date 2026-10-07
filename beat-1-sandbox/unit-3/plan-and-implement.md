# Unit 3 — Plan and Build

## Posted upstream

**GitHub username**

ryandej

**Plan comment**

https://github.com/codepath/pathreview-ai301-fa26-s3/issues/73#issuecomment-6031809420

I reproduced the mismatch from #73 and traced it to `.env.example`.

`README.md` tells users to add `OPENROUTER_API_KEY` to `.env`, and `docs/SETUP.md` gives the same instruction. `core/config.py` also already defines `openrouter_api_key`.

However, `.env.example` currently only lists `mock` and `openai` as provider options and does not include an `OPENROUTER_API_KEY` entry.

My plan is to update `.env.example` only:

- add `openrouter` to the documented `LLM_PROVIDER` options
- add an `OPENROUTER_API_KEY` placeholder
- keep `LLM_PROVIDER=mock` as the default
- leave the existing OpenAI configuration unchanged

I do not plan to change `README.md`, `docs/SETUP.md`, or runtime provider code because the evidence I reproduced points to the example environment file as the inconsistency.

After the change, I’ll re-run the same grep checks from my reproduction to confirm the README, `.env.example`, and `core/config.py` agree on the OpenRouter configuration, and I’ll run `git diff --check` for whitespace issues.

---

## Your branch

**Branch**

fix/73-openrouter-env-example

**Evidence**

### Before

```bash
grep -nE 'OPENROUTER_API_KEY|LLM_PROVIDER|openrouter|openai|mock' README.md
```

Output:

```text
24:# Configure environment (add your OPENROUTER_API_KEY to .env)
```

```bash
grep -nE 'OPENROUTER_API_KEY|LLM_PROVIDER|openrouter|openai|mock' .env.example
```

Output:

```text
17:# Options: "mock" (default, no API key needed), "openai"
18:LLM_PROVIDER=mock
```

```bash
grep -nE 'OPENROUTER_API_KEY|LLM_PROVIDER|openrouter|openai|mock' core/config.py
```

Output:

```text
18:    llm_provider: str = Field(default="mock")
19:    openai_api_key: str = Field(default="")
20:    openrouter_api_key: str = Field(default="")
21:    openrouter_base_url: str = Field(default="https://openrouter.ai/api/v1")
22:    openrouter_model: str = Field(default="google/gemma-3-27b-it:free")
```

### After

```bash
grep -nE 'OPENROUTER_API_KEY|LLM_PROVIDER|openrouter|openai|mock' README.md
```

Output:

```text
24:# Configure environment (add your OPENROUTER_API_KEY to .env)
```

```bash
grep -nE 'OPENROUTER_API_KEY|LLM_PROVIDER|openrouter|openai|mock' .env.example
```

Output:

```text
17:# Options: "mock" (default, no API key needed), "openai", "openrouter"
18:LLM_PROVIDER=mock
20:OPENROUTER_API_KEY=your-openrouter-key-here
```

```bash
grep -nE 'OPENROUTER_API_KEY|LLM_PROVIDER|openrouter|openai|mock' core/config.py
```

Output:

```text
18:    llm_provider: str = Field(default="mock")
19:    openai_api_key: str = Field(default="")
20:    openrouter_api_key: str = Field(default="")
21:    openrouter_base_url: str = Field(default="https://openrouter.ai/api/v1")
22:    openrouter_model: str = Field(default="google/gemma-3-27b-it:free")
```

```bash
git diff --check
```

Output:

```text
```

`git diff --check` produced no output, indicating no whitespace errors.

## Eval iterations

**Run history**

Run 1: `20/20` scored items agreed with the gold labels.

Final harness result:

```text
categories: clear-accept 7/7  scope-creep 4/4  thread-convention 2/2  unbuildable 3/3  wrong-cause 4/4
agreement: 20/20 scored items  (bar: 18/20: PASS)
```

No additional eval runs were needed.

**Package analysis**

I reviewed `pkg-01`. My rubric returned **reject**, and the gold label was also **reject**.

The package's candidate plan says:

> "The `REQUEST_ITEM` tokenizer in `httpie/cli/requestitems.py` is the problem."

However, the reproduction evidence says:

> "`--debug` on the failing run shows the error is raised by argparse's `parse_args` while consuming positionals; the request items are never handed to HTTPie's item parser."

My Diagnosis grounding check therefore fails because the proposed cause is contradicted by the reproduction evidence. Since Diagnosis grounding is required, the final verdict is reject. This is the behavior I wanted from the rubric: a plan should not pass just because it states a specific cause if the reproduction points somewhere else.

**Check rationale**

One check in my uploaded `rubric.md` reads:

> **Diagnosis grounding** — Evidence: "Read the Candidate plan's stated cause against the Issue and Repro evidence, including the reproduced steps and expected/actual behavior." Pass condition: "Passes if the diagnosis explains the reproduced behavior and is not contradicted by the reproduction evidence. If the cause is still uncertain, the plan must say so instead of presenting an unsupported cause as fact." Weight: `required`.

I wrote the check this way because the sample rubric from the activity only required a plan to state what caused the bug. In `calib-03`, that allowed a specific-sounding diagnosis to pass even though the reproduction evidence did not support it. I wanted the check to require comparison with the reproduction evidence instead of rewarding a diagnosis simply for being present.

**Trade-offs**

This Diagnosis grounding check is intentionally conservative. A plan may identify the correct cause before the available reproduction evidence fully proves it, but this check can still return unclear or fail until the evidence supports the claim. I accept that trade-off because I would rather hold a plan for more evidence than approve a confident diagnosis that the reproduction contradicts. In the first full eval this did not create a scored false rejection: the run matched all 20 gold labels, so no rubric revision or retry was needed.
