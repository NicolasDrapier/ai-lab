---
name: grill-me
description: Interview the researcher about their AI project until the paper is fully specified, then write .ai-lab/brief.md. Use before /write-paper, or when the user wants to start or re-scope a paper.
---

# Grill me

You interview the researcher so the writing team knows exactly what paper to write. Output: `.ai-lab/brief.md`.

## Before asking anything

Explore the project: README, code, configs, result files (CSV, JSON, logs, `wandb/`, `runs/`, notebooks), `template/`. Use what you find to propose answers, so the researcher confirms instead of typing from scratch. If `.ai-lab/brief.md` already exists, read it and only ask about what is missing or what the user wants to change.

## Interview

Ask **one question at a time**, with your proposed answer when you have one. Push back on vague answers ("better results" → better on what metric, against what, by how much?). Cover:

1. Venue and page limit (check `template/` for hints).
2. The contribution in one sentence.
3. The main claims (2–4), each testable.
4. Where the results are in the repo, and which runs are the final ones.
5. Baselines and why they are the right ones.
6. Figures and tables the researcher expects (you can propose some).
7. Key references that must be cited.
8. Known limitations and negative results.
9. Anything else (anonymity, title ideas, audience).

Stop when every item has a concrete answer. Do not ask more than needed.

## Write the brief

Create `.ai-lab/brief.md`:

    # Brief
    ## Venue
    ## Page limit
    ## Contribution
    ## Claims
    1. ...
    ## Results location
    - `<path>` — <what it contains>
    ## Baselines
    ## Expected figures and tables
    ## Key references
    ## Limitations
    ## Notes

Show it to the researcher and ask for validation. Apply corrections. When approved, tell them the next step: put the venue's LaTeX template in `template/` (if not there yet) and run `/write-paper`.
