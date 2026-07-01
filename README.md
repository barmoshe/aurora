# Aurora

A single-file WebGL silk-wordmark template: a cursor-reactive variable-weight
**AURORA** wordmark floating over a hand-written GLSL "aurora silk" shader
background, followed by three template sections — Overview, Specimens
(interactive variable-font playground + shader palette), and About.

## Run locally

It's one file — open `index.html` in a browser, or serve it:

```sh
python3 -m http.server
```

## Stack

Plain HTML/CSS/JS, no framework, no build step, no dependencies.
Fonts: Fraunces + Inter (Google Fonts). The background is a hand-written GLSL
fragment shader (domain-warped fbm) rendered on a single full-screen triangle,
capped for efficiency (DPR ≤ 0.66, ≤ 1.2 MP, low-power hint, hidden-tab pause,
debounced resize) with reduced-motion / no-WebGL fallbacks and GPU
context-loss recovery.

## Page structure

- **Hero** — the wordmark over the silk, anchor nav, scroll cue.
- **Overview** — three cards explaining the silk, the wordmark, and the light.
- **Specimens** — a live weight slider on a Fraunces specimen, a weight
  waterfall, and the shader palette as copyable hex chips.
- **About** — what the template is for, how it degrades, and a facts list.
- A scroll-aware top bar fades in once the hero leaves the viewport;
  sections reveal on scroll via `IntersectionObserver`.

## Interaction model

- **Desktop:** the cursor is a cool light on the silk; AURORA's letters swell
  in weight toward it (Fraunces variable font, per-letter). The letter loop
  idles while the wordmark is off-screen.
- **Mobile (no cursor):** the finger is the cursor while touching (with a
  2.5 s linger); every tap fires a light pulse at the touch point; when nobody
  touches, the light tours the page on waypoints and the letters run a slow
  breathing wave.
- `prefers-reduced-motion` disables all of it — animations, reveals, and the
  shader; the page stays static and fully legible.

## Accessibility

Skip-to-content link, semantic landmarks and labelled sections, visible
`:focus-visible` styles everywhere, reduced-motion parity, and a top bar that
is `aria-hidden` (and untabbable) while off-screen.

## Make it yours

Rename the wordmark in the `<h1>`, retint the page via the CSS variables in
`:root`, and retint the silk via the three `col +=` constants in the fragment
shader.
