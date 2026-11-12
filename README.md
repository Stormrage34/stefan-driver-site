# Stefan Angelovski — driver profile site

A one page site for direct hire as a C+E driver in the Benelux, Germany and Denmark. Static HTML, one file, no build step, no third party requests: the Geist webfont is served from this folder.

## Files

    index.html                      the page (markup, CSS and JS in one file)
    404.html                        branded not found page
    TOKENS.md                       design tokens, ready to rebuild in Figma
    assets/favicon.svg              amber dot mark
    assets/og.png                   social sharing image, 1200x630
    assets/og.svg                   source for the above
    assets/portrait.jpg             hero portrait, 800x1000, EXIF stripped
    assets/portrait-480.jpg         smaller source for narrow screens
    assets/Stefan-Angelovski-CV.pdf the CV the download link serves
    assets/fonts/                   Geist variable woff2, latin + latin-ext

## View it

Open `index.html` in a browser. That is the whole setup. For a local server, if you want the 404 page to resolve:

    python3 -m http.server 8000

then visit `http://localhost:8000`.

## Deploy

Any static host works. For GitHub Pages, push the folder to a repository, then Settings → Pages → deploy from the `main` branch root. For Netlify or Cloudflare Pages, drag the folder onto the dashboard.

Before going live, set absolute URLs for `og:image` and add `og:url` plus `<link rel="canonical">` — scrapers ignore relative paths. `assets/og.png` is already 1200×630.

## What to edit

| What | Where |
|---|---|
| Email address | the two `mailto:` links and `form` submit handler |
| Phone number | the `tel:` link in the contact section |
| CV download | replace `assets/Stefan-Angelovski-CV.pdf` with the current PDF, keep the filename |
| Rates, routes, availability | the hero, the four benefit cards, the FAQ |

## Copy rules this page follows

No hyphens in visible copy, no italics, no words above semibold, no exclamation marks, no background gradients, sentence case headings. All type sizes land on the Tailwind scale and all spacing on the token table in `TOKENS.md`.

## Checks already run

- 1440px and 390px: no horizontal overflow, primary action above the fold, buttons hold their text.
- All computed font sizes land on the scale (12, 14, 16, 18, 20, 24, 30, 36, 48, 60).
- Contrast on the base surface: white 18.8:1, secondary 6.8:1, tertiary 5.4:1, accent 9.2:1.
- Form validation: empty submit marks three fields and reports inline; typing clears each one.
- Reveals and the tagline degrade to visible text when JavaScript or IntersectionObserver is missing.
- One h1, semantic sections, skip link, focus rings on every control, `prefers-reduced-motion` honoured.
- Mobile menu traps Tab, focuses the first link on open, closes on Escape and returns focus to the burger.
- Form button shows a loading state and restores itself, so the page stays usable if the mail client never opens.
- `Person` structured data validates as JSON and is read by the browser.
- No heading level jumps, no unnamed controls, no unlabeled inputs, every image has alt text.
- Anchor links land 88px clear of the floating nav (scroll-margin), smooth scroll only when motion is allowed.
- Touch targets: form button 48, FAQ row 76, panel links 60, footer links 44 (all measured at 390px).
- Form error line counts the fields that actually failed ("One field…" / "3 fields…").
- With JavaScript off, mobile still shows the nav links and hides the burger.
- Reading measure held at 51-73 characters per line on every long paragraph.
- All colour values come from tokens; no hardcoded hex outside `:root`.

## Not done here

No analytics, no cookie banner, no backend. The enquiry form opens the visitor's mail client with the message prefilled, so nothing is stored anywhere. If you later add a real form endpoint, wire it into the submit handler and delete the `mailto:` fallback.
