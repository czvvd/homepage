# Homepage Beautification Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Transform the academic homepage from a blue-teal color scheme to a purple-mint palette with colored left-border section identifiers, refined card/button styles, and minimal animation.

**Architecture:** Pure CSS variable swap + targeted rule updates in `stylesheet.css`, plus three small HTML fixes in `index.html` (favicon path, hero link classes, footer). No structural HTML changes to tables or publication entries.

**Tech Stack:** Plain HTML + CSS (no build tools, no JS changes)

**Spec:** `docs/superpowers/specs/2026-04-01-homepage-beautify-design.md`

---

### Task 1: Update CSS custom properties and background gradients

**Files:**
- Modify: `stylesheet.css:66-77` (`:root` variables)
- Modify: `stylesheet.css:95-102` (`body.homepage` background)

- [ ] **Step 1: Replace all CSS custom properties in `:root`**

In `stylesheet.css`, replace the `:root` block (lines 66-77) with:

```css
:root {
  --bg: #f0f0f5;
  --bg-soft: #f8f7fc;
  --text: #1e1e2e;
  --muted: #5e5e72;
  --line: #dddde5;
  --accent: #6c5ce7;
  --accent-strong: #5a4bd6;
  --accent-secondary: #00b894;
  --card: #ffffff;
  --radius: 16px;
  --shadow: 0 14px 30px rgba(60, 40, 100, 0.08);
}
```

- [ ] **Step 2: Replace body background gradients**

In `stylesheet.css`, replace the `body.homepage` rule (lines 95-102) with:

```css
body.homepage {
  margin: 0;
  background:
    radial-gradient(circle at 12% -8%, #e4dff8 0, transparent 44%),
    radial-gradient(circle at 88% 0%, #d4f5ee 0, transparent 40%),
    var(--bg);
  line-height: 1.65;
}
```

- [ ] **Step 3: Update link transition speed**

In `stylesheet.css`, change the `a` rule (line 117) transition from `0.22s` to `0.15s`:

```css
a {
  color: var(--accent);
  text-decoration: none;
  transition: color 0.15s ease;
}
```

- [ ] **Step 4: Update h2 underline gradient**

In `stylesheet.css`, replace the `h2::after` background (line 139) with:

```css
h2::after {
  content: "";
  display: block;
  width: 56px;
  height: 3px;
  border-radius: 999px;
  margin-top: 8px;
  background: linear-gradient(90deg, #6c5ce7 0%, #00b894 100%);
}
```

- [ ] **Step 5: Verify in browser**

Open `index.html` in browser. Check: page background is light purple-gray, radial gradients are purple (top-left) and mint (top-right), link color is purple, h2 underlines are purple-to-mint gradient.

- [ ] **Step 6: Commit**

```bash
git add stylesheet.css
git commit -m "style: update color palette to purple-mint and adjust background gradients"
```

---

### Task 2: Update hero section styles

**Files:**
- Modify: `stylesheet.css:142-189` (hero-related rules)

- [ ] **Step 1: Update `.hero-section` background and add left border**

Replace the `.hero-section` rule (lines 142-148) with:

```css
.hero-section {
  background: linear-gradient(145deg, #ffffff 0%, #f9f8ff 100%);
  border: 1px solid var(--line);
  border-left: 3px solid var(--accent);
  border-radius: 22px;
  box-shadow: var(--shadow);
  margin-bottom: 18px;
}
```

- [ ] **Step 2: Update `.hero-links a` pill button colors**

Replace the `.hero-links a` rule (lines 172-179) with:

```css
.hero-links a {
  display: inline-block;
  margin: 4px 4px;
  padding: 4px 10px;
  border-radius: 999px;
  border: 1px solid #d5d0f0;
  background: #f5f3ff;
}
```

- [ ] **Step 3: Add Email primary CTA style**

Add a new rule after `.hero-links a` for the first link (Email) to be solid purple. Add this CSS:

```css
.hero-links a.hero-link-primary {
  background: var(--accent);
  color: #fff;
  border-color: var(--accent);
}

.hero-links a.hero-link-primary:hover {
  background: var(--accent-strong);
  border-color: var(--accent-strong);
  color: #fff;
}
```

- [ ] **Step 4: Update `.hero-photo-cell img` shadow color**

Replace the `.hero-photo-cell img` rule (lines 185-189) with:

