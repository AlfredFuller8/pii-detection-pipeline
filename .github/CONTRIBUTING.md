# Contributing to pii-detection-pipeline

## Ground rules

**Never commit real PII.** Test fixtures, examples, and documentation must use synthetic data only. The `.gitignore` blocks most data file extensions outside `tests/fixtures/` and `benchmarks/public/` — do not work around it. If you accidentally commit real PII, see [SECURITY.md](./SECURITY.md) immediately and do not push further commits to that branch.

**Detection changes require benchmarks.** Any PR that modifies detector logic, thresholds, or redaction strategies must include before/after precision, recall, and F1 in the PR description.

**Security issues are private.** Do not open public issues for vulnerabilities or accidental PII commits. Use the channels in [SECURITY.md](./SECURITY.md).

## Branch and commit conventions

Branch names: `feature/...`, `fix/...`, `detector/...`, `docs/...`, `chore/...`, `ci/...`, `bench/...`

Commit prefixes (Conventional Commits):
- `feat:` — new capability
- `fix:` — bug fix
- `detector:` — change to a detector module
- `docs:` — documentation only
- `test:` — test additions or changes
- `bench:` — benchmark additions or changes
- `chore:` — tooling, deps, refactors with no behavior change
- `ci:` — CI workflow changes

## PR requirements

- All CI checks pass (lint, tests, secret/PII scan)
- Reviewed by a code owner per [CODEOWNERS](./.github/CODEOWNERS)
- No real PII in the diff
- Documentation updated if interfaces or behavior changed
- Benchmark deltas included for detection changes

## Adding a new detector

1. Open a "New detector request" issue first to align on scope
2. Add the detector module under `/src/detectors/`
3. Add config under `/configs/`
4. Add synthetic fixtures under `/tests/fixtures/`
5. Add a benchmark entry under `/benchmarks/`
6. Update `/docs/detectors.md`

## Adding a new redaction strategy

1. Add the redactor under `/src/redactors/`
2. Document trade-offs (reversibility, format preservation, collision risk) in `/docs/redactors.md`
3. Add unit tests covering edge cases (empty strings, multibyte chars, overlapping spans)

## Local development

*(Detailed setup will land once `pyproject.toml` exists.)*

Minimum expectations once code is in place:
- Python 3.11+
- `ruff` for lint and format
- `mypy` for type checking
- `pytest` for tests
- `pre-commit` hooks installed before first commit
