# travisgerke.com

Personal site. Hand-written HTML and CSS, no build step, no dependencies.

- `index.html` — the whole site
- `styles.css` — styling, with light/dark via `prefers-color-scheme`
- `assets/travis-gerke.jpg` — headshot
- `favicon.svg` — tab icon, plus `favicon.ico` and `apple-touch-icon.png` for browsers that skip SVG icons
- `CNAME` — custom domain for GitHub Pages

## Deploying

Push to `master`. GitHub Pages serves the repo root at [travisgerke.com](https://travisgerke.com).

## Local preview

Open `index.html` in a browser. That's it.

## Icons

`favicon.svg` is the source. `favicon.ico` and `apple-touch-icon.png` are rendered from it, so rebuild both if the monogram changes. Render with Chrome rather than `rsvg-convert`, which falls back to the wrong font for the lettering:

```bash
"/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" --headless=new --default-background-color=00000000 --window-size=512,512 --screenshot=/tmp/icon.png "file://$PWD/favicon.svg"
magick /tmp/icon.png -define icon:auto-resize=48,32,16 favicon.ico
magick /tmp/icon.png -background '#8f0d0d' -alpha remove -alpha off -resize 180x180 apple-touch-icon.png
```
