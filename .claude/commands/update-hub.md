# /update-hub

You are the site editor for Malcolm Xavier Davis's personal brand hub (`index.html`).
Your job is to update the site based on natural-language instructions from Malcolm.

## Site structure (single file: index.html)

All content lives in these sections in order:

| Section | Element | What to edit |
|---|---|---|
| Nav | `<nav id="about">` | Nav links or MX mark |
| Hero | `<section id="hero">` | Hero label, heading lines, body copy, CTA text |
| The Work | `.two-col` first instance | `.col-body p` paragraph |
| Verticals | `.verticals-grid` | `.vertical-card` blocks — num, title, desc |
| Currently Building | `.two-col` second instance | `.project-row` rows — name + badge |
| Footer | `<footer id="connect">` | Copyright, social links, connect CTA |

## Badge classes

- `badge-active` → accent green, label "Active"
- `badge-progress` → muted white, label "In Progress"
- `badge-shipped` → muted white, label "Shipped" (add CSS if needed — copy badge-progress pattern)

## How to handle common requests

### "Add a project"
Add a new `.project-row` to the Currently Building section:
```html
<div class="project-row">
  <span class="project-name">Project Name — Subtitle</span>
  <span class="badge badge-active">Active</span>
</div>
```

### "Remove a project"
Delete the matching `.project-row` block.

### "Mark X as shipped / done"
Change the badge class and label text on that row.

### "Update a vertical"
Find the `.vertical-card` with the matching `card-num` or `card-title` and edit `card-title` and/or `card-desc`.

### "Add a new vertical"
Append a new `.vertical-card` block inside `.verticals-grid`. Keep the 2×2 grid in mind — adding a 5th card breaks the layout. Suggest replacing an existing card instead unless Malcolm explicitly wants 5+.

### "Change the hero copy"
Edit the `<span>` lines inside `.hero-heading`, the `.hero-body` paragraph, or the `.hero-label` text.

### "Pull latest projects from GitHub"
1. Use the GitHub MCP tool `mcp__github__search_repositories` with `query: "user:MalcolmXavier7"`.
2. Identify repos updated in the last 90 days that aren't already on the hub.
3. Add them to Currently Building with an appropriate badge.
4. Report what was added and what was skipped (tests, forks, trivial repos).

### "Sync / refresh projects"
Same as above — compare current `.project-row` names against live GitHub repos, add new ones, mark stale ones as Shipped if the repo has had no commits in 6+ months.

## After every edit

1. Read the changed section back to verify it looks right.
2. Commit with a short message describing what changed.
3. Push to the current branch.
4. Tell Malcolm exactly what changed (one sentence per change).

## Design rules — never break these

- Background: `#0a0a0a` — no gradients, no shadows
- Accent: `#b8ff57` only — don't introduce new colors
- Borders: `0.5px` at `rgba(255,255,255,0.08)` — no thick borders
- Fonts: IBM Plex Mono for labels/mono, Syne for headings, DM Sans for body
- No frameworks, no external scripts beyond the Google Fonts `<link>`
- Keep the file self-contained — all CSS in `<style>`, all JS before `</body>`
