# BenchmarkSCA-PyPI

> **Warning:** this repository intentionally pins vulnerable package versions for scanner
> evaluation. Do not install or execute its dependencies.

A public, reproducible PyPI SCA accuracy corpus. Every package in the resolved `Pipfile.lock`
graph is labelled in `ground-truth.json`; there are no unlabelled packages hidden from the
precision or recall denominators.

## Current scorecard

| Packages | Expected findings | Expected clean | Precision | Recall | F1 | Coverage |
|---:|---:|---:|---:|---:|---:|---:|
| 20 | 8 | 12 | 100.00% | 100.00% | 100.00% | 100.00% |

The score is pinned to staging scan commit `11eb40e` and analyzer `3db6559658cd`.

## Coverage and reproducibility

- Five direct requirements and fifteen resolved lockfile packages.
- Vulnerable direct and transitive packages plus clean precision controls.
- Every exact label is rechecked against OSV in CI.
- CI fails on a false positive, false negative, unscanned oracle case, unlabelled scanned package,
  stale advisory, or score below 100%.

Run locally:

```bash
node scripts/verify-oracle.mjs
node scripts/score.mjs
```

The score applies to this version-pinned corpus; it is not an ecosystem-wide prevalence claim.
