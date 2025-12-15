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

## Holding Bay Categories

The `holding-bay/sorted/` directory organizes repository projects by their current status and development priority:

| Category | Description | Link |
|----------|-------------|------|
| **Consolidation** | Related ideas and projects that could be grouped, matched, or integrated together. These repositories may share data sources, similar goals, or complementary functionality. | [View](holding-bay/sorted/consolidation.md) |
| **Experiments in Progress** | Enduring experiments and proof-of-concepts that aren't overnight projects. Ongoing explorations to see if particular approaches work in practice. | [View](holding-bay/sorted/experiments-in-prog.md) |
| **General Ideas** | Long-term visions for solving particular problems. Bigger-picture concepts, sometimes addressing societal challenges like job markets. | [View](holding-bay/sorted/general-ideas.md) |
| **Needs Update** | Repositories that are behind or lagging a bit and need updating to bring them current. | [View](holding-bay/sorted/needs-update.md) |
| **Not Started** | Projects that are parked and waiting for time to work on them. Initial scope or context has typically been defined, but implementation hasn't begun yet. | [View](holding-bay/sorted/not-started.md) |
| **Parked** | Ideas and experiments that have been set aside or are on indefinite hiatus. | [View](holding-bay/sorted/parked.md.) |
| **To Develop** | Cherry-picked repositories that show merit and are worth continuing to work on and focus development efforts. | [View](holding-bay/sorted/to-develop.md) |
| **To Maintain** | Repositories that are in good order and already started. These just need periodic maintenance to keep them up to date. | [View](holding-bay/sorted/to-maintain.md) |

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