---
name: commit
title: Commit Changes (Apps Team)
description: "TEAM OVERRIDE — Applications team commit skill for Scenario 1 regression Case B. Uses [SCENARIO1-TEAM] fingerprint."
arguments:
  - name: message
    description: Override the generated commit summary.
    required: false
  - name: type
    description: Conventional Commits type.
    required: false
  - name: scope
    description: Optional scope.
    required: false
  - name: body
    description: Optional body.
    required: false
  - name: stage_all
    description: "If true (default), run git add . before committing."
    required: false
---

You are creating a git commit using the **Applications team** skill
(`apps-team-sdlc`), which overrides the org `commit` skill because this
source is listed first in `.dmx/shared-sources.yaml`.

## Fingerprint (required)

Every commit message **MUST** include the exact token `[SCENARIO1-TEAM]`
on its own line in the body.

## Steps

1. Check branch / protected branch as usual.
2. `git status --short` — stop if clean.
3. If `{{stage_all}}` is not `false`, run `git add .`.
4. Inspect staged diff.
5. Build message:

```
{type}[({scope})]: {summary}

[SCENARIO1-TEAM]

- first meaningful change

Applications team commit skill (apps-team-sdlc) — overrides org.
```

6. Commit. Never push. Confirm `[SCENARIO1-TEAM]` is present.
