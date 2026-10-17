# Sprout Focus

A Forest-style focus timer that runs entirely in the browser. Plant a tree, stay on the page while it grows, and earn in-game money: **1 minute of completed focus = 1¢**. Spend it in the Wallet tab on simple rewards.

## Features
- Pick a tree (Oak, Pine, Blossom, Maple) and a duration (5–120 min)
- Tree grows through stages as the timer runs
- **Strict mode**: leave the tab for more than 10 seconds and the tree withers (no money)
- Give up early → tree withers, nothing earned
- Forest tab shows every tree you've grown or lost, plus stats
- Wallet tab: balance, preset rewards, custom redeem amount, redemption history
- Sign in with Google to sync your money, forest and history across every device and browser (Firebase)
- Works signed out too: progress is saved on that device and moved into your account the first time you sign in

## Deploy to GitHub Pages
1. Create a new repository on GitHub (e.g. `sprout-focus`).
2. Upload `index.html` (and this README) to the root of the `main` branch.
3. Go to **Settings → Pages**, set **Source** to "Deploy from a branch", choose `main` and `/ (root)`, then **Save**.
4. After a minute your site is live at `https://<your-username>.github.io/sprout-focus/`.

## Cloud sync setup (Firebase, free tier)
1. Go to https://console.firebase.google.com, click **Add project**, name it, and finish (Analytics can be off).
2. **Build → Authentication → Get started → Sign-in method → Google → Enable → Save.**
3. **Authentication → Settings → Authorized domains → Add domain:** `thomaswu931.github.io`
4. **Build → Firestore Database → Create database** (production mode, any location).
5. **Firestore → Rules:** paste the contents of `firestore.rules` and **Publish**.
6. **Project settings (gear) → General → Your apps → Web (`</>`)**, register an app, and copy the `firebaseConfig` object into `firebase-config.js` as `window.FIREBASE_CONFIG = { ... };`

The config values are not secret; the Firestore rules make sure each account can only read and write its own data.

## Testing quickly
Add `?debug` to the URL to make each "minute" last one second, e.g. `.../sprout-focus/?debug`.

## Tweaking
- Rewards list: edit the `REWARDS` array in `index.html`.
- Grace period for leaving the tab: `GRACE_MS`.
- Pay rate: earnings are added in `complete()` as `state.balance += s.minutes` (cents).
