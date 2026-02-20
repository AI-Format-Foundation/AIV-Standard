# AIFV v0 Minimal Profile (SDA + Canonical Integrity)

Status: **LOCKED (v0)**
Verification tier: **SDA only**
Integrity: **sha256 + canonical_excludes_self**

This document defines the minimum required structure for an **AIFV** package to be considered valid in AIFX v0.

AIFV is a container for AI-generated video, bundling:
- `manifest.json`
- one primary video asset in `assets/`
- one thumbnail image in `assets/`
- canonical integrity hashes

---

## 1) Container structure

An **.aifv** file is a ZIP container with:

Required:
- `manifest.json`
- `assets/video.<ext>` (single primary video)
- `assets/thumb.<ext>` (thumbnail image)

No symlinks.
No absolute paths.
No `..` traversal.

---

## 2) Manifest required fields

`manifest.json` MUST be valid JSON and MUST include:

### Identity / work
- `aifx_version` (string; current tooling uses `"0.1"`)
- `type` = `"AIFV"`
- `work.title` (string; non-empty)

### Creator (SDA)
- `creator.name` (string; non-empty)
- `creator.contact` (string; non-empty; email recommended)

### Provenance scope
- `mode` (string; example: `human-directed-ai`)
- `verification_tier` MUST be `"SDA"`
- `ai_generated` MUST be `true`
- `declaration` (string; non-empty; human-authored)

---

## 3) Assets

AIFV v0 requires exactly:
- one primary video
- one thumbnail

Recommended canonical paths:
- `assets/video.<ext>`
- `assets/thumb.<ext>`

Allowed video extensions (tooling v0):
- `.mp4`, `.mov`, `.webm`, `.m4v`

Allowed thumbnail extensions (tooling v0):
- `.jpg`, `.jpeg`, `.png`, `.webp`

---

## 4) Canonical integrity (AIFX)

AIFV MUST include the canonical `integrity` block:

```json
"integrity": {
  "algorithm": "sha256",
  "manifest_hash_mode": "canonical_excludes_self",
  "hashed_files": {
    "assets/video.mp4": {"sha256": "<sha256>"},
    "assets/thumb.jpg": {"sha256": "<sha256>"},
    "manifest.json": {"sha256": "<sha256_of_manifest_canonical_excludes_self>"}
  }
}
```
Rules
	•	integrity.algorithm MUST be "sha256".
	•	integrity.hashed_files MUST be an object with sha256 entries for all required files.
	•	Required hashed files include at minimum:
	•	the primary video asset (e.g., assets/video.mp4)
	•	the thumbnail asset (e.g., assets/thumb.jpg)
	•	manifest.json

Canonical excludes self

The manifest.json hash MUST be computed over the manifest JSON with the manifest.json hash entry excluded.

⸻

5) Informational (warnings only in v0)

Tooling may warn if optional facts are missing (non-fatal), e.g.:
	•	duration
	•	resolution
	•	fps
	•	codecs

These are NOT required in v0.

⸻

6) Validation outcomes

A package FAILS if any required field is missing, empty, or invalid, including:
	•	missing manifest.json
	•	missing work.title
	•	missing creator.name or creator.contact
	•	verification_tier not "SDA"
	•	ai_generated not true
	•	missing/empty declaration
	•	missing integrity or integrity mismatch
	•	missing primary video asset
	•	missing thumbnail asset
	•	unsafe paths/symlinks

⸻

7) v0 scope boundary

AIFV v0 does not:
	•	prove originality
	•	verify identity
	•	enforce licensing
	•	perform moderation

It only enforces:
	•	structure
	•	SDA boundary
	•	canonical integrity

⸻

Core principle

Declare only what you can prove today.
Design for what you can verify tomorrow.
