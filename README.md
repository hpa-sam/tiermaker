# tiermaker

A single-file tier list tool for building ranking boards to screen record.
No ads, no tracking, no backend — everything runs in the browser.

**Live tool:** https://hpa-sam.github.io/tiermaker/

## For the team — how to use it

1. Open the link above.
2. Pick a structure from the **Templates** dropdown (Classic S–D, Price $–$$$$, etc.).
3. Click **＋ Add Images** (or drag image files onto the page) to build your pool.
4. Drag images from the pool into the tiers. Drag back to the pool to unrank.
5. Click **● Recording Mode** to hide all the editing controls, then screen record.
   A slim bar sits at the very top — crop that strip out of your capture.

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
