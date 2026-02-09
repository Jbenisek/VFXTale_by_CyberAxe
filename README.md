# VFXTale by CyberAxe - A Hytale Particle Generator

A visual particle effect editor for Hytale, built with Rust + egui + wgpu.
Load, edit, preview, and save native Hytale `.particlespawner` and `.particlesystem` JSON files.

**Current Version: 0.3.19** - Beta

## What's New (v0.3.6 - v0.3.19)

### v0.3.19 - Batch Tools Improvements
- **Batch Tools floating window** — BATCH TOOLS now opens as a floating popup window instead of inline, no longer consumes entire screen
- **BatchTarget Min/Max selector** — Scale X, Scale Y, Rotation, and Frame batch operations can now target Min only, Max only, or Both (preserves untargeted value)
- **hytale_slider typed input fix** — DragValue number box input in Initial Frame and Collision Frame Scale X/Y now correctly triggers changes

### v0.3.18 - Batch Tools & Generate
- **Batch Edit** — Apply Set/Add/Multiply/Random across ALL keyframes for Opacity, Scale X, Scale Y, Rotation, and Frame
- **Generate Loop** — Repeat animation pattern N times across 0-100% timeline with optional jitter and randomize
- **Generate FPS** — Create keyframes from frame count + FPS + lifetime, auto-placing with incrementing frame index

### v0.3.17 - System Connection Fixes
- **System load connected_spawners fix** — All spawner tabs now correctly start enabled when loading a system file
- **New/duplicated/template spawners auto-connect** — New spawner tabs are automatically connected when a system is open
- **UV Motion Strength fix** — Strength values now correctly divided by 100 (Hytale uses percentages)

### v0.3.16 - System Spawner Reference Fixes
- **Spawner rename syncs to system** — Renaming a spawner tab updates the SpawnerReference.spawner_id in the system
- **Save/Export preserves SpawnerReference overrides** — Position, rotation, and data overrides no longer lost on save
- **Disconnected spawner management** — Disconnected spawners stop simulating, tabs dim visually, right-click Enable/Disable menu

### v0.3.15 - Duplicate Tab & Backup
- **Duplicate Tab** — Right-click a spawner tab to duplicate it with all settings
- **Backup to Zip** — File menu option to zip entire mod structure (spawners, system, textures)
- **SoftParticlesFadeFactor range fix** — Slider now correctly capped at 2.0 (Hytale maximum)

### v0.3.14 - Tab Bar & Performance Fixes
- **Tab bar scrolling** — Tabs no longer overflow off-screen with many spawners open (horizontal scroll + mouse wheel)
- **Blueprint performance fix** — Blueprint view with 50+ keyframes no longer drops to 1 FPS
- **Keyframe deselect** — Click empty space in animation editor to deselect
- **Flow map error handling** — Missing distortion textures show error instead of silent failure
- **Soft particles visibility fix** — Soft particles no longer nearly invisible in editor preview
- **Initial frame scale enforcement** — Game forces initial frame scale across all frames, editor now matches
- **Precision improvements** — Keyframe sliders, DragValue, and global scale now use 0.01 precision
- **New keyframe inheritance** — New animation frames inherit global color and scale settings

### v0.3.13 - Import & System Fixes
- **FrameSize auto-resolution** — Frame size automatically set from texture dimensions on import (no more "cut in half" particles)
- **SpawnerReference overrides applied** — Position, rotation, and data overrides from system references now work in simulation
- **UVMotion.AddRandomUVOffset preserved** — Field no longer silently dropped on import/save

### v0.3.12 - Burst+Loop Fix
- **Burst+Loop coexistence** — Beam spawners (Flamethrower, etc.) no longer broken on import. SpawnBurst with Loop is a valid Hytale pattern

### v0.3.11 - Apply to Animation Fix
- **"Apply to Animation" now distributes all sprite frames** — Previously only created keyframes at 0% and 100%. Now distributes all selected frames evenly across the timeline (e.g., 8 frames → 0%, 14%, 29%, 43%, 57%, 71%, 86%, 100%)
- **Frame selection resets on texture/frame_size change** — Previously kept stale selection when switching textures