```css
.hero-photo-cell img {
  border-radius: 18px !important;
  border: 1px solid var(--line);
  box-shadow: 0 10px 24px rgba(60, 40, 100, 0.14);
}
```

- [ ] **Step 5: Verify in browser**

Check: hero card has purple left border, background is white-to-light-purple gradient, contact pills are purple-tinted, photo shadow is purple-tinted.

- [ ] **Step 6: Commit**

```bash
git add stylesheet.css
git commit -m "style: update hero section with purple accent border and refined pills"
```

---

### Task 3: Update section cards with left-border identifiers

**Files:**
- Modify: `stylesheet.css:191-210` (section-card rules)

- [ ] **Step 1: Add News-specific left border class**

Add CSS rules for section-card variants. After the existing `.section-card li` rule (line 210), add:

```css
.section-card-news {
  border-left: 3px solid var(--accent-secondary);
}

.section-card-services {
  border-left: 3px solid var(--accent-secondary);
}

.section-card-pubs {
  border-left: 3px solid var(--accent);
}
```

- [ ] **Step 2: Verify the new classes exist in CSS**

Confirm the rules are present after `.section-card li`.

- [ ] **Step 3: Commit**

```bash
git add stylesheet.css
git commit -m "style: add left-border color identifiers for section cards"
```

---

### Task 4: Update publication toggle buttons and card hover styles

**Files:**
- Modify: `stylesheet.css:219-270` (pub-btn and publication-list rules)

- [ ] **Step 1: Update `.pub-btn` inactive state**

Replace the `.pub-btn` rule (lines 219-228) with:

```css
.pub-btn {
  font-size: 15px;
  padding: 9px 15px;
  border: 1px solid #d5d0f0;
  background: #f5f3ff;
  color: #5e5e72;
  border-radius: 10px;
  cursor: pointer;
  transition: all 0.15s ease;
}
```

- [ ] **Step 2: Update `.pub-btn:hover`**

Replace the `.pub-btn:hover` rule (lines 230-233) with:

```css
.pub-btn:hover {
  background: #ece8ff;
  border-color: #b8b0e0;
}
```

- [ ] **Step 3: Update `.pub-btn.active`**

Replace the `.pub-btn.active` rule (lines 235-240) with:

```css
.pub-btn.active {
  background: linear-gradient(90deg, #6c5ce7, #5a4bd6);
  color: #fff;
  border-color: transparent;
  box-shadow: 0 8px 18px rgba(108, 92, 231, 0.28);
}
```

- [ ] **Step 4: Remove transition from publication card transform**

Replace the `.publication-list tr td` rule (lines 250-255). Remove the transform transition, keep only box-shadow:

```css
.publication-list tr td {
  background: var(--card);
  border-top: 1px solid var(--line);
  border-bottom: 1px solid var(--line);
}
```

- [ ] **Step 5: Update publication card hover shadow color**

Replace the `.publication-list tr:hover td` rule (lines 267-270) with:

```css
.publication-list tr:hover td {
  transform: translateY(-1px);
  box-shadow: 0 8px 18px rgba(60, 40, 100, 0.1);
}
```

- [ ] **Step 6: Update teaser image border color**

Replace the `.publication-list td:first-child img` rule (lines 272-276) with:

```css
.publication-list td:first-child img {
  width: 100%;
  border-radius: 10px;
  border: 1px solid #dddde5;
}
```

- [ ] **Step 7: Update `.papertitle` color**

Replace the `.papertitle` rule (lines 278-282) with:

```css
.papertitle {
  font-size: 17px;
  font-weight: 700;
  line-height: 1.4;
  color: var(--accent);
}
```

- [ ] **Step 8: Add publication link pill styles**

Add a new rule after `.papertitle` for publication action links:

```css
.publication-list td:last-child a {
  display: inline-block;
  padding: 3px 10px;
  border: 1px solid #d5d0f0;
  border-radius: 999px;
  background: #f5f3ff;
  color: var(--accent);
  font-size: 14px;
  margin: 2px 2px;
}

.publication-list td:last-child a:hover {
  background: #ece8ff;
  border-color: #b8b0e0;
  color: var(--accent-strong);
}
```

- [ ] **Step 9: Verify in browser**

Check: toggle buttons are purple when active, paper titles are purple, links are pill-shaped, card hover has purple-tinted shadow, teaser image borders match the palette.

- [ ] **Step 10: Commit**

```bash
git add stylesheet.css
git commit -m "style: update publication cards, toggle buttons, and link pills to purple theme"
```

