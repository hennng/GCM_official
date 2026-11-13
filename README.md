# GCM_official

## Firebase setup

1. Create a Firebase project, add a web app, and enable Cloud Firestore.
2. Copy the web app configuration into `FIREBASE_CONFIG` in `index.html`. Do not use a service-account key in the page.
3. In Firebase Console, open **Authentication → Sign-in method**, enable **Google**, and add the GitHub Pages domain under **Authentication → Settings → Authorized domains**.
4. In the Firestore console, create a document in the private `editors` collection for each admin. Use that Google account's email as the document ID, with a boolean field `active: true`. Do not add client read/write access to this collection.
5. Open **Firestore Database → Rules**, paste the contents of `firestore.rules`, and publish them. The email allowlist stays in Firestore rather than the public page source.
6. Create documents in the `events`, `members`, `songs`, and `sessions` collections, or sign in with the authorized account and manage them from the page's **設定** tab. Past events are not filtered out; dates should use `YYYY-MM-DD`. The event selector lists newest first.
7. To restore an exported dashboard JSON, sign in as an editor, open **設定 → 批次匯入 Firestore JSON**, select the export, review the counts, and confirm. Existing document IDs are skipped, not overwritten. The importer validates references and writes related collections in dependency order.
8. Publish the repository root with GitHub Pages.

Dashboard data is publicly readable, but only the configured Google account(s) can create, edit, or delete documents. Do not publish private information in these collections.