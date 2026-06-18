# Aurora

A single-page WebGL silk-wordmark demo: a cursor-reactive variable-weight
**AURORA** wordmark floating over a hand-written GLSL "aurora silk" shader
background.

## Run locally

It's one file — open `index.html` in a browser, or serve it:

```sh
python3 -m http.server
```

## Stack

Plain HTML/CSS/JS, no framework. Fonts: Fraunces + Inter (Google Fonts).
The background is a hand-written GLSL fragment shader (domain-warped fbm)
rendered on a single full-screen triangle, capped for efficiency (DPR ≤ 0.66,
≤ 1.2 MP, low-power hint, hidden-tab pause) and with a reduced-motion /
no-WebGL fallback.

## Interaction model

- **Desktop:** the cursor is a cool light on the silk; AURORA's letters swell
  in weight toward it (Fraunces variable font, per-letter).
- **Mobile (no cursor):** the finger is the cursor while touching (with a
  2.5 s linger); every tap fires a light pulse at the touch point; when nobody
  touches, the light tours the page on waypoints and the letters run a slow
  breathing wave.
- `prefers-reduced-motion` disables all of it; the page stays static.
