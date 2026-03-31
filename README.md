# SurfaceMap

**A free, browser-based projection mapping tool for live performance, art installations, and education.**

SurfaceMap lets you map video onto irregular physical surfaces using quad-corner warping, freehand masks, and real-time dual-window output — all from a single HTML file. No installation, no accounts, no subscriptions.

## Features

- **Quad warping** — Drag corner handles to warp video onto any flat surface
- **Multiple video sources** — Load up to 10+ videos simultaneously
- **Freehand masking** — Paint masks with a soft-edged brush to hide or reveal areas
- **Shape masks** — Circle, ellipse, and polygon masks with adjustable feathering
- **Dual-window output** — Edit on your laptop while a separate output window drives the projector, with real-time sync
- **Synced playback** — Set delay offsets per surface and trigger everything with one Play All button
- **Surface snapping** — Corners snap to other surfaces' edges and corners for precise alignment
- **Bright mode** — Flood the projector with light to see exactly where the throw reaches
- **Save/Load projects** — Save your entire setup as a `.surfacemap` file and reload it later
- **Undo** — Ctrl/⌘+Z to undo corner and move changes
- **Auto-transcode** — Drop in AVI, MKV, WMV, or other formats and they auto-convert to MP4 via in-browser FFmpeg
- **Mac-optimized** — Keyboard shortcuts and fullscreen methods designed for macOS and Windows

## Quick Start

### Use it online

If this repo is hosted on GitHub Pages, just visit the URL and start mapping:

```
https://troybriggsis-arch.github.io/surfacemap/
```

### Use it locally

1. Download `index.html`
2. Open it in Chrome, Edge, or Firefox
3. That's it — it's a single self-contained file

> **Note:** When running from a local file, the FFmpeg auto-transcode feature won't work due to browser security restrictions. Use MP4 or WebM videos, or serve the file with a local server (`python3 -m http.server`).

## How to Use

### 1. Add videos
Drag & drop video files onto the window, or click **⊕ Video**. MP4 and WebM work natively in all browsers. Other formats (AVI, MKV, WMV, etc.) are automatically converted.

### 2. Create surfaces
Click **⊕ Surface** to add a projection quad. Each surface is a four-cornered shape you can warp.

### 3. Assign and position
Use the dropdown on each surface to assign a video. Drag the blue corner handles to warp the video onto your physical surface. Click inside a surface to drag the whole quad.

### 4. Mask (optional)
Select a mask type (Circle, Ellipse, Polygon, or Freehand) to clip the video to a specific shape. Click **Edit** to open the mask editor. Use the brush to hide areas and the eraser to reveal them. Adjust feather for soft edges.

### 5. Connect your projector
- Connect your projector as an **extended display** (not mirrored)
- Click **⧉ Output Window** to open a second browser window
- Drag the output window onto the projector display
- Mac: click the green ⊕ button or press **Ctrl+⌘+F** to fullscreen
- Windows: press **F11** to fullscreen

### 6. Fine-tune live
All edits in the main window update the projector output in real-time. Use **☀ Bright** mode to see the full projector throw while positioning. Toggle it off when you're ready to go live.

### 7. Sync playback
Set a **Delay** (in seconds) on each surface for staggered starts, then hit **▶ Play All**. All videos loop automatically.

## Keyboard Shortcuts

| Key | Action |
|-----|--------|
| `F` | Toggle output window |
| `B` | Toggle bright mode |
| `S` | Toggle surface snapping |
| `L` | Lock/unlock all surfaces |
| `D` | Duplicate selected surface |
| `Delete` / `Backspace` | Remove selected surface |
| `Space` | Play/pause all videos |
| `⌘Z` / `Ctrl+Z` | Undo last corner/move change |
| `⌘S` / `Ctrl+S` | Save project |
| `⌘O` / `Ctrl+O` | Load project |

## Deploy Your Own

### GitHub Pages (free)

1. Fork this repo (or create a new one and copy `index.html`)
2. Go to **Settings → Pages**
3. Set source to **Deploy from a branch** → **main** → **/ (root)**
4. Your site will be live at `https://YOUR-USERNAME.github.io/surfacemap/`

### Any web server

Just serve `index.html`. There are no build steps, no dependencies, no `npm install`. It's one file.

## Technical Details

- **Single HTML file** — all CSS, JS, and markup in one portable file (~3,100 lines)
- **WebGL-free** — uses CSS `matrix3d` transforms for hardware-accelerated warping (works on integrated GPUs)
- **Video decoding** — leverages the browser's native video decoder for playback; supports ~10 simultaneous streams on modern hardware
- **Masking** — uses CSS `mask-image` with dynamically generated data URLs
- **FFmpeg** — uses [ffmpeg.wasm](https://github.com/ffmpegwasm/ffmpeg.wasm) for in-browser video transcoding (loaded on-demand, ~25MB)
- **No backend** — everything runs client-side. No data leaves the browser.

## Browser Support

| Browser | Status |
|---------|--------|
| Chrome / Edge | ✅ Full support |
| Firefox | ✅ Full support |
| Safari | ⚠️ Works, but output window may require manual fullscreen via green button |

## Contributing

Contributions welcome! Some ideas for future work:

- **Mesh warp grid** — Subdivide quads into a fine grid for projecting onto curved surfaces
- **Electron wrapper** — Desktop app with native multi-monitor detection
- **MIDI/OSC control** — Trigger cues from lighting consoles or controllers
- **Solo mode** — Mute all surfaces except one for testing
- **Bezier edge masking** — Curved mask edges for organic shapes
- **Video effects** — Brightness, contrast, hue rotation per surface

## License

MIT — free for personal, educational, and commercial use. See [LICENSE](LICENSE).

## Credits

Built for educators and projection artists. If you use SurfaceMap in your teaching or work, we'd love to hear about it — open an issue or discussion to share!
