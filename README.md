# STRONGER — Offline Workout Log (iPhone PWA)

A private, **offline-first Progressive Web App** for the 12-week three-day full-body muscle/tendon program. No account, subscription, external library, or network API is needed.

## What it does

- Workout A, B, C with all 19 program exercises, technique instructions, precautions, alternative movements, set/rep/RPE targets, and rest times.
- 12 training weeks, including lighter deload weeks 4 and 8.
- Track each set's **weight in pounds, repetitions/quantity, RPE, and completed status**. Automatically saves workouts in the iPhone's local browser storage.
- Rest countdown timer (while app is active), optional exercise additions, notes, finish/draft status.
- **History:** search/filter sessions, reopen and edit, review individual sets, delete sessions.
- **Progress:** completed workouts, sets, 12-week attendance, and exercise weight charts.
- **CSV export/import:** one row per set; opens in Apple Numbers, Excel, and Google Sheets.
- **JSON full backup/restore:** preserves sessions, individual sets, notes, and settings.
- Works offline after initial installation, via a service worker which caches all app code.

## Install on an iPhone with Add to Home Screen

The files must first be hosted on an **HTTPS website**. An HTML file opened from Files or a ZIP attachment cannot become a reliable offline iPhone home-screen app on its own.

**Free hosting using GitHub Pages:**

1. Create a GitHub account if needed. Create a new **public** repository, for example `stronger-workout-log`.
2. Upload **the contents** of this folder (`index.html`, `app.js`, `styles.css`, `sw.js`, `manifest.webmanifest`, and the `icons/` folder) to the **root** of the repository. Do not upload just the ZIP file.
3. On GitHub, open **Settings → Pages → Build and deployment**. Choose **Deploy from a branch**, `main`, `/ (root)`, then **Save**.
4. GitHub Pages will publish an HTTPS link similar to `https://YOUR-USERNAME.github.io/stronger-workout-log/`. Open your actual published link.
5. On your iPhone, open that link in **Safari** while connected to the internet. Wait for the app to load completely.
6. Tap **Share → Add to Home Screen → Add** (in newer Safari versions, you may need to scroll the Share sheet to find it).
7. Open **Stronger** from the home screen while still online once, then put your iPhone into airplane mode to test offline use.

### IMPORTANT — Back up your workouts!

Workout data is **local to the installed app and device**. GitHub hosts only the app's static code, **not** your workout logs. It cannot see or sync them.

Go to **Settings → Export backup** periodically, and save the `.json` file to Files/iCloud Drive. CSV export is ideal for spreadsheet review. Reinstalling the app, erasing website data, low-storage cleanup, or switching phones can remove local records. Before deleting/reinstalling, export a JSON backup, then import it on the new installation.

A home-screen PWA and an ordinary Safari tab may have different local storage; avoid switching between them when tracking your workouts.

## Updates / troubleshooting

- Updates to hosted code are fetched when the app next connects to the internet; previous offline files stay cached until updated. If you are working offline and already installed, you do not need any network.
- Rest timer is visible while the app is open. iOS can suspend apps in the background, so there are **no guaranteed background alerts** or timers.
- CSV is for tabular review and reimport. JSON is the **lossless backup format**.
- If you install from a non-HTTPS host or open the HTML file directly in Files, the service worker cannot work.
- All weights use **pounds**. For carries enter meters in the quantity box; bodyweight exercises can leave weight blank.

## Local desktop preview

From this directory, run a local server:

```sh
python3 -m http.server 8000
```

Then visit `http://localhost:8000` (localhost is allowed for PWA service workers in desktop browsers). You can also open `index.html` directly in most desktop browsers to preview and log; *offline home-screen installation requires HTTPS hosting*.

## Health disclaimer

This is a general workout tracker, not a medical device or prescribed rehabilitation. Stop painful or aggravating exercise; seek medical assessment for recurring neck pain, radiating symptoms, new weakness, or severe symptoms. Exercise instructions assume the previous neck injury is fully resolved.
