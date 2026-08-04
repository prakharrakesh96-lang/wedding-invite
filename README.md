# Disha & Prakhar — Wedding Invitation

Single-page site. No build step, no dependencies to install.
Open `index.html` in a browser and it runs.

## Files

```
index.html          everything — markup, styles, scripts
assets/
  engagement.jpg    Chapter 01
  haldi.jpg         Chapter 02
  sangeet.jpg       Chapter 03
  wedding.jpg       Chapter 04
  vidai.jpg         Chapter 05
```

Keep `index.html` and `assets/` together. The image paths are relative,
so separating them breaks the chapter panels.

## Putting it online

Drag this whole folder onto **Netlify Drop** (app.netlify.com/drop) or
**Cloudflare Pages**. Both are free and give you a URL in seconds.
Vercel and GitHub Pages work the same way. Nothing here needs a server.

## Things you may want to change

**RSVP destination** — search `ENDPOINT` in `index.html`. Currently posts to
Formspree form `xqerjvjg`. Replace the URL to send replies elsewhere.
Note: the free Formspree tier caps at 50 submissions per month.

**Countdown target** — search `TARGET`. Set to 19 Jan 2027, 8:00 PM IST.

**Image crops** — each chapter panel carries a `--pos` value, e.g.
`--pos:72% center`. These portraits have the couple off to one side, so
the crop is tuned per image. Adjust the percentage if one looks off.

**Venues** — now three cards, each with a side badge on the map:

| Venue | Badge | Layout |
|---|---|---|
| Atithi Inn | Groom's Side | top-left, address filled in |
| Aaradhya | Bride's Side | top-right, **still needs map + address** |
| Viviana Greens Lawn | Both Families | full-width row below, address filled in |

Atithi Inn and Viviana Greens addresses were verified against Google Places.
The wedding venue spans the full row on purpose — two family venues above,
the shared one below.

**Finishing the Aaradhya card** — it currently shows a striped "Map to follow"
panel. Search `v-map-pending`. Replace that whole `<div>` with a copy of the
Atithi card's `<div class="v-map">` block, swapping in Aaradhya's map query,
then replace `Address to be confirmed` with the real address and add a
`Get directions` link like the other two cards have.

**Music** — `assets/music.mp3`, 28.6s, 128 kbps. A round toggle sits
bottom-right. Behaviour:

- Does *not* autoplay with sound; browsers refuse. It starts on the visitor's
  first tap, scroll, or keypress.
- Fades in to 35% volume rather than starting at full blast. Tune `VOL` at the
  top of the script.
- The track is short and ends mid-phrase, so it does **not** use the native
  `loop` attribute — a hard loop clicked audibly every 29 seconds. Two audio
  elements leapfrog each other with a 2.2s crossfade instead, set by `XF`.
- Pauses when the visitor leaves the tab, resumes where it left off.
- If the file is missing or unplayable the button removes itself and the page
  behaves as though the feature were never there.
- Swapping the track: replace `assets/music.mp3`. Nothing else needs editing —
  the crossfade reads the duration at runtime.
- To remove entirely: delete the `<audio>` element, the `.bgm-btn` button, and
  the final `<script>` block.

**Weekdays** — the event weekdays currently read Saturday 18th and
Sunday 19th. In January 2027 the 18th is a Monday and the 19th a Tuesday;
those labels match January 2025. Worth correcting before you send the link.

**Ganesha artwork** — the watermark behind the bride and groom names is a
lotus mandala drawn in SVG, standing in for the Ganesha illustration on the
original. Search `class="wm"` to swap in your own file.

**Removing the RSVP** — delete the `<section class="rsvp">` block and the
RSVP script block at the bottom. Nothing else depends on them.
