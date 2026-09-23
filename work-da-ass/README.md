# Work da ass — fitness tracker PWA

Independent fitness tracker inspired by the category of workout apps, not affiliated with STNDRD.

## Included in v1
Custom routines, 25 built-in exercises and custom exercises, exercise text guidance, set/reps/kg logging, automatic rest timer, rep-range progression suggestions, workout history, best single-set volume records, muscle-group set charts, monthly workout calendar, manual food/macronutrient logging, body-weight tracking, local offline storage, JSON export/import, and optional Supabase email login/cloud sync.

**Not included:** licensed exercise demonstration videos, a searchable commercial food database, push notifications, Apple Health integration, or guaranteed conflict-free multi-device editing. Exercise guides are text-only. The app's PR metric is best single-set volume (kg × reps), not one-rep max. The sync feature merges entries by ID but concurrent edits or deletions across devices may not resolve as expected. Always export backups.

## Run on Windows

1. Install Node.js from https://nodejs.org if needed.
2. Open PowerShell inside this folder and run `npx serve .` (or `python -m http.server 8000` if Python is installed).
3. Open the localhost address printed in the terminal. Service workers need HTTPS or localhost.

## Install on iPhone for free

1. Put the files on an HTTPS static host such as GitHub Pages, Cloudflare Pages or Netlify. GitHub Pages: create a repository, upload the **contents** of this folder to its root, then Settings > Pages > Deploy from branch > main / root. Wait for the published HTTPS link.
2. Open the HTTPS link in **Safari** on your iPhone.
3. Tap Share > Add to Home Screen > Add (the exact menu position varies by iOS version).
4. Launch from the new icon once while online. Later launches and existing local data work offline. Hosting may have platform-specific free-plan limits.

## Optional Supabase cloud login

1. Create a Supabase project at https://supabase.com.
2. In SQL Editor run `supabase.sql` in this folder. It creates a row-level-security-protected table.
3. Under Authentication > Providers, enable Email and decide whether email confirmation is required. For sign-up with confirmation, follow the confirmation email before login.
4. Under Project Settings / Connect, copy the project URL and **publishable or legacy anon** key into the app's More > Optional cloud account. NEVER use a service_role or secret key in the browser.
5. Sign up or log in. Tap Sync Now. The app attempts background sync when local data changes and when connectivity returns.

**Privacy and sync caveats:** local data resides in the browser's localStorage and can be erased by clearing site data. Cloud sync is optional, and Supabase's free plan may have quotas and inactivity policies. Do not use this version as the sole copy of important records. There is no dedicated server-side conflict resolution or account recovery UI; password recovery can be handled through Supabase's hosted/admin flow. Don't use the same account simultaneously on multiple devices when editing. For public release, add production-grade conflict handling, accessibility review, privacy policy, and more extensive testing.

## Updating

Replace hosted files and bump `CACHE` in `sw.js` (e.g. v2). Reload online to install the update. Existing local data remains under the same domain, unless site data is cleared.
