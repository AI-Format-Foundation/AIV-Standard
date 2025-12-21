# AIFV — AI First Video Format (`.aifv`)
Part of the AI First Exchange (AIFX)

**AIFV (AI First Video Format)** is an open, ZIP-based standard for AI-generated
video. It packages video assets, prompts, scripts, generation parameters,
audio tracks, subtitles, thumbnails, licensing information, and declared
provenance into a single **`.aifv`** container.

AIFV is designed for **transparent, inspectable, and interoperable**
AI-native video workflows across platforms and tools.

---

## 🎬 Overview

An `.aifv` file represents a single AI-generated video with structured
context describing **how the video was created**, **with what tools**, and
**under what parameters**.

AIFV supports documentation of:
- AI generation inputs (prompts, scripts, settings)
- Media assets (video, audio, subtitles, thumbnails)
- Declared provenance and timestamps
- Licensing and attribution context

AIFV does **not** guarantee reproducibility or legal authorship and does
not verify metadata beyond what is recorded in the container.

---

## 📦 AIFV Container Structure

An `.aifv` file is a ZIP container with the following standardized layout:

/
manifest.json # REQUIRED: primary video manifest
video/
main.mp4 # REQUIRED: primary video (mp4/webm/mov)
audio/
voiceover.wav # OPTIONAL
music.wav # OPTIONAL
frames/
thumbnails/ # OPTIONAL: preview images
keyframes/ # OPTIONAL: extracted frames
prompts/
generation.txt # OPTIONAL: main prompt
negative.txt # OPTIONAL
script.txt # OPTIONAL: scene or narration script
settings.json # OPTIONAL: model/generator parameters
subtitles/
captions.srt # OPTIONAL: captions or transcripts
legal/
license.txt # OPTIONAL: licensing terms
terms.txt # OPTIONAL
extra/
notes.md # OPTIONAL: creator notes

yaml
Copy code

The `manifest.json` anchors the container by defining metadata, declared
AI sources, provenance, and file references.

---

## 🧠 Key Capabilities

### ✔ AI-Native Video Metadata

AIFV may record declared information such as:
- AI tool or platform identifier (e.g., Veo, Runway, Sora, Pika)
- Model or pipeline name
- Prompt and script sources
- Negative prompts (where applicable)
- Generation parameters (resolution, FPS, duration, aspect ratio)
- Multi-track audio references
- Declared creator identity and timestamps

---

### ✔ Unified Video Container

A single `.aifv` file may include:
- Final rendered video
- Prompts and scripts
- Generator settings
- Audio tracks or stems
- Subtitles or transcripts
- Thumbnails or preview frames
- Licensing and attribution metadata

This supports **exchange, archiving, review, and platform ingestion**
without reliance on external sidecar files.

---

### ✔ Declared Provenance & Transparency

AIFV enables documentation of:
- Who declared authorship
- Which tools were used
- What inputs shaped the output
- When the video was created

AIFV records **declared provenance**, not absolute proof of origin.

---

### ✔ Open & Extensible Design

AIFV is:
- ZIP-based
- JSON-driven
- Language-agnostic
- Forward-compatible

Developers may extend AIFV for:
- Multi-scene or episodic video
- VFX or CGI pipelines
- Storyboards and animatics
- Multi-model or hybrid workflows

---

## 📑 `manifest.json` (Simplified Example)

```json
{
  "aifv_version": "1.0.0",
  "id": "aifv-2025-000001",
  "title": "Sample Video",
  "creator": "CreatorName",
  "duration_seconds": 12.5,
  "resolution": "1920x1080",
  "fps": 24,
  "aspect_ratio": "16:9",
  "ai_generated": true,

  "ai_source": {
    "tool_name": "Veo",
    "model_name": "Veo-Gen",
    "prompt_source": "prompts/generation.txt",
    "script_source": "prompts/script.txt",
    "settings_source": "prompts/settings.json"
  },

  "provenance": {
    "creator_handle": "YourName",
    "creation_utc": "2025-12-01T04:22:00Z",
    "tool_chain": ["Veo", "AIFX Converter v1.0"]
  },

  "files": {
    "main_video": "video/main.mp4",
    "audio_tracks": [
      "audio/voiceover.wav",
      "audio/music.wav"
    ],
    "captions": "subtitles/captions.srt",
    "thumbnail": "frames/thumbnails/default.jpg"
  }
}
```
🌐 MIME Type
Proposed MIME type:

bash
Copy code
video/aifv
🧰 Tooling (Planned)
Reference implementations may include:

aifvwrap — package video assets into .aifv

aifv-validate — validate AIFV containers

aifv-core — libraries for reading/writing AIFV files

🛠 Use Cases
AI filmmaking and short-form video

Storyboarding and pre-visualization

Platform ingestion of AI video

Training datasets with full metadata context

Archival of AI-native video projects

Multi-scene or episodic AI video workflows

🔄 Versioning
AIFV follows semantic versioning:

1.x.x — backward-compatible enhancements

2.x.x — backward-incompatible schema changes

Unknown fields should be ignored for forward compatibility.

📬 Contributing
AIFV is an open specification under the AI First Exchange (AIFX).
Contributions via issues and pull requests are welcome.

📝 License
Released under the MIT License.
