# VFXTale by CyberAxe - A Hytale Particle Generator

A visual particle effect editor for Hytale, built with Rust + egui + wgpu.
Load, edit, preview, and save native Hytale `.particlespawner` and `.particlesystem` JSON files.

**Current Version: 0.3.4** - Beta

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
- **6 Easing Types** — Linear, EaseIn, EaseOut, EaseInOut, BounceOut, ElasticOut with curve preview
- **Global Scale Multiplier** — proportionally scale all keyframe Scale values (0.1x–3.0x)
- **Global Color Picker** — set color on all keyframes at once
- **52 Animation Presets** — Presets with organic min/max variation across 7 categories:
  - Opacity (6), Scale (5), Squash/Stretch (3), Rotation (6), Color (9), Combined (16), Action (7)
- **Animation Preset Browser** — search, sort, apply, save, and delete custom presets

### Template Library
- **226 Particle Templates** across 27 categories:
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
