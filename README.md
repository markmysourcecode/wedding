# Sofia & Rafael — Wedding Invitation Site

Static, single-page wedding invitation + personalized RSVP page.

## What's in this build

- `index.html` — the full site. Pure HTML/CSS/JS, no build step, no dependencies.
- `assets/illustrations/` — stub placeholder SVGs, one per illustration slot the site expects. Each is a simple labeled box; swap the file in place with the real artwork (same filename) and it will appear automatically — no HTML/CSS changes needed.

This is the **frontend only**. Token verification, RSVP submission, and the messenger thank-you flow are currently mocked in `index.html`'s `<script>` block (see `MOCK_GUESTS`) so the whole flow is demo-able without a backend. Wiring up the real Google Apps Script + Sheets backend is the next phase — see "Not yet built" below.

## Try it locally

Open `index.html` directly in a browser, or serve the folder (`python3 -m http.server`) and visit:

- `index.html` — public/preview mode
- `index.html?invite=X4K9-Maria` or `?invite=A7P2-Diego` — a working mock RSVP
- `index.html?invite=NOT-Real` — the invalid-token screen
- `index.html?admin=1` — the token generator tool

## Deploying to GitHub Pages

1. Push this whole folder to a repo (keep `index.html` at the root).
2. In the repo settings, enable GitHub Pages for the root of the default branch.
3. Your site is live at `https://<username>.github.io/<repo>/`, or attach a custom domain via the repo's Pages settings.

## Replacing placeholders

Search `index.html` for:
- **Event details** (names, date, RSVP-by date, venue, address, ceremony time): edit the single `CONFIG` object at the top of the `<script>` block — every place they appear updates automatically.
- **Long-form copy**: Our Story paragraphs, FAQ answers, attire paragraphs, cat names/one-liners are edited directly in the page.
- **Illustrations**: every file in `assets/illustrations/` — replace each stub with the finished line-art SVG, same filename.

## Not yet built (next phase)

- Google Apps Script Web App (`doGet` token verification, `doPost` RSVP write)
- Google Sheets `Guests` and `RSVPs` tabs
- Shared-secret request signing + IP rate limiting
- Make (Integromat) scenario for the Viber/WhatsApp thank-you message
- Wiring the admin tool's CSV export into the live Guests sheet

Once the Apps Script endpoint exists, the two spots to update in `index.html` are marked with comments: `// Real build: POST to Apps Script...` and the `MOCK_GUESTS` verification block.
