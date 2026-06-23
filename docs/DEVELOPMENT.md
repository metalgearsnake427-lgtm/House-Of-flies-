# Development Notes

## Keep the game single-file

`index.html` intentionally contains the complete playable game. Its styles, JavaScript, inline SVG portrait data, and audio logic remain together so the project can run offline from one file.

When changing it:

1. Preserve the viewport meta tag.
2. Keep all save-state migrations defensive; old saves may exist in local browsers.
3. Test with JavaScript disabled? No — this game requires JavaScript, but it should fail visibly rather than leaving a blank loader.
4. Keep resource-loading timeouts. A failed portrait decode must never hold the loader forever.
5. Test both portrait and landscape phone widths.

## Minimum test matrix

- Desktop: 1366×768
- Android portrait: 360×640 and 390×844
- Android landscape: 844×390
- Tablet: 768×1024

## Syntax check

Extract inline script blocks and run Node’s parser check:

```bash
python3 - <<'PY'
from pathlib import Path
import re
html = Path('index.html').read_text(encoding='utf-8')
scripts = re.findall(r'<script(?:\s[^>]*)?>(.*?)</script>', html, re.S | re.I)
Path('.syntax-check.js').write_text('\n\n'.join(scripts), encoding='utf-8')
PY
node --check .syntax-check.js
rm .syntax-check.js
```

## Design rules

- Avoid remote fonts, CDNs, and asset URLs.
- Prefer CSS transforms and opacity for loops.
- Disable expensive loops in Low Hardware and Reduced Motion modes.
- Keep touch targets at least 44 CSS pixels high when possible.
- Make all narration readable without sound.
