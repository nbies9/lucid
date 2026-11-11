# LUCID launcher

A tiny web app that puts the LUCID eclipse icon on a phone or computer home screen.
Opened from the installed icon, it goes straight to Nick's private LUCID board (which still needs his claude.ai sign-in).
It holds no data of its own.

Live at https://nbies9.github.io/lucid/

## How it works

- `index.html`: opened from the installed icon (`?app=1`, or standalone display mode) it sends the browser to the board. Opened in a normal tab it shows an Install button and a link to the board.
- `manifest.webmanifest`: the installed app's name, colors and icons. `id` is fixed so a phone keeps treating it as the same app if `start_url` ever changes.
- `sw.js`: a pass-through service worker. It caches nothing, so it can never show an old copy of the page.
- The board's address is in `index.html` twice (the `BOARD` variable and the link). Change both together.

## Changing it

Push to `main`. GitHub Pages redeploys in a minute or two, and browsers may reuse the old files for up to 10 minutes.
The installed icon and name come from the manifest; Chrome on Android re-checks it about once a day and can take a few days to apply a change.

## Keep in mind

- This repo and site are public. The board link is not a secret (the board is private and asks for a sign-in), but nothing private belongs here.
- The site has to stay public and on GitHub Pages. The installed icon opens this page first, so making the repo private, renaming it or turning Pages off breaks the icon.
- With no connection the page can't load and the browser shows its own offline page. The board needs a connection anyway.
