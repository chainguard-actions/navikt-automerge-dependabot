<!-- markdownlint-disable -->

# Hardening Report: navikt--automerge-dependabot/v1.2.2

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **navikt--automerge-dependabot/v1.2.2** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The workflow file uses tag-based (mutable) refs instead of pinned 40-character commit SHAs for two actions. If the tag is moved or the upstream repository is compromised, the action could execute arbitrary code. Failing references:
- `uses: actions/checkout@v5` (line 12)
- `uses: actions/setup-node@v5` (line 13)

These should be pinned to their full SHA digests, e.g.:
- `uses: actions/checkout@<40-char-sha> # v5`
- `uses: actions/setup-node@<40-char-sha> # v5`

Locations:

- `.github/workflows/tests.yml:12`
- `.github/workflows/tests.yml:13`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned both mutable tag references in .github/workflows/tests.yml to their full commit SHAs: actions/checkout@v5 → fbc6f3992d24b796d5a048ff273f7fcc4a7b6c09 and actions/setup-node@v5 → a0853c24544627f65ddf259abe73b1d18a591444. Original tags preserved as inline comments for readability.

