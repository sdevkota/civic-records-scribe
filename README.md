# Civic Records Scribe

Transparent extraction manifests for public records and government documents.

> Version: 1.0.0 | License: MIT | Status: production-oriented v1 foundation

## Problem

Public records digitization often lacks transparent extraction quality, provenance, and challenge workflows.

## What this project solves

A civic document extraction checker that tracks source authority, fields, confidence, redactions, and appeal-ready audit metadata.

Civic Records Scribe ships as a small, dependency-free CLI and library. It validates a domain-specific JSON packet, emits actionable findings, and gives contributors a concrete surface for adding adapters, richer checks, schemas, and integrations.

## Who it is for

Civic tech groups, local governments, journalists, archivists.

## Quick start

```bash
npm test
npm start -- sample
```

Analyze your own packet:

```bash
civic-records-scribe ./packet.json
```

Or pipe JSON:

```bash
cat packet.json | node src/cli.js
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

```js
const { analyze } = require("./src/index.js");

const report = analyze({
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
});
console.log(report.summary);
```

## v1 behavior

- Validates required fields for the domain packet.
- Scores readiness from 0 to 100.
- Reports missing or weak governance evidence.
- Suggests next actions and contributor extension points.
- Runs fully offline with no API keys and no network access.

## Contribution map

Good first contributions:

- Add FOIA workflows.
- Add OCR adapters.
- Add field validation plugins.
- Add public audit portals.

Larger contributions:

- Add a JSON Schema and compatibility tests.
- Build import/export adapters for popular AI frameworks.
- Add real-world fixtures from public, non-sensitive examples.
- Improve scoring with transparent, documented heuristics.

## Project principles

- Human agency over blind automation.
- Open standards over vendor lock-in.
- Auditable decisions over hidden magic.
- Privacy and safety as design constraints, not release notes.

## GitHub Pages

The marketing site lives in `site/index.html`. Enable GitHub Pages from the `site` folder or use the included Pages workflow after publishing.

## Security

This project does not process secrets by default. If you build adapters that touch production systems, keep least privilege, explicit consent, and auditable logs in the design.
