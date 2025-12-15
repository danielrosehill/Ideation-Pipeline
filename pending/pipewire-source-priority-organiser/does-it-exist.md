# Does It Exist? - PipeWire Source Priority Organiser

**Assessment Date:** 2025-12-15

## Summary

**Verdict: This specific tool does NOT exist.** There is a gap in the Linux audio ecosystem that this idea could fill.

While there are several related tools and methods for managing audio device priorities in PipeWire/WirePlumber, none provide the specific combination of features described: a GUI-based, profile-driven microphone priority manager with automatic switching based on context.

---

## Existing Solutions Evaluated

### 1. WirePlumber Configuration Files

**What it does:** WirePlumber (PipeWire's session manager) allows setting device priorities through configuration files using SPA-JSON format.

**Limitations:**
- Requires editing configuration files manually (`~/.config/wireplumber/wireplumber.conf.d/*.conf`)
- No GUI interface
- No profile-based switching
- Priorities are static, not context-aware
- As of WirePlumber 0.5, configuration format changed from Lua to SPA-JSON, requiring users to learn new syntax

**Source:** [WirePlumber - ArchWiki](https://wiki.archlinux.org/title/WirePlumber), [ZenLinux Blog](https://blog.zenlinux.com/2022/08/how-to-configure-audio-device-priorities-in-pipewire-wireplumber/)

### 2. pavucontrol / pavucontrol-qt

**What it does:** Volume control and device selection GUI for PulseAudio/PipeWire.

**Limitations:**
- Can select which microphone to use, but no priority management
- No profile system for different workflows
- No automatic switching based on rules
- Requires manual intervention each time

**Source:** [PipeWire - ArchWiki](https://wiki.archlinux.org/title/PipeWire)

### 3. qpwgraph / Helvum

**What it does:** Graphical patchbay tools for visualizing and connecting audio nodes in PipeWire.

**Limitations:**
- Focused on routing/patching, not priority management
- More suited for professional audio workflows with complex routing
- Overkill for simple "which microphone is default" management
- No profile-based automation

**Source:** [PipeWire - ArchWiki](https://wiki.archlinux.org/title/PipeWire)

### 4. SoundSwitch / AudioSwitch (Windows Only)

**What it does:** Windows applications that allow hotkey-based profile switching between audio devices, including application-specific triggers.

**Limitations:**
- **Windows only** - not available for Linux
- Closest conceptual match to the proposed tool
- C# application (SoundSwitch) or Windows-native (AudioSwitch)

**Source:** [SoundSwitch GitHub](https://github.com/Belphemur/SoundSwitch), [SoundSwitch Website](https://soundswitch.aaflalo.me/)

### 5. KDE Phonon

**What it does:** KDE's sound system allows organizing device priorities for different application categories through System Settings.

**Limitations:**
- Tied to KDE's Phonon abstraction layer
- Category-based (notifications, music, games) rather than workflow-based
- Doesn't support custom profiles like "Dictation Mode" or "Voiceover Mode"
- Not focused on microphone/input prioritization

---

## Gap Analysis

The following features are **not available** in any existing Linux tool:

| Feature | Existing Tools | Gap? |
|---------|---------------|------|
| GUI-based priority management | ❌ (config files only) | **YES** |
| Profile-based workflows (Dictation Mode, Voiceover Mode) | ❌ | **YES** |
| Automatic switching based on connected devices | Partial (WirePlumber does basic auto-switching) | **YES** (rule-based) |
| User-defined friendly names for devices | ❌ | **YES** |
| Device categorization (Headset, Studio Mic, Lavalier) | ❌ | **YES** |
| System tray integration for occasional access | ❌ | **YES** |
| Persistent, lightweight configuration | ❌ (WirePlumber requires manual file editing) | **YES** |

---

## Conclusion

**This idea addresses a genuine gap in the Linux audio ecosystem.**

The "Goldilocks problem" described in the proposal is accurate:
- **Too basic:** pavucontrol, KDE settings (no priority management, no profiles)
- **Too complex:** qpwgraph, Helvum (professional patchbay tools, steep learning curve)
- **Platform-locked:** SoundSwitch exists for Windows with similar functionality, but nothing comparable for Linux

The closest thing on Linux is manually editing WirePlumber configuration files, which:
- Has no GUI
- Has no profile system
- Requires technical knowledge
- Is not intuitive to maintain

**Recommendation:** This is a viable project to pursue. There is clear demand (the user's workflow reflects a common scenario for content creators, voice-to-text users, and podcasters on Linux), and no existing solution adequately addresses the specific use case.
