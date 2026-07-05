# Personal Website

My personal website — a single-page static site built with plain HTML, CSS, and JS. No build step required.

## Local preview

Just open `index.html` in a browser, or serve it locally:

```
python3 -m http.server 8000
```

Then visit `http://localhost:8000`.

## Deploying to GitHub Pages

1. Push this repo to GitHub.
2. Go to **Settings → Pages**.
3. Under "Build and deployment", set source to `Deploy from a branch`, branch `main`, folder `/ (root)`.
4. Save — the site will be live at `https://<username>.github.io/<repo>/` within a minute or two.

## Customizing

- Edit content directly in `index.html` (name, tagline, about, projects, contact links).
- Colors and layout live in `style.css` (see the `:root` variables at the top for quick theme tweaks).
- `script.js` handles the mobile nav toggle and the footer year.
