[README.md](https://github.com/user-attachments/files/30527530/README.md)
# Tier Maker (in-house)

A single-file tool for building ranking/decision boards to screen record.
No ads, no tracking, no backend — everything runs in the browser.

Five game modes, switchable via the tab bar at the top, all sharing the same
image pool, preview panel, recording mode and save/load:
**Tier List · Budget · Bracket · Draft · This / That**. Every mode keeps the same
footprint (left context column, middle play area, right preview, pool along the
bottom) so editing and screen-recording feel identical across all of them.

**Live tool:** (https://hpa-sam.github.io/tiermaker/)

---

## For the team — how to use it

1. Open the link above.
2. Pick a structure from the **Templates** dropdown (Classic S–D, Price $–$$$$, etc.).
3. Click **＋ Add Images** (or drag image files onto the page) to build your pool.
4. Drag images from the pool into the tiers. Drag back to the pool to unrank.
5. Click **● Recording Mode** to hide all the editing controls, then screen record.
   A slim bar sits at the very top — crop that strip out of your capture.

### Budget mode
Switch **Tier List / Budget** in the toolbar to turn the tool into a "spend the
budget" board — good for "what would you buy with $X" videos.

1. Set the **Budget $** amount in the toolbar.
2. Add your images and click each thumbnail's **price badge** (top-left) to type a price.
3. The page title becomes the heading over the purchase area (e.g. "Home Workshop
   Essentials"), so name your list before recording.
4. Drag an image into the **purchase area** to buy it — its price leaves the budget.
   Drag it back to the pool to refund.
5. Budget mode uses three columns: **left** = the **receipt** (its header is your list
   title; it itemises each purchase, then shows Budget and a large Remaining total that
   turns red on overspend); **middle** = the purchase area; **right** = the preview.
   The image pool runs along the bottom, same as tier mode.
6. **🖼 Export PNG** in budget mode saves a clean receipt image (title, items with
   thumbnails, spent, remaining) instead of a tier board.

Two things worth knowing:
- Each image lives in exactly one place — the pool, a tier, or the purchase area.
  If you placed images in tiers, then switch to budget mode, those images stay in the
  (now hidden) tiers and won't be in the pool to buy. Drag them back to the pool first,
  or start a budget project with a fresh set of images.
- Prices and budget are saved inside the project `.json`, so **💾 Save** and
  `?project=` links carry them.

### Bracket mode
Single-elimination tournament played as a series of "this or that" picks.

1. Add **2, 4, 8, 16 or 32** images to the pool (a clean bracket needs a power of two —
   if you're off, it tells you exactly how many to add or remove). Click
   **Generate from pool**.
2. The **chart** sits on the left as a live scoreboard; the **current matchup** shows as
   two big cards on the right. Click **Pick this** on the winner — they advance on the
   chart (highlighted green) and the next matchup loads automatically. No dragging.
3. When the final is decided, a **fireworks celebration** pops up with the champion.
   **↺ Restart** clears the winners and replays the same field; **Generate** reseeds
   from the pool.

### Draft mode
Positional build — one pick per category, "build the ultimate sleeper."

1. The middle column is a **grid of slot cards** (Engine, Forced Induction, Suspension…).
   Rename them inline, reorder with ▲▼, add/remove slots.
2. Each slot has its **own pool tab** along the top of the pool (the tab mirrors the
   card's name). Click a card *or* its tab to make that pool active; images you add
   land in the active tab. Drag an image onto a tab to re-file it. This keeps an
   "engine pool", "wheels pool" etc. separate.
3. Drag one image into each slot card. Dropping a second replaces the first (it
   returns to that pool).
4. Optional **Budget cap**: tick it in the toolbar for price badges and a live
   Remaining total in the left column.

In recording mode the pool shows only the active tab's images, so the screen isn't
overwhelmed with every option at once.

### This / That mode
King-of-the-hill picks — quick "OEM+ vs stanced" style rounds.

1. Two cards appear, champion vs challenger. Click either image to **preview** it.
2. Click **Pick this** on the winner — it stays as champion, the loser joins the
   **Defeated** list on the left, and the next pool image loads as the challenger.
3. When the pool runs out, the last champion is crowned with a **fireworks
   celebration**. **↺ Restart** starts over.

> Bracket, Draft and This/That are built for screen recording, so **🖼 Export PNG**
> only produces a still image in Tier and Budget modes.

### Preview panel (for presenting)
Click any image to load it large in the **Preview** panel on the right — useful for
talking about an item before you rank it. The clicked image gets a blue highlight so
viewers can see which one you mean. Dragging works exactly as before; clicking and
dragging are independent.

Works on pool images and ones already placed in tiers. **✕** clears the preview, and
**👁 Preview** in the toolbar hides the panel for a full-width board.

### Exporting a still image
**🖼 Export PNG** downloads the finished board as a single image at 2× resolution —
handy for thumbnails, docs, or a title card. It captures just the tier rows
(no toolbar or controls), matching exactly what's on screen.

### Saving your work
Images live in memory, so **a browser refresh clears the board.** Hit **💾 Save** to
download a `.json` project file containing your layout *and* the images.
**📂 Load** restores it.

### Templates vs projects
- **Template** = row names + colours only. Lightweight, switch anytime from the dropdown.
  Save your own with **☆ Save as Template** (stored in your own browser).
- **Project** = a full board including images. That's what 💾 Save exports.

---

## Saving setups to GitHub (Save to GitHub + Setups menu)

You can publish a fully-configured setup — mode, images, prices, draft pool tabs —
straight to the repo, then anyone opens it from a link with no login.

**One-time: create a token (only the person who saves needs this).**
1. GitHub → Settings → Developer settings → **Fine-grained personal access tokens** →
   Generate new token.
2. Resource owner: `hpa-sam`. Repository access: **Only select repositories → tiermaker**.
3. Permissions → Repository permissions → **Contents: Read and write**. Generate.
4. In the tool, click **☁ Save to GitHub** and paste the token when asked. It's stored
   only in your browser (localStorage) — never committed or uploaded.

**Saving:** click **☁ Save to GitHub**, name the setup. It writes
`projects/<name>.json`, updates `projects/index.json`, and copies the share link to
your clipboard. (GitHub Pages takes ~1 minute to publish the new file.)

**Opening:** anyone can click **🗂 Setups** to see all saved setups and hit **Open**,
**Open + Record**, or **Copy link** — no token or account needed. The links are just
`?project=<name>` URLs, so you can paste them anywhere.

Security notes: use a *fine-grained* token scoped to only this repo with Contents
write; keep it on your own machine; a public Pages site means saved setups (and their
images) are world-readable. For confidential imagery, don't publish — share the saved
`.json` privately and use 📂 Load instead.

## Sharing a finished board via link

A colleague can open a saved project directly, no Load button needed.

1. Build the board, click **💾 Save** to get the `.json`.
2. Commit that file into the `projects/` folder of this repo.
3. Share the link:

   ```
   https://<org-or-user>.github.io/<repo>/?project=<filename-without-.json>
   ```

   Example: `projects/spend-save-2026.json` → `...github.io/tiermaker/?project=spend-save-2026`

Optional extras:
- `&record=1` opens it straight into recording mode.
- `?project=https://.../any.json` loads any hosted JSON URL (e.g. a Gist raw link).

> Link loading uses `fetch`, which needs the page served over http(s).
> It works on GitHub Pages but **not** when opening `index.html` off your local disk.
> Local double-click still works fine for building boards.

---

## Repo layout

```
index.html            the entire tool (single self-contained file)
preview.png           social card image used by Slack/Teams link previews
projects/             saved .json projects, shareable via ?project=
README.md             this file
```

## One-time step after enabling Pages

Open `index.html` and find the `og:image` / `og:url` meta tags near the top.
Replace the relative values with your absolute Pages URL:

```html
<meta property="og:image" content="https://<user>.github.io/<repo>/preview.png">
<meta property="og:url"   content="https://<user>.github.io/<repo>/">
```

Slack and Teams are inconsistent about resolving relative image paths, so absolute
URLs are what make the preview card reliably show the image. Everything else works
without this step.

Note: link previews are generated from the static HTML, so **every** `?project=` link
shows the same generic card — the card can't reflect an individual board's contents.

## Updating the tool

Replace `index.html` and push. Everyone gets the new version on their next load —
no reinstall, nothing for the team to do.

## ⚠️ A note on visibility

GitHub Pages sites are **publicly reachable on the internet even when the repo is
private.** Anyone with the URL can open the tool and any project JSON in `projects/`.
Making the *site itself* private requires GitHub Enterprise Cloud.

The tool code is harmless to expose, but **don't commit project files containing
unreleased or confidential imagery** unless you're on Enterprise Cloud with private
Pages enabled. For sensitive boards, share the `.json` file directly (Slack, Drive)
and have the person use **📂 Load** instead.