---

### Task 5: Update footer styles and responsive media query colors

**Files:**
- Modify: `stylesheet.css:284-331` (footer + media query)

- [ ] **Step 1: Update `.site-footer p` color**

Replace the `.site-footer p` rule (lines 288-290) with:

```css
.site-footer p {
  color: var(--muted);
}
```

- [ ] **Step 2: Verify media query needs no color changes**

Review the `@media (max-width: 860px)` block (lines 292-331). It only adjusts layout (display: block, padding, border-radius) — no hardcoded colors to update. No changes needed.

- [ ] **Step 3: Commit**

```bash
git add stylesheet.css
git commit -m "style: update footer text color to use muted variable"
```

---

### Task 6: HTML changes — favicon fix, section card classes, Email CTA, footer

**Files:**
- Modify: `index.html:10` (favicon link)
- Modify: `index.html:31-36` (hero links — add class to Email)
- Modify: `index.html:47` (News section — add class)
- Modify: `index.html:63` (Publications section — add class)
- Modify: `index.html:580` (Services section — add class)
- Modify: `index.html:591-597` (add footer before closing tags)

- [ ] **Step 1: Fix favicon href**

In `index.html` line 10, replace:

```html
<link rel="icon" href="favicon-missing.ico?v=2">
```

with:

```html
<link rel="icon" href="images/favicon/favicon.ico?v=2">
```

- [ ] **Step 2: Add `hero-link-primary` class to Email link**

In `index.html` line 32, replace:

```html
<a href="mailto:zhuzhe0619@nuaa.edu.cn">Email</a> &nbsp;/&nbsp;
```

with:

```html
<a class="hero-link-primary" href="mailto:zhuzhe0619@nuaa.edu.cn">Email</a> &nbsp;/&nbsp;
```

- [ ] **Step 3: Add `section-card-news` class to News table**

In `index.html` line 47, replace:

```html
<table class="section-card" style="width:100%;border:0px;border-spacing:0px;border-collapse:separate;margin-right:auto;margin-left:auto;">
```

with:

```html
<table class="section-card section-card-news" style="width:100%;border:0px;border-spacing:0px;border-collapse:separate;margin-right:auto;margin-left:auto;">
```

- [ ] **Step 4: Add `section-card-pubs` class to Publications table**

In `index.html` line 63, replace:

```html
<table class="section-card" style="width:100%;border:0px;border-spacing:0px;border-collapse:separate;margin-right:auto;margin-left:auto;">
```

with:

```html
<table class="section-card section-card-pubs" style="width:100%;border:0px;border-spacing:0px;border-collapse:separate;margin-right:auto;margin-left:auto;">
```

Note: There are three `section-card` tables in the HTML (News at ~line 47, Publications at ~line 63, Services at ~line 580). Be careful to modify the correct one for each step.

- [ ] **Step 5: Add `section-card-services` class to Services table**

In `index.html` line 580, replace:

```html
<table class="section-card" style="width:100%;border:0px;border-spacing:0px;border-collapse:separate;margin-right:auto;margin-left:auto;">
```

with:

```html
<table class="section-card section-card-services" style="width:100%;border:0px;border-spacing:0px;border-collapse:separate;margin-right:auto;margin-left:auto;">
```

- [ ] **Step 6: Add footer before closing `</div>` of page-shell**

In `index.html`, after line 596 (`</table>`) and before line 597 (`</div>`), insert:

```html
    <footer class="site-footer" style="text-align:center;padding:16px 0 0;">
      <p>&copy; 2026 Zhe Zhu</p>
    </footer>
```

So the end of the file looks like:

```html
    </table>
    <footer class="site-footer" style="text-align:center;padding:16px 0 0;">
      <p>&copy; 2026 Zhe Zhu</p>
    </footer>
    </div>
    <script>
```

- [ ] **Step 7: Verify in browser**

Full visual check:
1. Favicon loads (check browser tab icon)
2. Email link is solid purple pill, other links are light purple pills
3. News section has mint-green left border
4. Publications section has purple left border
5. Services section has mint-green left border
6. Footer shows "© 2026 Zhe Zhu" centered at bottom
7. Toggle between Selected/All publications works
8. Resize to mobile width (< 860px) — layout stacks correctly, colors are consistent

- [ ] **Step 8: Commit**

```bash
git add index.html
git commit -m "fix: update favicon path, add section border classes, Email CTA, and footer"
```
