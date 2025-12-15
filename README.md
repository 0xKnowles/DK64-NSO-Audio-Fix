#Donkey Kong 64 (Tag Anywhere) - Nintendo Switch Online N64 Fix

This repository contains custom configuration files (.dtz and .cfg) designed to fix the critical audio crash issues when injecting Donkey Kong 64, specifically the Tag Anywhere (v5) mod, into the official Nintendo Switch Online (NSO) N64 application.

🚨 The Issue
When injecting Donkey Kong 64 into the NSO N64 app using standard tools (like CaVE Database Manager) or generic presets, players often encounter the following bugs:
Audio Dropout (The "Silence" Bug): Upon transitioning from the tutorial/lobby to the first main world (Jungle Japes), the audio completely cuts out while the video continues. This is caused by the audio thread crashing due to timing desyncs during heavy load operations.

Performance Lag: Using generic "safe" configuration values (e.g., TickPerInst: 5 or 8) prevents the crash but causes the game to run in "slow motion" during heavy scene transitions.

App Crashes: Using standard N64 timing values (e.g., TickPerInst: 3) causes the NSO app itself to hard crash due to race conditions between the audio and video threads.

🛠️ The Solution
These configuration files utilize a manually tuned TickPerInst value of 4.
Through extensive testing, this value was found to be the "Goldilocks" zone for the NSO emulator's handling of Rareware's custom engine
Fast enough to process massive asset decompressions (like entering Jungle Japes) without starving the audio buffer.
Stable enough to maintain thread synchronization, preventing the hard crashes associated with faster emulation speeds.

📂 Repository Contents
dk64_tag_anywhere_fix.dtz: The complete, packed configuration file ready for import into CaVE Database Manager.
dk64_config.cfg: The unpacked JSON configuration file for manual editing or inspection.

🚀 Installation Guide
Prerequisites
A modded Nintendo Switch running the Nintendo 64 - Nintendo Switch Online app (tested on v4.0.0+).
CaVE Database Manager (PC Tool).
Your legally obtained Donkey Kong 64 ROM (patched with the Tag Anywhere mod).
Instructions
Download the .dtz file from this repository.
Open CaVE Database Manager on your PC.
Locate your Donkey Kong 64 entry in your database.
Right-click the entry (or use the Tools menu) and select Import .dtz.
Select the dk64_tag_anywhere_fix.dtz file you downloaded.
Re-sync / Export your database to your Switch.
Launch the game on your Switch. The transition to Jungle Japes should now be smooth with full audio.
⚙️ For Manual Tweakers
If you prefer to edit your own existing config file, here are the specific values changed:
