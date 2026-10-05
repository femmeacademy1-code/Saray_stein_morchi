# CLAUDE.md – Sarai Stein Morhi website

Static one-page site (Hebrew, RTL). No build step: `index.html` + `assets/`. Deploy target: **GitHub Pages**.

## Task for Claude Code: publish to GitHub
1. Check tools: `git --version`, `gh --version`, `gh auth status`. If `gh` isn't logged in, run `gh auth login` and ask the user to finish in the browser.
2. From this folder:
   ```bash
   git init -b main
   git add .
   git commit -m "Initial site: Sarai Stein Morhi"
   gh repo create sarai-stein-morhi --public --source=. --remote=origin --push
   ```
   (Ask the user for a different repo name or private repo if they prefer. GitHub Pages on a free account needs a **public** repo.)
3. Enable Pages from `main` / root:
   ```bash
   gh api -X POST repos/{owner}/sarai-stein-morhi/pages -f "source[branch]=main" -f "source[path]=/"
   ```
   Then print the URL: `https://{owner}.github.io/sarai-stein-morhi/` (takes 1–2 min first time).
4. Custom domain (optional): rename `CNAME.example` → `CNAME` with the domain, commit and push, then at the domain registrar add a CNAME record `www` → `{owner}.github.io`. Enable "Enforce HTTPS" in repo Settings → Pages.

## Before / after publishing – pending items
- **Portrait photo**: add `assets/sarai-portrait.jpg` (portrait 4:5, ≥1000px wide). Until then the hero frame shows the beige block only.
- Compress images if large (clinic photos ~ aim < 300KB each).
- Legal text (terms / privacy) is a generic draft – recommend review.
- Israeli accessibility regulation: consider adding an accessibility statement (הצהרת נגישות).
- Analytics: none installed. If added, load only after cookie consent `localStorage['sarai-cookies'] === 'all'` (hook marked in the inline script).

## Editing rules
- Keep the 4-color palette only: `#F3EDE0` cream, `#D8CAAE` beige, `#8D9E73` sage, `#566B45` deep green (+ tint `#D3DAC3`).
- Fonts: Frank Ruhl Libre (headings), Assistant (body).
- Copy is final and approved – don't rewrite Hebrew text. Compound words use an unspaced hyphen (גופנית-התייחסותית); no spaced dashes.
- Illustrations are inline SVG line drawings – edit in place.
- Contact: tel `+972525832874`, WhatsApp `wa.me/972525832874`, `Saraysht@gmail.com`. No street address on the site (by request) – only "פרדס חנה-כרכור".
