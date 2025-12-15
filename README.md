# App Ideas (Staging / Pipeline Repository)

![alt text](images/banner.png)

This repository provides a structured system for capturing, refining, and organizing ideas for vibe-coded apps and utilities pending implementation.

## Overview

Vibe-coding enables rapid creation of utilities and proof-of-concepts at an unprecedented pace. Over the past year, using Claude Code and other AI assistants, I've been working through a backlog of utilities I've always wished existed—while continuously generating new ideas.

This repository manages that ideation pipeline. Ideas captured here can marinate until the right moment for implementation arrives. 

## Workflow

This process approximates spec-driven development, with each idea progressing through several refinement stages:

1. **Voice Recording**: Capture the idea as an audio note, including detailed specifications and feasibility thoughts
2. **Transcription**: Use ASR (Whisper, etc.) to generate a raw transcript
3. **Refinement**: Clean up the transcript using an LLM
4. **Analysis**: Generate AI assessments (does-it-exist checks, feasibility ratings)
5. **Specification**: Convert the refined transcript into a polished spec
6. **Implementation**: Use the spec to direct agent-based development

### Repository Structure

Each idea gets its own folder containing:
- Audio file(s) (original voice notes)
- `transcripts/` - Raw and refined transcripts
- `ai-analysis/` - AI-generated assessments
- Specification documents

Ideas live in:
- `pending/` - Ideas awaiting implementation (organized by category)
- `done/` - Completed/implemented ideas
- `to-process/` - Raw ideas needing transcription and analysis

Categories help group related ideas together (e.g., `voice-to-text/`, `automation/`, `media-processing/`).

## Ideas Index

### Pending Ideas

#### Voice-to-Text

| Idea | Audio | Transcript | Analysis | Status |
|------|-------|------------|----------|--------|
| [PipeWire Source Priority Organiser](pending/voice-to-text/pipewire-source-priority-organiser/) | [Audio](pending/voice-to-text/pipewire-source-priority-organiser/idea.mp3) | [Cleaned](pending/voice-to-text/pipewire-source-priority-organiser/transcripts/02-cleaned-transcript.md) | [Analysis](pending/voice-to-text/pipewire-source-priority-organiser/ai-analysis/ai-analysis.md) | Pending |

### Completed Ideas

*No completed ideas yet*

## License & Contributions

All ideas and code in this repository are licensed under MIT. Feel free to implement any idea—pending or completed—yourself!