### v0.3.10 - Animation Presets & Static Plane
- **3 simple animation presets** — "1-Frame", "2-Frame", "3-Frame" sort at top of presets list for quick access
- **Static Plane template** — Single particle that stays forever (like a TV screen or sign), available in Ui_Feedback category and "+" dropdown menu
- **Rain templates updated** — Billboard mode, gravity via attractor, infinite particles

### v0.3.9 - Easing & Frame Index Fix (FRAUD FIX)
- **30+ easing functions now work** — Linear, Quad, Cubic, Quart, Quint, Sine, Expo, Circ, Back, Elastic, Bounce (In/Out/InOut variants)
- **Frame index keyframe interpolation** — Sprite sheet animations now actually animate across keyframes (was broken)

### v0.3.8 - Rotation Interpolation Fix (FRAUD FIX)
- **Rotation keyframes now interpolate** — Previously rotation was set once at spawn and never changed. Now properly lerps between keyframe rotation values

### v0.3.7 - FlipU/FlipV & Frame Size Improvements
- **FlipU and FlipV UV options now work** — Previously did nothing (fraud)
- **Auto-set Frame Size on texture selection** — Automatically sets width/height to texture dimensions
- **Frame Size max increased to 16K** — Was 512, then 8192, now 16384
- **DragValue input fixed** — No longer accepts partial input while typing

### v0.3.6 - Texture Loading & Frame Size Fixes
- **Browse button texture selection fixed** — Textures selected via Browse now load correctly
- **Frame Size max increased to 8K** — Was artificially capped at 512
- **"File not found" false positive fixed** — UV atlas frame selector no longer hidden for valid textures

## Features

### Core
- **Real-time 3D Preview** — GPU-accelerated particle rendering with wgpu
- **Hytale JSON Format** — loads and saves `.particlespawner` and `.particlesystem` files using Hytale's PascalCase JSON format (partial field coverage — not all Hytale fields are supported yet)
- **Tab-based Editing** — edit multiple spawners simultaneously, each with independent simulation
- **Particle System Support** — edit `.particlesystem` files with multiple spawner references
- **Undo/Redo** — per-tab undo history (Ctrl+Z / Ctrl+Y)
- **Auto-save** — 60-second interval automatic saving
- **Recent Files** — quick access to previously opened files

### Editing Modes
- **Properties View** — traditional form-based editing with Hytale-style widgets (gold accent rows, diamond sliders, min/max range controls)
- **Blueprint View** — node-based visual editing with 12 node types:
  - Spawner, Emission, Spatial, Velocity, Effects, Appearance, Render, Particle, Attractor, Keyframe, Initial Frame, Collision Frame
  - Drag-drop node creation from pin connections
  - Copy/paste nodes (Ctrl+C/V)
  - Wire disconnect (Alt+click or right-click pin)

### Keyframe Animation
- **Visual Timeline** — diamond keyframes on a percentage-based timeline, colored by keyframe color
- **9-Property Grid** — Time, Opacity, Color, Scale X/Y, Rotation Z, Frame Index, Easing, Curve Preview
- **30+ Easing Types** — Linear, Quad, Cubic, Quart, Quint, Sine, Expo, Circ, Back, Elastic, Bounce (In/Out/InOut variants) with curve preview
- **Global Scale Multiplier** — proportionally scale all keyframe Scale values (0.1x–3.0x)
- **Global Color Picker** — set color on all keyframes at once
- **55 Animation Presets** — Presets with organic min/max variation across 7 categories:
  - Quick Access (3): 1-Frame, 2-Frame, 3-Frame
  - Opacity (6), Scale (5), Squash/Stretch (3), Rotation (6), Color (9), Combined (16), Action (7)
- **Animation Preset Browser** — search, sort, apply, save, and delete custom presets

