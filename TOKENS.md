# Design tokens

The page is built on the token system both skills define, so it can be rebuilt in Figma without re-deciding anything. Values here are the source of truth; the CSS variables at the top of `index.html` mirror them one to one.

## Colour

Dark mode only. Backgrounds come from the allowed dark set, never gradients.

| Token | Value | Used for |
|---|---|---|
| `Surface/Base` | `#131209` | page background |
| `Surface/Primary` | `#181818` | cards, contact panel |
| `Surface/Secondary` | `#1F1F1F` | steps, notes |
| `Surface/Tertiary` | `#272727` | hover fills, numerals |
| `Surface/Quaternary` | `#313131` | icon tiles |
| `Text/Primary` | `#FFFFFF` | headings, body on dark |
| `Text/Secondary` | `#9B9B9B` | supporting copy, hero gradient end |
| `Text/Tertiary` | `#8A8A8A` | metadata (5.44:1 on base, passes AA) |
| `Border/Subtle` | `rgba(255,255,255,.10)` | card and section rules |
| `Border/Strong` | `rgba(255,255,255,.18)` | inputs, ghost button |
| `Accent/Base` | `#F5A524` | primary button, markers, focus ring |
| `Accent/Hover` | `#FFB84D` | button hover fill |
| `Accent/Tint` | `rgba(245,165,36,.12)` | certificate tick chips |
| `Accent/Ink` | `#131209` | text on accent |
| `Error` | `#FF8A7A` | invalid field border and message |
| `Scrim/Heavy` | `rgba(19,18,9,.96)` | mobile menu backdrop |
| `Scrim/Light` | `rgba(19,18,9,.86)` | portrait caption pill |
| `Nav/Glass` | `rgba(24,24,24,.72)` | floating nav fill, blurred |
| `Line/Hover` | `rgba(255,255,255,.30)` | input hover border |

Contrast measured on `Surface/Base`: white 18.8:1, secondary 6.8:1, tertiary 5.4:1, accent 9.2:1, error 7.75:1, accent hover 10.9:1. Muted on `Surface/Tertiary` (nav hover fill) is the tightest pair at 5.37:1, still AA.

Hero heading gradient is the only gradient in the file, and it is on text only: `#FFFFFF → #9B9B9B`, left to right.

## Type

One family: **Geist**, a variable font (weight axis 100-900, used at 400/500/600), self hosted from `assets/fonts/` in latin and latin-ext. No italics, no weight above 600. `font-display: swap`.

| Style | Size / line height | Weight |
|---|---|---|
| Heading 1 | 60 / 60 | Semibold |
| Heading 2 | 48 / 48 | Semibold |
| Heading 3 | 36 / 40 | Semibold |
| Heading 4 | 30 / 36 | Semibold |
| Heading 5 | 24 / 32 | Semibold |
| Heading 6 | 20 / 28 | Semibold |
| Title 2 | 18 / 28 | Medium |
| Title 3 | 16 / 24 | Medium |
| Body 3 | 16 / 24 | Regular |
| Body 5 | 14 / 20 | Medium |
| Body 6 | 14 / 20 | Regular |
| Button md | 16 / 24 | Semibold |
| Button sm | 14 / 20 | Semibold |
| Caption 2 | 14 / 20 | Regular |
| Caption 4 | 12 / 16 | Medium |

Mobile snaps down the scale rather than inventing sizes: Heading 1 → 48 at 900px, → 36 at 640px. Heading 2 → 36, then 30.

## Spacing

Only these values, used for both padding and gap.

| Token | Value |
|---|---|
| Spacing-25 | 2 |
| Spacing-50 | 4 |
| Spacing-75 | 8 |
| Spacing-100 | 12 |
| Spacing-200 | 16 |
| Spacing-300 | 24 |
| Spacing-400 | 32 |
| Spacing-500 | 40 |
| Spacing-600 | 48 |
| Spacing-700 | 64 |
| Spacing-800 | 80 |
| Spacing-900 | 96 |

Section rhythm: 96 above and below on desktop, 64 at 900px and below. Card padding 32, step padding 32, contact panel 48.

## Radius

| Token | Value | Used for |
|---|---|---|
| radius/sm | 4 | focus ring |
| radius/lg | 8 | inputs, icon tiles, numerals |
| radius/xl | 12 | certificate rows, buttons |
| radius/2xl | 16 | cards, steps |
| radius/3xl | 24 | contact panel |
| radius/full | 9999 | nav pill, badges, dots |

Nested radius rule applied: the hero buttons sit inside nothing, so they take 12; the tick tile at 8 sits inside a row at 12 with 24px gap, so the formula (inner = outer − gap) permits 8 unchanged. Cards at 16 contain only unrounded text.

## Components to build in Figma

1. **Button** — primary and ghost, sizes md and sm, states: default, hover, active (`scale .98`), focus (2px accent ring, 3px offset).
2. **Nav** — auto layout, padding 8, radius full, fill `#181818` at 72%, layer blur 16, plus a burger variant with the two line states.
3. **Card** — padding 32, radius 16, fill `Surface/Primary`, 1px `Border/Subtle`, containing numeral tile, title, body.
4. **Cert row** — padding 24, radius 12, horizontal auto layout, 24px gap, 24px tick.
5. **FAQ row** — 24 padding top and bottom, 1px bottom rule, `+` and `–` affordance.
6. **Input** — padding 12/16, radius 8, three states: default, hover (`Line/Hover`), invalid (`Error` border plus inline message). Submit button in the form is 12/16 padding, full width.

Motion, for whoever rebuilds it: base curve `cubic-bezier(.22,1,.36,1)`, 500ms for layout and position, 300ms for colour, 600–800ms for scroll reveals of 32px, tagline words stepping 70ms each.
