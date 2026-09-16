# Just Encode Whatever - hosting edition

This is the complete folder distribution of the standalone HTML app. No CDN,
external script, model, font, image, or WASM download is required. All runtime
dependencies are included in `assets/`. Only Gemini transcription uses an
external service.

## GitHub Pages

1. Extract this ZIP.
2. Upload **all extracted contents**, including `index.html`, `assets/`, and
   `.nojekyll`, to the folder used by your GitHub Pages site. Keep this layout.
3. Enable or use Pages for that branch/folder in the repository's settings.
4. Open the Pages URL in a full browser and enter your own Gemini API key.

The key starts empty and is used only in this tab. It is not included in this
package and the app does not write it to localStorage, sessionStorage, or files.
Avoid adding a private key to the public source code.

The app processes selected media locally. It finds nearby pauses for roughly
15-minute transcription sections, sends sections sequentially with the chosen
pause, and adjusts returned timestamps to the recording's timeline. Video
snapshots are created locally and have their own image/ZIP downloads.

## Local use

For a single file opened directly from disk, use the separate standalone HTML
download. This folder distribution should be served from a web server, because
browsers restrict workers and WASM reads from `file://` folder pages. A local
server works without internet after these files are on your device. Gemini
still needs an internet connection and your API key. This build does not install
a service worker or promise offline reloads of a GitHub Pages URL.

## Included files and licenses

- `index.html`: page markup and complete third-party notices.
- `assets/styles.css`: application styles.
- `assets/*.js`: page scripts, configuration, and the two worker scripts.
- `assets/ffmpeg-core.wasm`: full FFmpeg 0.12.10 decoder/processing runtime.
- `assets/fvad.wasm`: lightweight WebRTC/libfvad speech detector.
- `assets/THIRD-PARTY-NOTICES.txt`: complete copied license notices.
- `.nojekyll`: prevents unnecessary Jekyll processing on GitHub Pages.

The source/notice addresses in the license text are attribution only. They are
not application dependencies. FFmpeg is GPL-2.0-or-later; lamejs/LAME is LGPL;
WebRTC/libfvad is BSD-3-Clause. Preserve these notices when redistributing.

Native video preview and downloads depend on the browser's format support. The
included FFmpeg runtime supports fallback processing. Live Gemini requests were
not part of the automated offline validation.
