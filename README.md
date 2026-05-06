# stingray

Landing page for **stingray** — a digital advertising agency based in Dbayeh, Lebanon.

> *Ads that leave a **mark**.*

A single-page experience built around the brand's *kings of the digital seas* identity. The hero is a WebGL particle stingray sampled from the official emblem silhouette, opened by a ~9-second cinematic intro sequence inspired by application launch experiences.

---

## Stack

- **Vanilla HTML, CSS, JavaScript** — no framework, no build step
- **[Three.js r128](https://threejs.org/)** — WebGL particle stingray + plankton field (loaded from CDN)
- **[Poppins](https://fonts.google.com/specimen/Poppins)** — official brand font, loaded from Google Fonts
- **[JetBrains Mono](https://fonts.google.com/specimen/JetBrains+Mono)** — system HUD typography during intro

## Brand

| Token       | Value      |
| ----------- | ---------- |
| Primary     | Bluebonnet `#2423e0` |
| Background  | True black `#000000` |
| Text        | White `#ffffff` |
| Font        | Poppins (300, 400, 500, 600, 700, 800) |
| Wordmark    | `stingray` (lowercase, Poppins ExtraBold) |

## Project structure

```
stingray-landing/
├── index.html
├── assets/
│   └── images/
│       ├── emblem-light.png       # Inverted-luminance emblem for dark backgrounds
│       ├── emblem-dark.png        # Original black emblem for light backgrounds
│       ├── emblem-light-sm.png    # Small inverted emblem for nav (over dark)
│       └── emblem-dark-sm.png     # Small black emblem for nav (over white)
├── README.md
├── LICENSE
└── .gitignore
```

## Sections

1. **Intro** — ~9-second WebGL boot sequence (assemble → reveal → handoff)
2. **Hero** — Slogan, sub-tagline, CTA, four headline stats
3. **Marquee** — Rotating brand keywords
4. **Services** — Six performance-marketing disciplines
5. **Manifesto** — *The Stingray Doctrine* (pulled from the brand book name rationale)
6. **Testimonials** — Real client quotes (Ultron, Innowise, LN Educational)
7. **Partners** — Polygon, techstars, IDSG, Avenue Capital, Y Combinator + others
8. **CTA** — *Ready to leave a mark?* call-to-action
9. **Footer** — Office address (Dbayeh Waterfront, Lebanon), site map

## Local development

The page is fully static — no build, no dependencies to install. Open `index.html` directly in any modern browser, or run a tiny local server for proper relative-path handling:

```bash
# Python
python3 -m http.server 8000

# Node
npx serve

# PHP
php -S localhost:8000
```

Then visit `http://localhost:8000`.

## The intro sequence

The opening choreography runs in five phases over ~9 seconds:

| Time     | Phase        | What happens                                                          |
| -------- | ------------ | --------------------------------------------------------------------- |
| 0.0–1.4s | Void         | Black canvas. HUD lines type in. Status: *initializing core*.        |
| 1.4–4.0s | Assembly     | Particles stream in from a hemisphere shell behind the camera; status rolls through *connecting → calibrating → welcome*; camera dollies from z=11.5 to z=9. |
| 4.0s     | Lock         | Flash burst as particles snap into formation.                         |
| 4.2–5.7s | Brand reveal | Eyebrow, wordmark (letter-by-letter 3D drop), and tagline appear.    |
| 5.7–7.5s | Hold         | Brand identity holds while the stingray gently swims in place.       |
| 7.5–8.9s | Handoff      | Stingray glides to hero pose; intro UI fades; hero text cascades in. |

Tuning lives in the `INTRO` constants block inside `index.html` (search for `const INTRO`).

A **Skip intro** button is provided top-right; pressing it snaps directly to the hero state.

## Deploying

Any static host works. Pick one:

- **Vercel** — `vercel deploy` (or drag-and-drop the folder at vercel.com)
- **Netlify** — drag-and-drop the folder at netlify.com/drop
- **GitHub Pages** — push to `main` and enable Pages from the repository's *Settings → Pages*
- **Cloudflare Pages** — connect the GitHub repo at pages.cloudflare.com

## Browser support

Tested on current Chrome, Safari, Firefox, and Edge. Requires WebGL support for the 3D hero (graceful fallback: page loads, scrolls, and reads correctly without the particle scene if WebGL is unavailable).

## License

Proprietary — © stingray. All rights reserved. See [LICENSE](LICENSE).

The brand identity, name rationale, slogan ("Ads that leave a mark"), wordmark, and emblem are the property of stingray.

---

*Built with care. Lebanon · Dbayeh · Worldwide.*
