# PipeWire Source Priority Organiser - Cleaned Transcript

## Overview

This utility addresses a common problem in voice-centric workflows: managing multiple connected microphones and automatically switching between them based on context.

## The Problem

When working with multiple USB microphones (headsets, boundary mics, studio mics, webcam mics, Bluetooth devices), it's easy to have 4-5 audio sources connected simultaneously. Currently, managing these in PipeWire requires editing service files and configuration code, which is neither intuitive nor maintainable.

The challenge is even more pronounced when:
- Webcams have built-in microphones (usually poor quality)
- Different mics are optimal for different tasks (dictation vs. voiceover recording)
- You forget to disconnect Bluetooth devices
- You need to frequently switch between use cases

## Current Workflow Issues

Currently managing microphone priority through PipeWire service files has several drawbacks:
- Configurations are defined in code
- Not easy to swap the order of precedence
- Difficult to maintain
- No visual interface for management

## Proposed Solution

A GUI-based microphone priority manager with the following features:

### Core Functionality

1. **Profile-Based Priority System**
   - Define different profiles for different activities (e.g., "Dictation Mode", "Voiceover Mode")
   - Each profile specifies a hierarchy of microphone preferences
   - Profiles persist across reboots

2. **Intelligent Source Selection**
   - Rather than binding applications to specific microphones, bind them to the "default" source
   - The tool automatically switches which microphone becomes the default based on:
     - Active profile
     - Connected devices
     - User-defined rules

3. **Device Management**
   - Lightweight data store for all microphones the OS has encountered
   - User can assign friendly names to devices (vendor IDs don't always include model names)
   - Categorization system (e.g., "Studio Microphone", "Headset", "Lavalier", "Gooseneck", "Bluetooth")

### Example Use Cases

**Dictation Mode:**
- Priority: Headset > Studio Mic > Webcam
- Logic: "If in dictation mode and both studio microphone and headset are available, headset gets priority"

**Voiceover Mode:**
- Priority: Samson Q2U (or ATR XLR mic) > Headset > Others
- Logic: "If in voiceover mode, prioritize studio-grade microphones"

### Implementation Details

**Background Service:**
- Runs on boot as a background process
- Monitors connected audio sources
- Applies priority rules automatically when devices connect/disconnect

**GUI Interface:**
- Accessible from system tray
- Not a frequently-accessed tool (maybe monthly adjustments)
- Simple interface for:
  - Viewing connected microphones
  - Setting priority order
  - Managing profiles
  - Assigning names and categories to devices

**Data Storage:**
- Very lightweight (only ~10 microphones maximum that OS has ever seen)
- Stores:
  - Device name
  - Vendor ID
  - Manufacturer ID
  - User-assigned friendly name
  - Category
  - Priority order per profile

**PipeWire Integration:**
- Handle actual source toggling through PipeWire
- Acts as a source manager
- Automatically sets default source based on rules

## Design Philosophy

This tool aims to solve the "Goldilocks problem" in audio software:
- Existing solutions are either too basic (no priority management)
- Or insanely overcomplicated (stage routing tools with this as a minor feature)

This tool should be:
- **Simple**: GUI-based microphone source prioritization
- **Focused**: Does one thing well
- **Straightforward**: Profile-based, rule-based logic
- **User-friendly**: Visual interface, not configuration files

## Technical Considerations

- Rule-based logic for priority switching
- Profile system for different workflows
- Lightweight enough to run continuously in background
- Integration with PipeWire for actual source management
- System tray presence for occasional configuration access

## Notes

If this tool already exists, great! But based on current research, nothing quite fits this specific niche of profile-based, rule-driven microphone priority management with a simple GUI.
