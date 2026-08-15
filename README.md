# POEBOY — Paused

A single-page "away" site with a live countdown, an arcade "game paused" theme, synthesized 8-bit sound effects, and a pixel-heart favicon. No build tools, no dependencies to install — it's one self-contained HTML file.

## What's inside

- **Live countdown** to February 1, 2027, styled as an in-game "Continue in..." timer
- **Contact menu** with four channels: direct call, WhatsApp, TikTok, and iMessage
- **8-bit sound effects** (hover blips, select chimes) generated live with the Web Audio API — no audio files needed
- **Pixel-heart favicon**, drawn as inline SVG — no image files needed
- Fully responsive, works down to mobile
- Respects `prefers-reduced-motion` (turns off animations for people who've asked their OS for that)

## Files

```
index.html   → the entire site (HTML, CSS, and JS all in one file)
README.md    → this file
```

## How to host it

Since it's one plain HTML file, any static host works. A few free options:

**GitHub Pages**
1. Create a new GitHub repo
2. Upload `index.html` to it
3. Go to Settings → Pages → set source to your main branch
4. Your site will be live at `https://<username>.github.io/<repo-name>`

**Netlify**
1. Go to [netlify.com/drop](https://app.netlify.com/drop)
2. Drag and drop `index.html` (or the folder containing it) into the browser
3. It's live instantly with a generated URL — you can rename it or connect a custom domain in settings

**Vercel**
1. Go to [vercel.com](https://vercel.com), create a new project
2. Upload the file or connect a repo containing it
3. Deploy — Vercel gives you a live URL automatically

Any of these let you attach your own domain name later if you buy one.

## Customizing it

Everything lives in `index.html` — open it in any text editor.

**Change the countdown date**
Find this line near the bottom of the file (inside the `<script>` tag):
```js
const target = new Date('2027-02-01T00:00:00');
```
Change the date to whatever you want, in `YYYY-MM-DDTHH:MM:SS` format.

**Change contact info**
In the `<div class="menu">` section, each contact option is one `<a class="menu-item">` block. Update the `href` and the visible text:
- Call: `href="tel:+233554668659"`
- WhatsApp: `href="https://wa.me/233503812812"`
- TikTok: `href="https://tiktok.com/@abvlafia"`
- iMessage: `href="sms:esb.abulafia@gmail.com"`

**Change colors**
All colors are defined once at the top of the file under `:root`, so changing a value there updates it everywhere:
```css
--bg: #170f2e;
--panel: #241546;
--pink: #ff3d81;
--yellow: #ffd23f;
--mint: #3ef8b0;
```

**Sound effects**
On by default for first-time visitors. There's a `SFX: ON/OFF` button in the top-right corner to mute it — the choice is remembered on that visitor's browser for next time. Because of browser autoplay rules, sound only starts after the visitor's first click or tap anywhere on the page — that's a browser restriction, not something adjustable in the code.

## Notes

- The iMessage link (`sms:` scheme) works well on iPhones/Safari but may not do anything on desktop or Android, since there's no Messages app there to catch it.
- Double-check your phone number and WhatsApp number include the correct country code before publishing.
