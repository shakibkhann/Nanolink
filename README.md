# Nanolink (Vanish)

A self-destructing message tool. Create a unique ID — no phone number required — and send a message to someone's ID. Once they open it, it's permanently deleted.

## Features
- Unique ID signup, no phone number needed
- Messages are deleted permanently after being read once
- No hidden tracking, no spoofed sender identity, no silent background messaging — everything happens visibly on screen
- Lightweight static web app, deployable via GitHub Pages

## Current status
The app currently runs in **local mode** (browser-only storage via localStorage), meaning it works for testing on one device but doesn't yet sync messages between different people. See the setup notes below to connect it to Firebase for live, cross-device use.

## Tech stack
- HTML / CSS / JavaScript (no framework)
- Firebase Firestore (for live backend — setup required)

## Setup
1. Clone or download this repo
2. Open `nanolink.html` in a browser to test locally
3. To make it work across devices, connect a Firebase project (see comments in `nanolink.html` under the "LOCAL-MODE STORAGE ENGINE" section)

## Deploying
This is deployed via GitHub Pages. Push `nanolink.html` (renamed to `index.html`) to the `main` branch and enable Pages under repo Settings.

## License
See [LICENSE](./LICENSE).
