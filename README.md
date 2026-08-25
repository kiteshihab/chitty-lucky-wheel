# GHS Areekode Chitty — Lucky Draw Wheel (PWA)

## Files
- `index.html` — the whole app (wheel, winners list, edit participants, payment distribution). This is the file to replace on GitHub.
- `manifest.json` — PWA manifest (name, icons, colors) so it can be installed as an app.
- `service-worker.js` — caches the app shell so it opens even with a weak connection once installed.
- `icon-192.png`, `icon-512.png` — app icons used on the home screen.

All 5 files must sit in the **same folder** (e.g. the root of your GitHub repo).

## Publish on GitHub Pages
1. Open your GitHub repo → replace the existing `index.html` with this new one, and add `manifest.json`, `service-worker.js`, `icon-192.png`, `icon-512.png` alongside it (same folder as `index.html`).
2. Commit / push.
3. In the repo, go to **Settings → Pages**, make sure "Deploy from branch" points at the branch/folder containing `index.html` (usually `main` / `root`).
4. Your site is now live at `https://<your-username>.github.io/<repo-name>/`.

## Install on iPhone Home Screen (PWA)
1. Open the GitHub Pages link in **Safari** on the iPhone (must be Safari, not Chrome).
2. Tap the **Share** icon (square with an arrow) at the bottom of the screen.
3. Scroll down and tap **"Add to Home Screen."**
4. Tap **Add**. A "Chitty Draw" icon now appears on the home screen and opens full-screen, like a normal app.

## Install on laptop / Android (optional)
- **Chrome/Edge (desktop or Android):** open the link, then use the browser's "Install app" option (icon in the address bar, or the ⋮ menu → "Install app").
- Works as a normal webpage too — just open `index.html` in any browser, no install needed.

## How the app works
- **Spin the wheel** to pick a random participant. Every person sharing that person's **lucky number** is treated as having completed the chitty that round and is removed from the wheel together (per the chitty's group rule).
- **Next Month / Next Month Spin** lets you continue drawing from the people still remaining.
- **Winners List** (right panel, under "🏆 Winners List") keeps a running history of every completed lucky number and who was in that group.
- **Edit Participants** (password protected) lets you add, edit, or remove people, and change the password itself.
- **Payment Distribution** (matches real chit-fund practice):
  - Each winner's total payout = their own monthly chitty amount × 10
    (₹20,000 → ₹2,00,000 · ₹10,000 → ₹1,00,000 · ₹5,000 → ₹50,000). That payout is the winner's own contribution (×1) plus every other member's contribution for that round (×9).
  - Every Winners List round is calculated **on its own**: only the winner(s) of *that* round are excluded from *that* round's payer pool. Members who already won in an earlier round still count as payers in later rounds — exactly like a real chit, where you keep paying your monthly installment even after you've already received your payout.
  - Winners in the same round never pay each other. The other members' monthly amounts are assigned **whole** (not split into fractions) to whichever winner in that round they balance best against, so a round with equal-amount winners (e.g. 2 winners on ₹10,000/month, or 4 winners on ₹5,000/month) comes out to an equal ₹1,00,000 or ₹50,000 each.
- **Password protection**: the same admin password now guards Edit Participants, Payment Distribution, Next Month, Next Month Spin, Winner Remove (OK), Last Winner Reset (undo), and All Reset — not just editing participants. Change it any time from inside Edit Participants → "🔐 Change Password."
- **Backup / Restore**: since progress is saved in the browser's local storage (per device), use "💾 Backup" to download a JSON snapshot and "📂 Restore" to load it on another device/browser so everyone stays in sync.
