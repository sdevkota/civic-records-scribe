# Civic Records Scribe

Transparent extraction manifests for public records and government documents.

> Version: 2.0.0 | Runtime: Python | License: MIT | Status: production-oriented v2 foundation

## Problem

Public records digitization often lacks transparent extraction quality, provenance, and challenge workflows.

## What this project solves

A civic document extraction checker that tracks source authority, fields, confidence, redactions, and appeal-ready audit metadata.

Civic Records Scribe is now Python-first. It ships as a dependency-free Python package and CLI that validates a domain-specific JSON packet, emits actionable findings, and gives contributors a practical foundation for adapters, datasets, evals, and workflow integrations.

## Quick start

```bash
python3 -m unittest discover -s tests
python3 -m civic_records_scribe.cli sample
```

Analyze your own packet:

```bash
python3 -m civic_records_scribe.cli ./packet.json
```

Or pipe JSON:

```bash
cat packet.json | python3 -m civic_records_scribe.cli
```

## Example packet

```json
{
  "record": {
    "agency": "city clerk",
    "id": "permit-77"
  },
  "extraction": {
    "fields": {
      "applicant": "A. Patel"
    },
    "confidence": 0.81
  },
  "redactions": {
    "present": true,
    "reason": "personal_phone"
  }
}
```

## Library usage

```python
from civic_records_scribe import analyze

report = analyze({
  "record": {
    "agency": "city clerk",
    "id": "permit-77"
  },
  "extraction": {
    "fields": {
      "applicant": "A. Patel"
    },
    "confidence": 0.81
  },
  "redactions": {
    "present": True,
    "reason": "personal_phone"
  }
})
print(report["summary"])
```

## v2 behavior

- Python-first CLI and importable library.
- Validates required fields for the domain packet.
- Scores readiness from 0 to 100.
- Reports missing or weak governance evidence.
- Runs fully offline with no API keys and no network access.

## Contribution map

- Add FOIA workflows.
- Add OCR adapters.
- Add field validation plugins.
- Add public audit portals.

## Project principles

- Human agency over blind automation.
- Open standards over vendor lock-in.
- Auditable decisions over hidden magic.
- Privacy and safety as design constraints, not release notes.
