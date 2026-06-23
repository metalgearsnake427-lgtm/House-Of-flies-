# House of Flies

**House of Flies** is an offline, single-file dystopian detective visual novel. It is designed for a browser first: desktop PCs, older integrated-graphics machines, and Android-sized screens.

The project uses only browser-native technology:

- HTML
- CSS
- JavaScript
- Inline SVG portrait plates
- Web Audio API
- `localStorage` save slots

No framework, package manager, remote server, or external asset download is required.



## Features

- Five case files with separate investigation states
- Local save slots and per-case progress memory
- Branching scene choices, leads, evidence, interrogation vectors, and accusation routes
- Cut-up reconstruction boards that persist in the active save
- A 200-volume archive with on-demand reading pages
- Responsive layouts for desktop, Android portrait, Android landscape, and tablet screens
- Accessibility and hardware settings: text size, reduced motion, high contrast, and low-hardware mode
- Browser-native audio with separate Master, Text, UI, and Ambience controls

> Audio is armed after the first tap/click because browsers restrict automatic sound playback.



## Run locally

Download or clone the repository, then open `index.html` in a modern browser.

bash
# Optional local server for development
python3 -m http.server 8080


Then open `http://localhost:8080` in your browser.

The game also works by opening `index.html` directly, but a local server is better for browser testing.



## Controls

| Action | Desktop | Android / Touch |
| --- | --- | --- |
| Finish active text block | Click text, `Space`, or `Enter` | Tap text |
| Move to the next text block | Click again or use **Next Line** | Tap again or use **Next Line** |
| Return to a prior block | **Previous Line** | **Previous Line** |
| Open case systems | Menu buttons | Bottom navigation and menu buttons |
| Change sound/accessibility options | **Settings** | **Settings** |

The visible `Previous Line`, `Complete Text`, and `Next Line` controls are the reliable way to read at your own pace on all screen sizes.



## Performance notes

The game deliberately avoids external images, video, and web fonts. Portraits and interface art are inline vector/SVG resources, and the archive generates only the active reading page instead of keeping every page in memory.

For older PCs or lower-end Android devices:

1. Open **Settings**.
2. Enable **Low Hardware**.
3. Enable **Reduced Motion** if animation feels distracting or slow.
4. Lower the text-speed setting only if desired; it does not change the game’s frame rate.



## Saving

Save data is stored in the browser using `localStorage`.

- Clearing browser/site data removes local saves.
- Different browsers and devices have separate save data.
- Use **Export Current Slot** in Settings to make a manual JSON backup.



## Publish on GitHub

Create a new repository named `house-of-flies`, then run:

bash
git init
git add .
git commit -m "Initial House of Flies build"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/house-of-flies.git
git push -u origin main


For a browser release, publish the repository through GitHub Pages with `index.html` at the repository root.



## Project structure

text
House-of-Flies/
├── index.html                 # Complete playable game
├── README.md                  # Project overview and publishing notes
├── LICENSE                    # MIT license
├── .gitignore                 # Local/editor exclusions
├── .gitattributes             # Consistent line endings
├── assets/
│   └── house-of-flies.svg     # Repository/favicon mark
└── docs/
    ├── DEVELOPMENT.md         # Editing and debugging notes
    ├── ANDROID.md             # Android WebView wrapper notes
    └── CHANGELOG.md           # Current build summary




## Development

See [docs/DEVELOPMENT.md](docs/DEVELOPMENT.md) for safe editing guidance and [docs/ANDROID.md](docs/ANDROID.md) for wrapping the web build in a native Android app project.


## License

Released under the [MIT License](LICENSE).

Copyright © 2026 Dunkyatchkovesh
