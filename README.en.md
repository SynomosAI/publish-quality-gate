# publish-quality-gate

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE.md)
![Skill](https://img.shields.io/badge/type-Agent%20Skill-blue.svg)

> 中文版说明见 [README.md](README.md)

A fixed publish-process gate: anything you release externally (Skill, expert package, doc, HTML, PPT, tool) must pass it. **Before publish** — four layers of sensitive-information checks (company → machine → personal → secrets), zero hits per layer. **After publish** — TRACE five-dimension AI self-test (Trust / Reliability / Adaptability / Convention / Effectiveness).

## Features

- Four-layer sensitive info checklist (L1 company, L2 machine, L3 personal, L4 secrets).
- TRACE five-dimension post-publish self-test.
- Package fingerprint in `manifest.json`; ownership attestation in `ATTESTATION.md`.
- `scripts/check_release.py` quick release check.

## Quick Start

```bash
git clone --depth 1 https://github.com/SynomosAI/publish-quality-gate.git
cd publish-quality-gate
python scripts/check_release.py path/to/your/release
cat manifest.json
```

```text
Trigger: ready to publish, pre-publish check, post-publish self-test,
TRACE evaluation, scrub sensitive info, release quality.
```

## Four layers at a glance

| Layer | Target | Typical hit |
|---|---|---|
| L1 company | company/people/certs/internal docs | employer name, customer, registration numbers |
| L2 machine | paths/usernames/install/hardware | Users dir, local login name, hardcoded paths |
| L3 personal | ID/phone/email/address/bank | PII |
| L4 secrets | keys/tokens/passwords/API keys | any secrets |

Each layer must have **zero hits**; on a hit, scrub, repack, recheck.

## License

MIT; see [`LICENSE.md`](LICENSE.md). Ownership notice in `ATTESTATION.md` (© 2026 注册老炮 (MedXpert)) preserved verbatim.

## Security

Report issues privately per [`SECURITY.md`](SECURITY.md). Never commit real secrets found during scanning back to this repo.

## Disclaimer

Theoretical stance and tooling exploration; not a claim of certification, commercial delivery, or service to any customer.
