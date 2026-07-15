# Memi Design CI Proof

This maintained fork demonstrates deterministic agent design CI on Vercel's
Chatbot template without changing its runtime, model providers, database, or
deployment path.

## What is installed

- `.github/workflows/memi-design-ci.yml` follows the reviewed Memi `v2` Action while pinning the CLI to `2.5.0`.
- `memoire.policy.json` commits the design-quality contract.
- `.agents/skills/enforce-design-ci/SKILL.md` gives Codex, Claude, Cursor, and
  other Agent Skills clients the same completion gate.

## Verify locally

```bash
npx -y @memi-design/cli@2.5.0 diagnose . --json --no-write --fail-on none
npx -y @memi-design/cli@2.5.0 ci . --report
```

The audit is deterministic and does not call an LLM. Reports are written under
`.memoire/app-quality/`.

## Verified baseline

Memi `2.5.0` scanned this fork on July 15, 2026 and reported:

- 155 source files, 24 routes, and 76 components inspected;
- an 88/100 design-health score;
- concrete token, typography, spacing, radius, responsive, and accessibility findings;
- a SARIF artifact for code-scanning integrations; and
- a passing `high`-severity policy gate.

The generated report is intentionally not committed. The workflow regenerates
it from the current source on every push and pull request so the evidence cannot
drift away from the code.

## Install in another repository

```bash
npx -y @memi-design/cli@2.5.0 init --team
```

Then copy the workflow or use `sarveshsea/memi@v2.5.0` as a composite GitHub
Action.

Memi: https://github.com/sarveshsea/memi
Upstream template: https://github.com/vercel/chatbot
