# Academic website — setup notes

Plain HTML/CSS, no build step, no framework. Five pages: `index.html`,
`research.html`, `teaching.html`, `cv.html`, `contact.html`, sharing
`assets/css/style.css`.

Repo: `HZ19/acadsite`, local dir `~/dev/acadsite`.

## 1. Push it

```bash
cd ~/dev/acadsite
git init
git add .
git commit -m "Initial site with real CV content"
git branch -M main
git remote add origin https://github.com/HZ19/acadsite.git
git push -u origin main
```

If this Mac isn't already authenticated as HZ19 for git over HTTPS, it'll
prompt for a GitHub login/token on push — use the HZ19 account's credentials.

## 2. Enable Pages

Repo → Settings → Pages → Source: **Deploy from a branch** → Branch: `main`,
folder `/ (root)`. Save. As a project repo (not `hz19.github.io`), the site
goes live at `https://hz19.github.io/acadsite/` — every link in the site is
relative, so this works fine at that subpath with no changes needed. If you'd
rather have the bare `https://hz19.github.io` URL later, that requires a repo
literally named `hz19.github.io`; the content ports over unchanged either way.

## 3. What's already real vs. still a placeholder

Your CV (`Zhai_CV.pdf`) is in and wired up — the Research, CV, and Home pages
are now populated from it directly: real publications, working papers,
presentations, teaching history, and education/employment timeline.

Search for remaining placeholders:

```bash
grep -rn "TODO" *.html
```

What's left:
1. **Teaching philosophy** (`teaching.html`) — needs your actual statement;
   not fabricated on your behalf.
2. **Prepared-to-teach course list** (`teaching.html`) — drawn from your
   coursework/TA record as a proxy; match exact NYUAD catalog names.
3. **Contact page** — Scholar and LinkedIn links; decide if you want a phone
   number public (left off by default).
4. **Second CV** (policy/KAPSARC version) — drop at
   `assets/cv/Zhai_CV_policy.pdf` and uncomment the second download button
   in `cv.html`.
5. **Homepage "current focus" line** — currently set to the NYUAD/econ
   framing; an alternate UNH Riyadh/policy-data version is drafted as an
   HTML comment right above it in `index.html` — swap which one is
   uncommented per application.

## Design notes

- Fonts: IBM Plex Serif (headings) + IBM Plex Sans (body), loaded from
  Google Fonts via `style.css`. No local font files to manage.
- No JavaScript anywhere — nothing to break, nothing to maintain.
- One accent color (`--accent` in `style.css`, a muted slate-teal) — change
  it in one place if you ever want a different accent.
- Responsive down to phone width; print stylesheet hides nav/footer if
  someone prints the CV page.
