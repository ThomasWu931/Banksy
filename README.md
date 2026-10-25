# Banksy

A focus timer that pays you. Start a session, stay on the page until the timer hits zero, and get paid in-game money: **1 minute of completed focus = 1¢**. Spend it in the Wallet tab.

## Features
- Pick a session length (5–120 min); a coin stack grows as the timer runs
- **Strict mode**: leave the tab for more than 10 seconds and the session is forfeited (no pay)
- Quit early → forfeited, nothing paid
- Wallet: balance, stats, and a scroll-wheel picker to redeem any amount up to your balance, plus redemption history
- One shared wallet, no login: the same balance on every device and browser (Firebase Firestore, doc `wallet/global`)
- Anyone with the link can earn or spend from that wallet

## Deploy to GitHub Pages
Settings → Pages → Deploy from a branch → `main` / `(root)`. Live at `https://thomaswu931.github.io/Banksy/`.

## Cloud sync (Firebase)
Connected to the `banksy-1ea2f` Firebase project via `firebase-config.js`. All money lives in one Firestore document, `wallet/global`. The rules in `firestore.rules` allow anyone to read and update only that document, and block a negative balance.

## Testing quickly
Add `?debug` to the URL to make each "minute" last one second. Money earned in debug mode counts toward your real balance.

## Tweaking
- Grace period for leaving the tab: `GRACE_MS` in `index.html`.
- Pay rate: earnings are added in `complete()` (`recordSession(..., s.minutes)`, in cents).
- After editing `firebase-config.js`, bump the `?v=` number on its `<script>` tag so browsers load the new version.
