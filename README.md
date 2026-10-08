# QuizMaster

A responsive quiz management app built with HTML, CSS, Bootstrap, JavaScript and Firebase. The visual direction follows the supplied QuizMaster reference: vivid indigo and violet, rounded cards, an illustrated quiz preview, and clean student/admin entry points.

## Run it

Because the JavaScript uses ES modules, serve this folder from a local web server (opening `index.html` directly as a `file://` URL will not work in all browsers). For example, from this folder run `python -m http.server 8000`, then open `http://localhost:8000`.

The app works immediately in demo mode. It uses `sessionStorage` for the signed-in browser session and `localStorage` for demo quiz scores. Demo users are not securely authenticated; use the Firebase setup below for real accounts and cloud data.

## Enable Firebase

1. Create a Firebase project and register a Web app in the Firebase console.
2. Enable **Authentication → Email/Password** and create a **Cloud Firestore** database.
3. Copy the web app's config into `firebaseConfig` near the top of `app.js` (`apiKey`, `authDomain`, `projectId`, and `appId`).
4. Serve the app from localhost or a configured Firebase Hosting domain. Firebase browser modules are imported from Google's CDN.
5. Set Firestore rules so users can read/write only the records allowed by your app's roles. Do not rely on client-side role labels for authorization.

When Firebase config is present, registration/login uses Firebase Authentication and registration writes a profile document to `users/{uid}` in Firestore. Demo quiz definitions and quiz score history remain local in this starter; to persist them in Firestore, add quiz/attempt collections and appropriate security rules before deployment.

## Included interactions

- Student and admin registration/login entry points, with role selection.
- Six playable multiple-choice quizzes, countdown timer, score summary and local leaderboard updates.
- Responsive layout, animated hero quiz card, quiz browsing cards, and leaderboard.
- Session-only login state and Firebase config hook.
