# COPYRIGHT & HUMAN AUTHORSHIP GUIDANCE (AIV Standard)

The AI Format Foundation recognizes that copyright protection for AI-assisted works requires meaningful human creative contribution. The AIV Standard supports documentation of human authorship through structured metadata, provenance, and workflow history.

## 1. Human Authorship Requirements

A video may be eligible for copyright if a human:
- Writes prompts or storyboards
- Directs scene transitions, pacing, or composition
- Curates, selects, or rejects generated outputs
- Edits audio, sequencing, or cuts
- Provides stylistic or narrative control over the final result

Purely autonomous AI-generated video without human creative guidance is not copyrightable.

## 2. How AIV Supports Copyright Claims

AIV metadata captures:
- Creator identity (name, handle, email)
- Human-authored prompts and scripts
- Scene-level editing decisions
- Toolchain and model information
- Timestamps and project provenance

This information helps establish human involvement in the creative process.

## 3. Recommended Manifest Fields for Legal Compliance

Creators may include these optional fields:

"human_authorship_statement": "I affirm that I contributed creative authorship...",
"human_signature": "Name or digital signature hash",
"creator_email": "email@example.com",
"editorial_notes": "Summary of human creative decisions."


## 4. Ownership

Copyright belongs to the human author(s) who contributed creative expression.  
If the work contains only machine-generated content without human creative contribution, it may not be eligible for copyright.

## 5. Licensing

Creators may include licensing information in `legal/license.txt` and `legal/terms.txt`.  
All distribution must follow applicable legal requirements.

