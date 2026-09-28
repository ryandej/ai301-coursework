# Unit 2 — Claim and Reproduce

Path: `beat-1-sandbox/unit-2/reproduction.md`

Record of your claim and reproduction on the issue you chose in Unit 1, and of the
evaluation runs that produced `eval-run.txt`. This file is graded at the path above; a copy
kept anywhere else in the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the wrong
label is not graded.

---

## Your identity upstream

**GitHub username**

ryandej

---

## Posted upstream

**Claim comment**

https://github.com/codepath/pathreview-ai301-fa26-s3/issues/73#issuecomment-5864635899

I'd like to work on #73. I'll reproduce the mismatch between the README setup instructions and `.env.example`, check the relevant configuration behavior, and post a repro report with what I observe.

**Reproduction comment**

https://github.com/codepath/pathreview-ai301-fa26-s3/issues/73#issuecomment-5864699144

Reproduction report for #73

Environment
- OS: Ubuntu/Linux 6.5.0-1024-oem x86_64
- Python: 3.10.12
- Repository commit: 2f4e82f52efbcfcc57d65b3fa5348672163ca088
- Date reproduced: 2026-09-27

Steps
1. Clone the Path Review repository and check out commit 2f4e82f52efbcfcc57d65b3fa5348672163ca088.
2. From the repository root, run:
   `grep -nE 'OPENROUTER_API_KEY|LLM_PROVIDER|openrouter|openai|mock' README.md`
3. Run:
   `grep -nE 'OPENROUTER_API_KEY|LLM_PROVIDER|openrouter|openai|mock' .env.example`
4. Run:
   `grep -nE 'OPENROUTER_API_KEY|LLM_PROVIDER|openrouter|openai|mock' core/config.py`

Observed

README.md line 24 says:

`# Configure environment (add your OPENROUTER_API_KEY to .env)`

However, .env.example lines 17-18 say:

`# Options: "mock" (default, no API key needed), "openai"`  
`LLM_PROVIDER=mock`

There is no `OPENROUTER_API_KEY` entry in `.env.example` and its `LLM_PROVIDER` comment does not list `openrouter`.

core/config.py lines 18-22 define:

`llm_provider: str = Field(default="mock")`  
`openai_api_key: str = Field(default="")`  
`openrouter_api_key: str = Field(default="")`  
`openrouter_base_url: str = Field(default="https://openrouter.ai/api/v1")`  
`openrouter_model: str = Field(default="google/gemma-3-27b-it:free")`

Expected

The setup documentation and `.env.example` should agree about the supported OpenRouter configuration. If README.md instructs users to configure `OPENROUTER_API_KEY`, `.env.example` should expose the corresponding variable and accurately describe the supported `LLM_PROVIDER` options.

Result

Reproduced. README.md instructs users to configure OpenRouter, while `.env.example` omits the OpenRouter key and does not list `openrouter` as an `LLM_PROVIDER` option. core/config.py confirms that OpenRouter configuration is implemented.

## Eval iterations

Answer all four sections. Quote source text directly; paraphrase does not satisfy these
fields.

**Run history**

`agreement: 19/20 scored items  (bar: 18/20: below the bar; category floor unmet: no match in disclosure)`

`agreement: 3/3 scored items`

`agreement: 19/20 scored items  (bar: 18/20: PASS)`

**Package analysis**

For `pkg-20`, my first full run recorded:

`pkg-20  reject  accept   NO     graded accept`

My rubric decided `accept`, while the gold label was `reject`. The original repository-conventions check recognized that required AI-use disclosure should be followed, but it did not explicitly tell the grader to treat the eval package as AI-assisted and require the disclosure to appear in the candidate comment. Because the rest of the package passed, the rubric incorrectly accepted it despite the missing required disclosure.

**Check rationale**

My current rubric says:

> `Repository conventions followed | Claim comment and repro report read against repo-facts, contribution instructions, comment templates, and any AI-assistance policy | First read the repository's stated contribution and AI policy. If that policy requires disclosure of AI use, treat an eval package as AI-assisted and fail this check unless the candidate comment explicitly includes the required disclosure; do not infer disclosure from course context or from the quality of the work. If the repository permits AI assistance without requiring disclosure, absence of disclosure does not fail. Also fail comments that violate another explicit repository convention or claim a fix, completion date, or work that has not been done. | required`

I revised the check after the first full run missed the disclosure category. The updated wording makes the evidence threshold explicit: when a repository requires AI disclosure, the candidate comment itself must contain that disclosure. It also avoids inventing a disclosure requirement when the repository does not require one.

**Trade-offs**

After tightening the disclosure check, I re-ran three packages as canaries:

`pkg-05  accept  accept   yes`

`pkg-07  accept  accept   yes`

`pkg-20  reject  reject   yes`

This showed that the change correctly rejected the missing-disclosure case without incorrectly rejecting cases where disclosure was provided or was not required. The final complete run then reached 19/20 and passed every category.

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/repro-check/`.
