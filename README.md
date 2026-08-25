# Portfolio — Dinakaran

Personal portfolio site for a Power Platform / Dynamics 365 developer. One file, no build step, no dependencies to install. Open `index.html` in a browser and it runs.

**Live:** https://YOUR-USERNAME.github.io

---

## What's in here

```
.
├── index.html      # the entire site — markup, styles, and scripts
└── README.md
```

That's deliberate. There's no bundler, no `node_modules`, and nothing to compile. Fonts load from Google Fonts over CDN; everything else is inline. Editing means opening one file.

---

## Run it locally

Double-click `index.html`, or serve it if you'd rather have a proper localhost:

```bash
python3 -m http.server 8000
# then open http://localhost:8000
```

---

## Deploy to GitHub Pages

**For a site at `username.github.io`** — name the repo exactly `YOUR-USERNAME.github.io`, push `index.html` to the default branch, and Pages turns on by itself.

**For a project site at `username.github.io/portfolio`:**

1. Push to any repo (e.g. `portfolio`).
2. Settings → Pages → Source: **Deploy from a branch**.
3. Branch: `main`, folder: `/ (root)`. Save.

First build takes a minute or two. After that, every push republishes.

### Custom domain

Add a file named `CNAME` at the repo root containing just your domain:

```
dinakaran.dev
```

Then point a CNAME DNS record at `YOUR-USERNAME.github.io`, and tick **Enforce HTTPS** in Settings → Pages once the certificate provisions.

---

## Replacing the previous site

This rewrite supersedes an earlier single-page portfolio titled *Data Analyst Portfolio*. What carried over and what didn't:

**Carried over** — the full technical stack. Python, R, Java, C, SQL, RDBMS, JSON/XML, Tableau, Excel and Agile now live in the toolbox strip under the capabilities grid, alongside the Power Platform tooling. Docker and CI/CD sit under *delivery*.

**Deliberately dropped** — the old positioning. The previous page led with "Data Analyst" and a generic summary. Four current Microsoft associate certs and two years of Power Platform delivery support a stronger claim than that, and a page can only make one first impression.

**Needs a decision** — five projects from the old page have no home yet:

| Old project | Status |
|---|---|
| Infrastructure Automation with Terraform | not on the new page |
| Cloud Resource Management System | not on the new page |
| CI/CD Pipeline (GitLab) | not on the new page |
| Interactive Data Visualization Dashboard (Tableau) | not on the new page |
| IT Support Dashboard | not on the new page |

The first three are infrastructure work, which pulls against a Power Platform developer's story. The last two are closer — an IT support dashboard is arguably the same problem space as case tracking. If any of these have real repos behind them, add the two dashboard projects and leave the infrastructure ones on the résumé.

**Two bugs fixed from the old file:** the contact link used `href="sdinakaran2509@gmail.com"` with no `mailto:` scheme, so it resolved as a relative path and went nowhere — and the visible link text still read `your.email@example.com`.

**One conflict outstanding:** the old page linked to `linkedin.com/in/dinakaran-somasundaram-data-analyst/`; the current profile is `linkedin.com/in/dinakaran-so/`. The new page uses the latter in three places. If the older vanity URL is the live one, search and replace.

---

## Before you publish — checklist

- [ ] **Replace `YOUR-USERNAME`** — 8 occurrences (6 project links, the GitHub button, the live URL in this README). Find and replace across the file.
- [ ] **Fix the project cards.** Six repos are stubbed out from real work described on the LinkedIn profile. Either create the repos or delete the card. A dead link costs more than a missing one.
- [ ] **Check the Microsoft Learn verify links** actually resolve — they're built from credential share IDs and should open a public credential page.
- [ ] **Decide on the phone number.** It's intentionally not on the page. Add it to the contact section if you want it public.
- [ ] **Add a preview image** (see below) so the link renders properly when shared.

---

## Editing guide

Sections are marked with comment banners in `index.html`. Search for these:

| Banner | What it holds |
|---|---|
| `HERO` | Name, headline, lede, tech tags, cert strip, the animated flow diagram |
| `METRICS` | Four headline numbers |
| `WORK / CAPABILITIES` | Six capability cards, plus the toolbox strip |
| `EXPERIENCE` | Timeline entries — newest first |
| `PROJECTS` | Repo cards |
| `CREDENTIALS` | Microsoft cert cards, secondary cert list, education, languages |
| `CONTACT` | Email, copy button, social links |

### Adding a project

Copy an existing `<a class="proj">` block and edit four things — the repo name, the title, the description, and the `stack` tags. The grid reflows on its own.

### Adding a certification

Primary Microsoft certs are `<a class="cert">` cards. Everything else is a `list-item` row — use the `<a class="list-item">` form when you have a verification link, the `<div class="list-item">` form when you don't.

### Recolouring

Every colour and typeface is a CSS variable at the top of the `<style>` block:

| Variable | Role |
|---|---|
| `--ink` / `--ink-2` / `--panel` | Background layers, darkest first |
| `--line` | Every border and divider |
| `--teal` | Primary accent — links, active states, wires |
| `--amber` | Secondary accent — metrics, cert badges, data packets |
| `--display` | Chakra Petch — headings |
| `--body` | IBM Plex Sans — prose |
| `--mono` | IBM Plex Mono — labels, codes, technical text |

Change `--teal` and `--amber` and the whole page shifts with them.

### The hero diagram

The SVG under `SIGNATURE` maps four inputs (Dataverse, Dynamics 365, Power Apps, Power Automate) through a solution layer to three outputs (Power BI, Fabric, Copilot Studio). Node positions and wire paths are hand-placed coordinates in a `540 × 420` viewBox — if you move a node, the wire `d` attribute needs moving too. The amber packets are generated in JS from whatever `.wire` paths exist, so adding a wire automatically adds a packet.

---

## Social preview

GitHub and LinkedIn both need an image to render a link card. Add a 1200×630 PNG to the repo and drop these into `<head>`:

```html
<meta property="og:title" content="Dinakaran — Power Platform Developer">
<meta property="og:description" content="Dynamics 365 CRM, Dataverse, model-driven apps and Fabric analytics.">
<meta property="og:image" content="https://YOUR-USERNAME.github.io/preview.png">
<meta property="og:url" content="https://YOUR-USERNAME.github.io">
<meta name="twitter:card" content="summary_large_image">
```

---

## Notes on the build

- Responsive down to roughly 360px; the metrics strip goes two-up and the hero stacks.
- Keyboard focus is visible on every interactive element.
- `prefers-reduced-motion` kills all animation, including the diagram packets.
- The packet loop pauses when the tab is hidden.
- Works in current Chrome, Firefox, Safari and Edge. Uses `backdrop-filter` for the sticky nav, which degrades to a solid background where unsupported.

---

## License

MIT for the code. The content — bio, experience, credentials — isn't.
