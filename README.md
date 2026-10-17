# Sprout Focus

A Forest-style focus timer that runs entirely in the browser. Plant a tree, stay on the page while it grows, and earn in-game money: **1 minute of completed focus = 1¢**. Spend it in the Wallet tab on simple rewards.

## Features
- Pick a tree (Oak, Pine, Blossom, Maple) and a duration (5–120 min)
- Tree grows through stages as the timer runs
- **Strict mode**: leave the tab for more than 10 seconds and the tree withers (no money)
- Give up early → tree withers, nothing earned
- Forest tab shows every tree you've grown or lost, plus stats
- Wallet tab: balance, preset rewards, custom redeem amount, redemption history
- All data is saved in your browser (localStorage); nothing leaves your device

## Deploy to GitHub Pages
1. Create a new repository on GitHub (e.g. `sprout-focus`).
2. Upload `index.html` (and this README) to the root of the `main` branch.
3. Go to **Settings → Pages**, set **Source** to "Deploy from a branch", choose `main` and `/ (root)`, then **Save**.
4. After a minute your site is live at `https://<your-username>.github.io/sprout-focus/`.

## Testing quickly
Add `?debug` to the URL to make each "minute" last one second, e.g. `.../sprout-focus/?debug`.

## Tweaking
- Rewards list: edit the `REWARDS` array in `index.html`.
- Grace period for leaving the tab: `GRACE_MS`.
- Pay rate: earnings are added in `complete()` as `state.balance += s.minutes` (cents).
