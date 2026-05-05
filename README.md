# 🎬 rec — Lightweight Screen Recorder (wf-recorder + FFmpeg)

A minimal CLI tool to record your screen on Wayland using wf-recorder and compress the result with FFmpeg.

Built for speed, simplicity, and small output size.

---

## ✨ Features

- 📺 Record full screen, selected area, or a window
- ⚡ Fast encoding during capture
- 🗜️ Automatic compression after recording
- 🧠 Simple CLI interface
- 🐧 Wayland-friendly

---

## 📦 Requirements

Make sure these are installed:

- wf-recorder
- FFmpeg
- `slurp` (for area/window selection)

### Install (Ubuntu / Debian-based)

```bash
sudo apt install wf-recorder ffmpeg slurp
```

---

## 🚀 Installation

1. Save the script as `rec`:

```bash
mkdir -p ~/bin
nano ~/bin/rec
```

2. Paste the script and save

3. Make it executable:

```bash
chmod +x ~/bin/rec
```

4. Create a symlink:

```bash
sudo ln -s ~/bin/rec /usr/local/bin/rec
```

---

## 🧑‍💻 Usage

```bash
rec [mode]
```

### Modes

| Mode   | Description          |
| ------ | -------------------- |
| `full` | Record full screen   |
| `area` | Select custom region |
| `app`  | Select a window      |

### Examples

```bash
rec            # default (area)
rec area       # select region
rec full       # full screen
rec app        # pick a window
```

---

## ⚙️ How It Works

### 1. Recording

Uses:

```bash
wf-recorder
```

- Captures screen based on selected mode
- Saves raw video to `/tmp`

---

### 2. Compression

Uses:

```bash
ffmpeg
```

Settings:

- `-crf 28` → smaller file size
- `-preset veryfast` → quick processing
- `-movflags +faststart` → web-friendly playback

---

## 📁 Output

Videos are saved to:

```bash
~/Videos/
```

Format:

```bash
rec_YYYY-MM-DD_HH-MM-SS.mp4
```

---

## 🧠 Notes

- Wayland does **not support true window capture**
  → `app` mode is region-based selection using `slurp`

- Audio is not included by default
  → add `--audio=default` if needed

---

## 🔧 Customization

### Change quality

Edit:

```bash
-crf 28
```

Lower = better quality, larger size
Higher = smaller size, lower quality

---

### Change framerate

```bash
-r 30
```

---

### Change bitrate (recording phase)

```bash
-b 2500k
```

---

## ⚡ Tips

- Keep recordings short → faster compression
- Use `area` for focused content
- Avoid unnecessary full screen capture

---

## 🧼 Cleanup

Temporary files are stored in:

```bash
/tmp
```

Automatically removed after processing.

---

## 📜 License

Use it, modify it, break it, improve it.

---

## 😏 Final Thoughts

This is not OBS.
This is a **fast, scriptable, dev-friendly recorder**.

If you want:

- automation
- CLI workflow
- minimal overhead

This gets the job done.
