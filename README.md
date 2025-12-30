# LinkDrop Site

Static landing page + privacy policy for the LinkDrop Chrome extension. Built with plain HTML/CSS and ready to serve from GitHub Pages.

## Preview
- Home: `index.html`
- Privacy: `privacy.html`
- OG/SEO assets: `og-image.png` (source `og-image.svg`), `favicon.svg`, `apple-touch-icon.png`, `robots.txt`, `sitemap.xml`, `404.html`

## Local preview
Just open `index.html` in a browser. No build step.

## Regenerate the OG image
If you tweak `og-image.svg`, export the PNG with the same gradient/icon styling:
```sh
DYLD_LIBRARY_PATH=/opt/homebrew/lib python - <<'PY'
import cairosvg
cairosvg.svg2png(url='og-image.svg', write_to='og-image.png', output_width=1200, output_height=630)
PY
```

## Deploy to GitHub Pages
1) GitHub → `Settings` → `Pages`  
2) Source: `Deploy from a branch` → Branch: `main` → Folder: `/ (root)` → Save  
3) Wait for the `github-pages` action to finish; the site will be at `https://<username>.github.io/<repo>/`.
4) If the public URL changes, update canonical/OG URLs in `index.html`, `privacy.html`, and `sitemap.xml`.
5) Optional custom domain: add a `CNAME` file (one line with your domain), configure DNS to CNAME `<username>.github.io`, and set the domain in Pages settings.

## Manual extension install (from the main project)
- Edit the extension config (`src/config.js`) to point `EDGE_BASE_URL` at your Supabase project.
- Chrome → Extensions → Developer mode → “Load unpacked” → select the repository root.
- Open the popup once to register the device.

## Repo structure
- `index.html` — landing page
- `privacy.html` — privacy policy
- `style.css` — shared styles
- `og-image.svg/png`, `favicon.svg`, `apple-touch-icon.png` — branding assets
- `robots.txt`, `sitemap.xml`, `404.html` — Pages/SEO support
