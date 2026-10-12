# Charana Seva Walk Tracker — put it online (no app store)

This folder is the whole app. Upload it to any web host and walkers install it from a link.
It must be served over **https** (camera, GPS and Bluetooth require it). All hosts below do this for free.

## Step 1 — Live leaderboard database (5 minutes)
1. Go to https://console.firebase.google.com, create a project, then Build > Realtime Database > Create database.
2. Rules tab, paste this and Publish:
   `{ "rules": { "live": { ".read": true, ".write": true }, "results": { ".read": true, ".write": true } } }`
3. Copy the database URL into `config.js` between the quotes. Open rules let anyone write, so delete the database after the event.

## Step 2 — Upload the folder
**Easiest: Netlify Drop** — go to https://app.netlify.com/drop, drag this whole folder onto the page. You get a link like `https://something.netlify.app`. You can rename it in Site settings.
**Alternative: Firebase Hosting** — `npm i -g firebase-tools`, `firebase login`, `firebase init hosting` (public folder = this folder, single-page app = No), `firebase deploy`.
If you change `config.js` later, upload the folder again.

## Step 3 — Share the link
- Make a QR code of the link and put it on the flyer and at the start line.
- **Android (Chrome):** open the link, tap the menu, then "Install app". Heart-rate sensors, QR sign-in and GPS all work.
- **iPhone (Safari):** open the link, tap Share, then "Add to Home Screen". QR sign-in, GPS, steps and camera pulse check work. Bluetooth heart-rate sensors do not work in iPhone web apps.
- Walkers must tap "Allow" for camera and location when asked.

## Step 4 — Test before 24 October
Try 2–3 phones (at least one Android and one iPhone) on a short walk: sign in by QR, watch the leaderboard, sign out.
