# GCM_official

## Firebase setup

1. Create a Firebase project, add a web app, and enable Cloud Firestore.
2. Copy the web app configuration into `FIREBASE_CONFIG` in `index.html`. Do not use a service-account key in the page.
3. In Firebase Console, open **Firestore Database → Rules**, paste the contents of `firestore.rules`, and publish them.
4. Create the initial `events`, `members`, `songs`, and `sessions` documents in Firestore. The page is public and only edits attendance and scores; other collections are read-only from the page.
5. Publish the repository root with GitHub Pages.

The rules make all dashboard data publicly readable. Anyone who can access the page can change any member's attendance and scores. Do not publish private information in these collections.