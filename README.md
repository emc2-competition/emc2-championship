# Competition webpage

The public page for the **Speculative Decoding Championship** (emc2 workshop). It's one
static page with no build step, JavaScript or external resources:

| File | What it is |
|---|---|
| `index.html` | The whole page: overview, the two phases (report, then paper), prizes for the phase 1 winners, how it works, scoring, rules, dates, links, FAQ, contact |
| `style.css` | Light theme: cream background, violet accent, soft colour bands per section (mint, lilac, peach, rose), and a different layout per section (config-file facts, numbered phases, a prizes card with an offset shadow, stepper, data table with weight bars, checklists, tag chips, timeline, link list, accordion); JetBrains Mono for headings, navigation, labels and code, the system sans-serif font for body text |
| `fonts/` | JetBrains Mono (regular and bold, woff2), bundled so the page loads nothing from other sites. Free under the SIL Open Font License (`JetBrainsMono-OFL.txt`, keep it with the fonts). |
| `img/hero.svg` | Title banner: a draft model's guesses being checked by the target |
| `img/drafter-verifier.svg` | Animated drafter → verifier loop: a small neural network (drafter) fires once per guessed token, and a large one (verifier) checks all guesses in one wave (CSS animation inside the SVG, no JavaScript; shows a still final frame for visitors who turn off animations) |
| `img/how-it-works.svg` | One speculative decoding step, and what acceptance length means |
| `img/scoring.svg` | The 50 / 25 / 25 score weights |

The images are original SVGs drawn for this page, so they have no licensing restrictions. Edit
them as text. Their text asks for JetBrains Mono and falls back to the viewer's monospace font,
because an SVG shown with `<img>` can't use the page's bundled fonts.

## Preview

Open `index.html` in a browser. To serve it over HTTP instead:

```bash
python3 -m http.server 8000     # then open http://localhost:8000
```

## Placeholders to fill in before launch

Every placeholder is a gray **TBD** pill (`<span class="tbd">`), and every link that doesn't
exist yet is `<a class="placeholder" href="#">`. To find them all:

```bash
grep -n 'tbd\|placeholder' index.html
```

| Where | What's missing |
|---|---|
| Overview → Evaluation hardware | The evaluation GPU |
| Two phases, Rules | Report format, page limit and review criteria (phase 1); paper format and page limit (phase 2) |
| Prizes | The prizes for the 3 phase 1 winners (shown as "to be announced") |
| Scoring | Acceptance-gate and cap values (calibrated in the dry run) |
| Rules | Link to the full rules document; K, the number of guesses per step |
| Important dates | Five dates (kit release, report deadline, phase 1 winners, paper and draft model deadline, phase 2 results), and the time zone confirmation (AoE). The workshop entry (February 2027) is real; set its exact day once known |
| Important links | Report template, report submission, paper submission, draft model submission form, kit repository, rules document |
| Organizers & contact | Organizer names; contact email |
| Footer | "Last updated" date |

When a placeholder is filled, remove its `tbd` pill and, for a link, the `placeholder` class.

## Hosting

The page is served by GitHub Pages straight from the root of this repository's `main` branch.
The empty `.nojekyll` file tells Pages to publish the files as they are, with no Jekyll build.
