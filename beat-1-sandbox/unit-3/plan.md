# Plan for issue #73

## Diagnosis

The issue is a configuration-documentation mismatch between `README.md` and `.env.example`.

My reproduction showed:

> `README.md` line 24 says:
>
> `# Configure environment (add your OPENROUTER_API_KEY to .env)`

but `.env.example` currently says:

> `# Options: "mock" (default, no API key needed), "openai"`
>
> `LLM_PROVIDER=mock`

and does not include `OPENROUTER_API_KEY`.

`core/config.py` already defines:

> `openrouter_api_key: str = Field(default="")`

and `docs/SETUP.md` also tells users to set `OPENROUTER_API_KEY`. The mismatch is therefore in the example environment file rather than the existing README/setup instructions.

## Scope

### In scope

- Update `.env.example` so its LLM provider options include `openrouter`.
- Add an `OPENROUTER_API_KEY` placeholder to `.env.example`.
- Keep the existing `mock` default and existing OpenAI configuration intact.

### Out of scope

- Changes to `README.md` or `docs/SETUP.md`, because both already direct users toward the OpenRouter configuration.
- Changes to `core/config.py` or other runtime provider logic.
- Unrelated environment-variable or documentation cleanup.

## Files to change

- `.env.example`

## Approach

1. Update the LLM provider comment in `.env.example` so it lists `openrouter` along with the existing `mock` and `openai` options.
2. Add an `OPENROUTER_API_KEY` placeholder alongside the existing LLM API-key configuration.
3. Preserve `LLM_PROVIDER=mock` as the default and leave `OPENAI_API_KEY` unchanged.
4. Review the diff to make sure no unrelated configuration was changed.

## Test plan

Re-run the Unit 2 reproduction checks after the change:

```bash
grep -nE 'OPENROUTER_API_KEY|LLM_PROVIDER|openrouter|openai|mock' README.md
grep -nE 'OPENROUTER_API_KEY|LLM_PROVIDER|openrouter|openai|mock' .env.example
grep -nE 'OPENROUTER_API_KEY|LLM_PROVIDER|openrouter|openai|mock' core/config.py
```

Expected after the fix:

- `README.md` still instructs users to configure `OPENROUTER_API_KEY`.
- `.env.example` lists `openrouter` as an `LLM_PROVIDER` option.
- `.env.example` includes an `OPENROUTER_API_KEY` placeholder.
- `LLM_PROVIDER=mock` remains the default.
- `core/config.py` still contains the existing OpenRouter configuration fields.

Also run:

```bash
git diff --check
```

Expected result: no whitespace errors.

## Risks and unknowns

The issue is limited to making the setup/configuration examples agree. I have not verified broader OpenRouter runtime behavior, so this plan does not make or claim any runtime-provider changes.

The exact placeholder text for `OPENROUTER_API_KEY` is not specified by the issue, so I will follow the style already used for `OPENAI_API_KEY` in `.env.example`.

## Deviations

The implementation matched the plan. No deviations were needed.
