# pii-detection-pipeline

Reference architecture for privacy-by-design PII detection and redaction — pluggable detectors (regex, NER, LLM), policy-driven redaction, audit logging, and review workflows across data lakes, streams, and document stores. Aligned with GDPR, CCPA, and HIPAA.

## Status
Early development — architecture and interfaces in flux. Not production-ready.

## Who this is for
- Privacy engineers designing PII handling at the platform level
- Data platform teams implementing redaction across pipelines
- Compliance teams needing auditable detection workflows

## Architecture overview
See [docs/architecture.md](./docs/architecture.md).

Core components:
- **Detectors** — regex, NER models, LLM classifiers, validators (pluggable)
- **Pipeline** — orchestration across batch, streaming, and document sources
- **Redactors** — masking, tokenization, hashing, format-preserving encryption
- **Audit log** — every detection and redaction recorded for compliance review
- **Review queue** — human-in-the-loop for low-confidence or high-risk matches

## Quickstart
*(Coming soon — pipeline implementation in progress.)*

## Documentation
- [Architecture](./docs/architecture.md)
- [Detector specifications](./docs/detectors.md)
- [Threat model](./docs/threat-model.md)
- [Compliance mapping](./docs/compliance.md)

## Contributing
See [CONTRIBUTING.md](./CONTRIBUTING.md). PRs must contain no real PII and detection changes must include benchmark deltas.

## Security
See [SECURITY.md](./SECURITY.md) for private vulnerability disclosure.

## License
Apache 2.0 — see [LICENSE](./LICENSE).
