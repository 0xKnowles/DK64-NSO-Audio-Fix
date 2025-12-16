<div align="center">

# Donkey Kong 64 Audio Fix - Switch NSO on CFW
### NSO Configuration Fix

Custom configuration files (`.dtz` and `.cfg`) designed to fix the critical audio crash issues when injecting **Donkey Kong 64** into the official **Nintendo Switch Online N64 app**.

</div>

---

## 🚨 The Issue

When injecting Donkey Kong 64 into the NSO N64 app using standard tools (like CaVE Database Manager) or generic presets, players often encounter the following bugs:

- **Audio Dropout (The "Silence" Bug)**: Upon transitioning from DK Isle to the first main world (Jungle Japes), the audio completely cuts out while the video continues. This is caused by the audio thread crashing due to timing desyncs during heavy load operations.
- **Performance Lag**: Using generic "safe" configuration values (e.g., `TickPerInst: 5` or `8`) prevents the crash but causes the game to run in "slow motion" during heavy scene transitions.
- **App Crashes**: Using standard N64 timing values (e.g., `TickPerInst: 3`) causes the NSO app itself to hard crash due to race conditions between the audio and video threads.

## 🛠️ The Solution

These configuration files utilize a manually tuned `TickPerInst` value of **4**.

> **Why this works:**
> Through testing, this value was found to be the "Goldilocks" zone for the NSO emulator's handling of Rareware's custom engine. It is fast enough to process massive asset decompressions (like entering Jungle Japes) without starving the audio buffer, but stable enough to maintain thread synchronization.

## 📂 Repository Contents

- `DK64_Ticker4.dtz`: The complete, packed configuration file (**Import this one**).
- `02_XXXXXX.000.cfg`: The unpacked JSON configuration file (For manual editing/inspection).

## 🚀 Installation Guide

### Prerequisites
1. A modded Nintendo Switch running the **Nintendo 64 - Nintendo Switch Online** app (tested on v4.0.0+).
2. **CaVE Database Manager** (PC Tool).
3. Your legally obtained **Donkey Kong 64 ROM** (patched with the Tag Anywhere mod).

### Instructions
1. Download the `.dtz` file from this repository.
2. Open **CaVE Database Manager** on your PC.
3. Locate your Donkey Kong 64 entry in your database.
4. Right-click the entry (or use the Tools menu) and select **Import .dtz**.
5. Select the `DK64_Ticker4.dtz` file you downloaded.
6. Re-sync / Export your database to your Switch.
7. Launch the game on your Switch. The transition to Jungle Japes should now be smooth with full audio.

## ⚙️ For Manual Tweakers

If you prefer to edit your own existing config file rather than importing mine, apply the following change to your JSON config:

```json
"RomOption": {
    "TickPerInst": 4
}
```

*Note: The `CopyDepthAtFullSync` value in `RendererSetting` was left at `1` during successful tests, but can be set to `0` if you experience graphical slowdowns in other areas.*

## ⚠️ Disclaimer

This repository **DOES NOT** contain any ROM files or game code. It only contains configuration text files (`.json`/`.cfg`) that tell the emulator how to run the game. You must provide your own legally owned backups of the game files.

## 🏆 Credits

- **Tag Anywhere Mod**: Created by Isotarge - The mod that makes this game infinitely more replayable.
- **CaVE Database Manager**: The essential tool for NSO modding.
- **Updated dtz**: Tuned by 0xKnowles.
