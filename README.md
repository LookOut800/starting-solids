# Starting Solids

Alexander's first-foods diary: foods tried, allergens, nutrients, and a roadmap of what to try next.
It's a static site on GitHub Pages. Data lives in Firebase Firestore, and only two Google accounts can read or write it.

## One-time setup (about 10 minutes)

### 1. Create the Firebase project
1. Go to https://console.firebase.google.com and click **Create a project**. Name it e.g. `starting-solids`. Google Analytics isn't needed.
2. **Build → Authentication → Get started → Sign-in method → Google → Enable.** Pick your email as the support email and save.
3. **Build → Firestore Database → Create database.** Choose a location near you and start in **production mode**.
4. Open the **Rules** tab, paste in the contents of `firestore.rules`, replace the two placeholder emails with yours and your wife's, and click **Publish**.
5. **Project settings (gear) → General → Your apps → Web (`</>`).** Register an app called `Starting Solids`; you don't need Firebase Hosting. Copy the `firebaseConfig` values into `firebase-config.js`.

### 2. Publish on GitHub Pages
1. Push this folder to a GitHub repo.
2. In the repo, go to **Settings → Pages → Build and deployment**, set **Source** to `Deploy from a branch`, and pick `main` and `/ (root)`.
3. After a minute the site is at `https://<your-username>.github.io/starting-solids/`.

### 3. Let Google sign-in work on that address
In Firebase, go to **Authentication → Settings → Authorized domains → Add domain** and add `<your-username>.github.io`.

### 4. Put it on your phones
Open the site, sign in with Google, then add it to the home screen. On iPhone that's **Share → Add to Home Screen**; on Android it's **⋮ → Add to Home screen**.

## Is it private?
- The page's code is public on GitHub, but it contains no records.
- The Firebase config values aren't secret. They only identify the project.
- The diary entries are protected by the Firestore rules. Anyone not signed in as one of the two listed Google accounts is refused.
- The page asks search engines not to index it.

## Files
- `index.html`: the whole app
- `firebase-config.js`: your Firebase project's web config
- `firestore.rules`: access rules to paste into the Firebase console (put the real emails in the console, not in this public file)
- `manifest.webmanifest` and `icon-*.png`: home-screen icon and name
