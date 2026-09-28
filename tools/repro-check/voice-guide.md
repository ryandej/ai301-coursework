# Voice guide: how I talk upstream

## Who I am in threads

I am a student contributor working through the issue by reproducing the reported behavior before attempting a fix. I write comments that are specific to what I actually tested and keep claims limited to evidence I can show. Readers should be able to tell what I am going to do, what I ran, and what happened without guessing.

## Rules I write by

### Rule: Promise the investigation, not the result

When claiming an issue, I say what I am going to reproduce or investigate. I do not imply that I already confirmed the bug or promise a fix before doing the work.

- Wrong: "I confirmed this bug and will have a fix up tonight."
- Right: "I'd like to work on this issue. I'll reproduce the reported behavior and post what I observe."

### Rule: Name the actual issue behavior

I refer to the concrete behavior from the issue instead of using generic phrases that could fit any bug.

- Wrong: "I'll investigate this issue and report back."
- Right: "I'll check the mismatch between the README API-key instructions and `.env.example` and post the reproduction results."

### Rule: Separate observation from interpretation

I state what the command, file, log, or screenshot showed before saying what I think it means.

- Wrong: "The configuration is definitely broken."
- Right: "The README names one API-key variable while `.env.example` names a different one, so the setup instructions do not currently agree."

### Rule: Do not overclaim a reproduction

I use "reproduced" only when my evidence shows the behavior described by the issue. If my result differs, I say that directly.

- Wrong: "Reproduced" when the only evidence is a different error.
- Right: "I could not reproduce the reported behavior in this environment; the command instead returned the output shown below."

### Rule: Include the evidence a stranger needs

I include the relevant environment, steps, and observed result rather than expecting readers to trust a summary.

- Wrong: "Confirmed, same problem here."
- Right: "On Python 3.x, after following these setup steps and running this command, I observed the following output: ..."

## Things I never post

- A promise that I will finish a fix by a particular date or time.
- A claim that I reproduced something when the evidence shows a different behavior.
- "Same as above" or a piggyback reproduction without my own steps and evidence.
- Generic claim comments that do not identify the issue I am actually investigating.
- Claims that hide a material environment difference or required AI-assistance disclosure.
