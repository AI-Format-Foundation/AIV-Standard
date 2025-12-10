# AIV-Standard
AIV (AI Video Format) is an open, ZIP-based standard for AI-generated video. It packages video, prompts, scripts, metadata, subtitles, thumbnails, audio tracks, licensing, and provenance into a single .aiv file for transparent, AI-native workflows.

🎬 AIV – AI Video Format
A unified open standard for AI-generated video

File extension: .aiv
Version: 1.0.0

🎥 Overview

AIV (AI Video Format) is an open, ZIP-based container standard for AI-generated video.
It packages the video file, generation prompts, scene scripts, frame metadata, subtitles, licensing, thumbnails, and provenance into a single .aiv file.

AIV enables transparent attribution, consistent metadata, and standardized workflows for AI-native video across platforms and tools.

📦 What’s Inside an .aiv File?

An .aiv file is a ZIP container with a structured directory:
/
  manifest.json                     # REQUIRED: core metadata for the video
  video/
    main.mp4                        # REQUIRED: primary video (or webm/mov)
  audio/
    voiceover.wav                   # OPTIONAL
    music.wav                       # OPTIONAL
  frames/
    thumbnails/                     # OPTIONAL: preview images
    keyframes/                      # OPTIONAL: keyframe exports
  prompts/
    generation.txt                  # OPTIONAL: main prompt text
    negative.txt                    # OPTIONAL
    script.txt                      # OPTIONAL: scene description
    settings.json                   # OPTIONAL: model/generator settings
  subtitles/
    captions.srt                    # OPTIONAL: captions or transcripts
  legal/
    license.txt                     # OPTIONAL: usage terms
    terms.txt                       # OPTIONAL: content rights
  extra/
    notes.md                        # OPTIONAL: project notes
The manifest.json file anchors the whole format by defining metadata, technical details, AI origin, prompt sources, and file paths.

🧠 Key Features
✔ AI-native video metadata

AIV stores:

AI model name + version

Generation engine (e.g., “Sora”, “Runway”, “Pika”, “Veo”)

Prompt text

Scene structure

Negative prompts

Seed values

Resolution, FPS, duration

Multi-track audio references

Creator identity & provenance

✔ Unified container

All elements required for full video reproduction are stored together:

Video file

Prompts

Settings

Scripts

Audio stems

Subtitles

Cover thumbnails

Licensing

Metadata

Everything in one .aiv.

✔ Verifiable provenance

Ensures transparency:

Who generated the video

With which tool

Using what prompts

On what date

With what parameters

Perfect for:

Platforms verifying AI content

Legal safety

Content authenticity

Ownership chain

Remix tracking

✔ Open & extensible

AIV uses a ZIP-based structure, readable by any language or tool:

Python

Node.js

Go

Rust

C++

Developers can easily extend the spec for:

VFX projects

Storyboards

CGI scene data

Multi-model pipelines

📑 manifest.json Structure (Simplified)
{
  "aiv_version": "1.0.0",
  "id": "aiv-2025-000001",
  "title": "Sample Video",
  "primary_creator": "CreatorName",
  "duration_seconds": 12.5,
  "resolution": "1920x1080",
  "fps": 24,
  "aspect_ratio": "16:9",
  "genres": ["cinematic"],
  "ai_generated": true,

  "ai_source": {
    "tool_name": "Sora",
    "tool_version": "v1",
    "model_name": "Sora-Gen",
    "prompt_source": "prompts/generation.txt",
    "script_source": "prompts/script.txt",
    "settings_source": "prompts/settings.json"
  },

  "provenance": {
    "creator_handle": "YourName",
    "creation_utc": "2025-12-01T04:22:00Z",
    "tool_chain": ["Sora", "AIV-WRAPPER v1.0"]
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

🧰 Tools (Coming Soon)

Planned reference implementations:

aivwrap — CLI to package MP4/WebM into .aiv

aiv-validator — ensure spec compatibility

aivcore — library for parsing/writing AIV containers

🌐 MIME Type

Recommended MIME type for AIV files:
video/aiv

🛠 Use Cases

AI filmmaking

Storyboarding & pre-visualization

Short-form and vertical content

Training datasets with full metadata

Verifiable generative content

Multi-scene animation workflows

🔄 Versioning

AIV uses semantic versioning:

1.x.x — backward compatible schema updates

2.x.x — breaking changes to container or manifest

Players should ignore unknown fields for forward compatibility.

📬 Contributing

AIV is an open specification.
Developers, creators, and platforms may propose additions or improvements via issues or pull requests.

📝 License

Released under the MIT License.
