# VFXTale - Hytale Particle Editor

A visual particle effect editor for Hytale by CyberAxe.

## Features

- **Real-time 3D Preview** - GPU-accelerated particle rendering with wgpu
- **Full Hytale Compatibility** - Load and save native Hytale particle spawner JSON files
- **Keyframe Animation** - Visual timeline editor for particle animations
- **Blueprint View** - Node-based visual editing (WIP)
- **Professional UI** - Hytale-inspired dark theme with gold accents

### Supported Particle Properties

| Property | Description |
|----------|-------------|
| `max_concurrent_particles` | Limit active particle count |
| `scale_ratio_constraint` | Lock uniform scale (OneToOne) |
| `attractor.radius` | Distance-limited attractor force |
| `frame_size` | Sprite sheet animation |
| `light_influence` | Particle lighting response |
| `render_mode` | Blend modes (Linear, Additive) |
| `linear_filtering` | Texture filtering toggle |
| `uv_option` | Random UV flip on spawn |
| `particle_rotation_influence` | Billboard orientation modes |

## Installation

1. Download the latest release from [Releases](../../releases)
2. Extract `vfxtale.exe` and the `textures/` folder to any folder
3. Run `vfxtale.exe`

### Bundled Textures

The release includes 15 bundled textures in the `textures/` folder:
- `element1.png` through `element15.png` - Cosmic pixel art textures

Use these as `Particles/Textures/elementN.png` paths in your particle spawners.

## Usage

1. **File > Open** to load a Hytale particle JSON file
2. Edit properties in the right panel
3. View real-time preview in the 3D viewport
4. **File > Save** to save changes

### Preview Controls

- **Left-click + drag** - Rotate camera
- **Scroll wheel** - Zoom (when hovering preview)
- **Space** - Play/Pause
- **R** - Restart simulation

## Hytale Mod Export

Use **File > Export to Mod** to create a complete mod folder with:
- `Common/Particles/Textures/` - Your particle textures
- `Server/Particles/` - System and spawner JSON files

VFXTale automatically applies Hytale naming convention (uppercase after `_`).

See **Help > Hytale Export** in-app for full documentation.

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

MIT License - See LICENSE file for details.

## Credits

- **CyberAxe** - Development
- Built with [egui](https://github.com/emilk/egui) and [wgpu](https://github.com/gfx-rs/wgpu)

---

*VFXTale is a fan-made tool and is not affiliated with Hypixel Studios or Hytale.*
