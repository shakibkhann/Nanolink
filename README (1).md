# Vanish — Setup Guide

This tool has two modes:

## Right now (Local mode)
The `nanolink.html` file currently works **only within a single browser** (it uses localStorage). This is fine for testing, but it can't send messages between two different devices/people yet.

## Going live — connect Firebase

1. Go to firebase.google.com -> create a new project (free plan)
2. Enable **Firestore Database** (start in test mode)
3. Project Settings -> Add a Web app -> copy your `firebaseConfig` object
4. In `nanolink.html`, add this above the existing `<script>` tag:

```html
<script type="module">
import { initializeApp } from "https://www.gstatic.com/firebasejs/10.7.0/firebase-app.js";
import { getFirestore, doc, setDoc, addDoc, collection, getDocs, deleteDoc } from "https://www.gstatic.com/firebasejs/10.7.0/firebase-firestore.js";

const firebaseConfig = { /* paste your config here */ };
const app = initializeApp(firebaseConfig);
const db = getFirestore(app);
window.db = db;
</script>
```

5. Replace the five functions in the "LOCAL-MODE STORAGE ENGINE" section (`apiCreateId`, `apiSendMessage`, `apiListInbox`, `apiRevealAndDelete`) with Firestore calls — keep the function names, just change the internals.

I can write this Firebase integration code for you directly — just say "write the Firebase code."

## Publishing on GitHub

1. Add `nanolink.html` to your repo (or rename it to `index.html`)
2. Go to repo **Settings -> Pages** -> Source: `main` branch, root folder -> Save
3. After a few minutes it will be live at `https://<username>.github.io/<repo-name>/`

## Android app
Once the web version is confirmed working, we can build an Android wrapper (Kotlin + WebView, or a native UI) around the same Firebase backend.

## Note on design
There is no hidden tracking, spoofed sender identity, or silent background SMS in this tool — everything that happens is visible on screen. Keeping it this way matters for staying compliant with GitHub and Play Store policies.