### Template Library
- **227 Particle Templates** across 28 categories:
  - Combat (Melee, Ranged), Magic (Fire, Ice, Lightning, Earth, Water, Nature, Light, Dark)
  - Status Effects, Environment, UI/Feedback, Space, Steampunk, Weapons
  - Smoke, Atmospheric, Clouds, Weather, Storms, Space Weather
  - Creatures, Construction, Liquids, Portals, Trails
- **Template Browser** — searchable, filterable by category

### Help System
- **F1 Help Window** — 100 documented fields across 16 categories with confidence ratings
- **[?] Tooltips** — every field has a help button with description, how-to-use, examples, and tips
- **Word Cloud Home** — clickable field overview sorted by confidence
- **Guided Walkthroughs** — "Your First Particle Spawner" and "Your First Particle System" guides

### Additional Features
- **Texture Gallery** — visual texture picker with thumbnail grid, search, and custom folder monitoring
- **Code Viewer** — real-time JSON preview of current spawner/system
- **Statistics** — lifetime usage tracking (particles spawned, files saved, time in editor)
- **100 Achievements** — across 6 categories (Getting Started, Creation, Mastery, Explorer, Persistence, Secret)
- **Diagnostic Log** — optional file logging (View > Panels > Diagnostic Log)
- **Screenshot Export** — save preview to PNG
- **GIF Recording** — record and export particle animations

## Installation

1. Download the latest release
2. Extract the folder — it contains:
   - `vfxtale.exe` — the application
   - `Particles/Textures/` — 42 bundled textures across 9 categories
   - `templates/` — 226 particle templates + 52 animation presets
3. Run `vfxtale.exe`

## Usage

1. **File > Open** to load a Hytale `.particlespawner` or `.particlesystem` file
2. Edit properties in the Properties View or Blueprint View (toggle via toolbar)
3. View real-time preview in the 3D viewport
4. **File > Save** to save changes

### Preview Controls

| Control | Action |
|---------|--------|
| Left-click + drag | Rotate camera |
| Right-click + drag | Pan camera |
| Scroll wheel | Zoom (when hovering preview) |
| W/S | Move forward/back |
| A/D | Move left/right |
| Q/E | Move down/up |
| Space | Play/Pause |
| R | Restart simulation |

### Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| Ctrl+N | New Spawner |
| Ctrl+O | Open File |
| Ctrl+S | Save |
| Ctrl+Shift+S | Save As |
| Ctrl+W | Close Tab |
| Ctrl+Z | Undo |
| Ctrl+Y | Redo |
| Ctrl+E | Export to Mod |
| Ctrl+G | Export GIF |
| F1 | Help |
| Delete | Delete selected node (Blueprint) |

## Hytale Mod Export

Use **File > Export to Mod** to create a complete mod folder:
- `Common/Particles/Textures/` — referenced textures
- `Server/Particles/` — system and spawner JSON files

VFXTale automatically applies Hytale naming convention: `smoke_3` becomes `Smoke_3`.

## Bundled Textures

42 textures included in `Particles/Textures/` across 9 categories:

| Folder | Contents |
|--------|----------|
| Basic | General-purpose particle textures (Glow, Spark, etc.) |
| Debris | Debris and fragment textures |
| Fire | Flame and ember textures |
| Ice | Ice crystal and frost textures |
| Liquid | Liquid drop and splash textures |
| Nature | Leaf, pollen, and organic textures |
| Smoke | Smoke and cloud textures |
| UVMotion | UV distortion flow maps |
| Weather | Rain, snow, and weather textures |

## Requirements

- Windows 10/11
- GPU with Vulkan, DirectX 12, or Metal support

## Building from Source

```bash
cd vfxtale
cargo build --release
```

Binary will be at `target/release/vfxtale.exe`

## License

GPL-3.0 License - See LICENSE file for details.

## Credits

- **CyberAxe** — Development
- Built with [egui](https://github.com/emilk/egui) and [wgpu](https://github.com/gfx-rs/wgpu)

---

*VFXTale is a fan-made tool and is not affiliated with Hypixel Studios or Hytale.*
