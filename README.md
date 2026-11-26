# ytpdf

A fast, lightweight Bash CLI tool that captures specific timestamps (`SS`, `MM:SS`, or `HH:MM:SS`) directly from YouTube video streams without downloading the entire video file, compiles the frames into a single PDF, and automatically cleans up all temporary files.

Built for students and self-learners who want clean, searchable PDF notes from long video lectures.

## Features
- **Zero Full-Video Downloads:** Uses `yt-dlp` stream URLs and `ffmpeg` keyframe seeking (`-ss` before `-i`) to capture frames in seconds, even from 3+ hour lectures.
- **Flexible Timestamp Input:** Supports `SS`, `MM:SS`, and `HH:MM:SS` formats separated by spaces, commas, or entered line-by-line.
- **Input Validation:** Built-in regex validation skips malformed timestamps before processing.
- **Auto-Cleanup:** Uses `trap` on `EXIT` so temporary files in `/tmp` are guaranteed to be deleted—even if an error occurs or you cancel mid-run.
- **Lossless PDF Compilation:** Uses `img2pdf` to wrap frames directly into a PDF without re-encoding or losing image quality.

## Requirements
- `bash`
- `ffmpeg`
- `yt-dlp`
- `img2pdf`

### Install Dependencies (Debian/Ubuntu)
```bash
sudo apt update && sudo apt install -y ffmpeg python3-pip
pip install --break-system-packages -U yt-dlp img2pdf
```

## Installation
```bash
git clone https://github.com/advaithjayesh/ytpdf
cd ytpdf
chmod +x ytpdf
mkdir -p ~/.local/bin && cp ytpdf ~/.local/bin/
```
*(Make sure `~/.local/bin` is in your `$PATH`.)*

## Usage
Run `ytpdf` from anywhere in your terminal:
```bash
ytpdf
```

## License
Copyright (C) 2026 advaithjayesh

Licensed under the **GNU General Public License v3.0 (GPL-3.0)** — see the [LICENSE](LICENSE) file for details.
