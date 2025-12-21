# OPTIONAL MANIFEST FIELDS FOR HUMAN AUTHORSHIP DOCUMENTATION
(AIFV Standard — AI First Exchange / AIFX)

The following optional fields MAY be included in an AIFV `manifest.json`
to document **declared human involvement** in AI-first video workflows.

These fields are intended to support transparency, attribution, and
contextual authorship documentation. They do not constitute legal
determinations of authorship, ownership, or copyright eligibility.

---

## Optional Fields

```json
"human_authorship_statement": "",
"human_signature": "",
"creator_email": "",
"editorial_notes": "",
"human_editing_steps": [],
"human_curated_output": true
```

Field Descriptions
human_authorship_statement

A creator-provided declaration describing human creative involvement,
such as prompt design, scripting, sequencing, editing, or curation.

human_signature

An optional typed name, digital signature, or cryptographic hash
associated with the authorship statement.

creator_email

Optional contact information for the declaring creator.

editorial_notes

Free-form notes describing human creative decisions, narrative intent,
stylistic direction, or editorial judgment applied to the video.

human_editing_steps

Optional array documenting post-generation edits, cuts, sequencing,
audio adjustments, or other human-applied refinements.

human_curated_output

Boolean flag indicating that the final video output was selected,
arranged, or refined by a human.

Notes

All fields are optional

All fields are declarative, not forensic

Interpretation and legal significance of these fields are determined
by downstream platforms, legal systems, or rights holders
