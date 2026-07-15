---
name: enforce-design-ci
description: Audit frontend changes against this repository's committed Memi design policy before declaring UI work complete.
---

# Enforce Design CI

Use this skill after editing files under `app/`, `components/`, or `artifacts/`.

1. Read `memoire.policy.json`.
2. Run the deterministic audit:

```bash
npx -y @memi-design/cli@2.5.0 diagnose . --json --no-write --fail-on none
```

3. Fix product-facing findings without weakening the policy or adding arbitrary
   raw color values.
4. Run the same gate used by GitHub Actions:

```bash
npx -y @memi-design/cli@2.5.0 ci . --report
```

5. Report the files inspected, findings fixed, remaining exceptions, and the
   design-health artifact path.

The CLI is an enhancement, not a substitute for judgment. Preserve the
template's existing shadcn, Radix, Tailwind, accessibility, and Ultracite
conventions.
