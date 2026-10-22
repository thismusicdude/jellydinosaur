# Build notes

Not required to just run the app: `index.html` at the repo root is ready to use. This is only
needed if you want to regenerate the minified bundle.

## Minified bundle (`upload/`)

```bash
node build-minify.js
```

Regenerates `upload/index.html` (minified `index.html`). Requires Node.js with internet access on
first run (uses `npx` to fetch Terser on demand for JS minification; no other network access
happens).

Kept deliberately conservative to never break ES3/old-browser compatibility:
- JS is minified with Terser targeting `ecma=5` explicitly, with `arrows`/`arguments`/`typeofs`
  transforms disabled — nothing that could introduce syntax newer than what's already in the
  source (which is plain ES3 to begin with).
- CSS/HTML are only whitespace-collapsed and comment-stripped, not restructured — no aggressive
  HTML minifier that could alter markup semantics (e.g. the file relies on real spaces between
  some inline elements, like `</span> <input>`, which a naive minifier would strip and visually
  break).

Run this after any change to `index.html`, to keep `upload/` in sync.
