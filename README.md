# GRIDIRON Fantasy League

A Vite + Firebase starter for a custom fantasy league. The commissioner imports players, manually assigns points, starts a draft, and controls weekly matchups. Firestore listeners keep member screens current.

## 1. Firebase setup
1. Create a Firebase project and register a Web app.
2. Authentication → Sign-in method → enable Email/Password.
3. Create a Cloud Firestore database in production mode.
4. Copy the web app config into `src/firebase.js`.
5. Publish `firestore.rules` in Firestore → Rules, or deploy with Firebase CLI.
6. Add your GitHub Pages domain to Authentication → Settings → Authorized domains if needed.

## 2. Local development
Install Node.js 22+, then:

```sh
npm install
npm run dev
```

## 3. GitHub Pages deployment
1. Create a GitHub repository, for example `gridiron`.
2. Edit `vite.config.js` and replace `/REPLACE_WITH_REPOSITORY_NAME/` with `/gridiron/` (use your actual repository name). If publishing to `username.github.io` repository root, use `/`.
3. Push all project files to the `main` branch.
4. Repository Settings → Pages → Build and deployment → Source: **GitHub Actions**.
5. Wait for the workflow in the Actions tab to finish.
6. In Firebase Authentication settings, add the published GitHub Pages host to Authorized domains.

## Notes / current MVP limits
- Email/password accounts and profile search work after Firebase setup.
- League code joining, member readiness, draft picks, custom player points, matchup scheduling, and three-game scoring are included.
- Email invitations are stored as in-app invite records; this starter does not send email messages. Share the league code with friends to join.
- Scores are manually entered, not fetched from NFL data.
- The UI restricts draft turns and roster sizes, but a production deployment should move draft-order validation, roster caps, and matchup finalization into trusted Cloud Functions. Do not treat client-side checks alone as tamper-proof.
- Test security rules with the Firebase Rules Simulator and two test accounts before using with friends.
