# AI Analysis - PipeWire Source Priority Organiser

**Assessment Date:** 2025-12-15

---

## Rating: 8/10

This is a well-conceived idea that addresses a real pain point in Linux audio workflows. It has clear utility, a defined scope, and fills an actual gap in the ecosystem.

---

## Strengths

### 1. Solves a Real Problem
The scenario described (multiple USB microphones connected, needing context-aware switching) is authentic and increasingly common with the rise of voice-to-text workflows, content creation, and remote work. Having 3-5 audio input devices connected is entirely plausible.

### 2. Clear Scope Definition
The proposal explicitly avoids feature creep. It's not trying to be a full audio routing solution or compete with professional tools like qpwgraph. The "Goldilocks" framing demonstrates good product thinking.

### 3. Well-Defined Use Cases
Concrete examples (Dictation Mode vs. Voiceover Mode) make the requirements tangible. The priority logic is straightforward: "If headset and studio mic are both connected, and I'm in dictation mode, prefer headset."

### 4. Sensible Architecture
- Background daemon running at boot
- System tray for occasional access
- Lightweight data store (only ~10 devices)
- PipeWire/WirePlumber integration

### 5. Fills an Ecosystem Gap
Research confirms no existing Linux tool provides this specific combination of features. Windows has SoundSwitch; Linux has nothing comparable.

---

## Weaknesses

### 1. WirePlumber API Complexity
PipeWire/WirePlumber is still evolving. The configuration format changed significantly in WirePlumber 0.5 (Lua to SPA-JSON). Building a stable tool on top of this will require careful attention to API stability.

### 2. Profile Switching Mechanism Unclear
How does the user activate a profile? Options include:
- Manual selection from system tray
- Hotkeys
- Automatic detection (e.g., application focus)

The proposal mentions "modes" but doesn't fully define the activation mechanism.

### 3. Bluetooth Handling Acknowledged but Unsolved
Bluetooth devices (HSP/HFP vs A2DP profiles) add complexity. The tool would need to handle Bluetooth microphones differently than wired USB sources.

### 4. Desktop Environment Considerations
System tray implementation varies across Linux DEs. KDE, GNOME (with extensions), and others handle tray icons differently. This adds cross-DE testing burden.

---

## Suggestions for Improvement

### 1. Define Profile Activation Methods
Consider supporting multiple activation approaches:
- **Manual:** Click system tray icon, select profile
- **Hotkey:** Global keyboard shortcuts (e.g., Super+Shift+D for Dictation)
- **Application-based:** When specific apps launch, auto-activate profiles (like SoundSwitch does on Windows)

### 2. Start with CLI-First Approach
Build the core logic as a CLI/daemon first, then add GUI. This allows:
- Easier testing
- Scriptability for power users
- GUI can come later without blocking core functionality

Example: `mic-priority profile set dictation` or `mic-priority list`

### 3. Use D-Bus for Profile Switching
Exposing profiles via D-Bus would enable integration with:
- KDE shortcuts
- GNOME extensions
- Custom scripts
- Stream Deck plugins

### 4. Consider Minimal First Version
For v1, consider just:
- Single priority list (no profiles)
- System tray with drag-and-drop reordering
- Automatic default source switching

Profiles could be v2.

### 5. Leverage Existing PipeWire Tools
Don't reinvent the wheel. Use `wpctl` and existing PipeWire utilities for actual device control. The tool should be a friendly wrapper, not a reimplementation.

---

## Estimated Complexity

| Component | Complexity | Notes |
|-----------|------------|-------|
| PipeWire/WirePlumber integration | **Medium-High** | Need to monitor device connections, set default sources via wpctl or libwireplumber |
| Device database | **Low** | Simple SQLite or JSON file; ~10 devices max |
| System tray GUI | **Medium** | Qt (for KDE integration) or GTK; cross-DE tray support varies |
| Profile management | **Medium** | CRUD for profiles, storage, activation logic |
| Background daemon | **Low-Medium** | Systemd user service, D-Bus interface |
| Bluetooth handling | **Medium-High** | HSP/HFP profile switching adds complexity |

**Overall Complexity: Medium**

A minimal viable version (single priority list, no profiles) could be built relatively quickly. Full profile-based implementation with all edge cases would take longer.

**Recommended Tech Stack:**
- **Language:** Python (rapid development, good PipeWire bindings) or Rust (performance, safety)
- **GUI:** Qt6/PySide6 (KDE-native) or GTK4 (GNOME-friendly)
- **Daemon:** Systemd user service
- **IPC:** D-Bus for external control
- **Storage:** JSON or SQLite

---

## Final Assessment

This is a **solid, implementable idea** with genuine utility. It's not revolutionary, but it's the kind of practical utility that improves daily workflows. The scope is appropriate for a vibe-coding project, and the problem is well-understood.

**Recommendation:** Proceed with implementation. Start with a minimal version (priority list without profiles) to validate the PipeWire integration, then expand.
