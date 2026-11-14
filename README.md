# Study League

A live study competition for up to 6 friends. Sign in with Google, claim a spot, clock in while you study, and climb the weekly, monthly and yearly leaderboards.

- Each full hour = 100 points, each extra minute = 1 point (1h 30m = 130 pts).
- Weeks run Monday to Sunday. Weekly, monthly and yearly totals reset on their own; no sessions are ever deleted.
- You can only change your own profile and hours. Everyone can see who is online and who is studying.

Built with plain HTML, CSS and JavaScript, hosted on GitHub Pages, with Firebase for sign-in and the shared database.

---

## Setup (about 15 minutes, all in the browser)

### Part 1 – Create the Firebase project

1. Go to https://console.firebase.google.com and sign in with your Google account.
2. Click **Create a project**, name it (for example `study-league`), and finish the steps. Google Analytics is not needed.
3. **Add a web app:** on the project home page click the **`</>`** (Web) icon, give it a nickname, and click **Register app**. Leave "Firebase Hosting" unticked.
4. Firebase shows a `firebaseConfig = { ... }` block. **Copy it**; you need it in Part 2.
5. **Turn on Google sign-in:** left menu → **Build → Authentication** → **Get started** → **Sign-in method** → **Google** → **Enable** → choose a support email → **Save**.
6. **Create the database:** left menu → **Build → Firestore Database** → **Create database** → pick a location near you → start in **production mode** → **Create**.
7. **Add the security rules:** in Firestore open the **Rules** tab, delete what is there, paste the whole contents of `firestore.rules` from this folder, and click **Publish**.

### Part 2 – Connect the website to Firebase

Open `index.html` and find the block near the bottom that starts with:

```js
const firebaseConfig = {
  apiKey: "PASTE_API_KEY",
```

Replace those `PASTE_...` values with the values from step 4. (These values are safe to publish. The security rules are what protect the data.)

### Part 3 – Put it on GitHub Pages

1. Go to https://github.com/new and create a **public** repository, for example `study-league`.
2. On the new repository page click **uploading an existing file**, drag in `index.html`, `firestore.rules` and `README.md`, and click **Commit changes**.
3. Go to the repository's **Settings → Pages**. Under **Build and deployment**, set **Source** to *Deploy from a branch*, choose branch **main** and folder **/ (root)**, then click **Save**.
4. After a minute or two, the page shows your address: `https://YOUR-USERNAME.github.io/study-league/`.

### Part 4 – Allow your website to use Google sign-in

In Firebase: **Authentication → Settings → Authorized domains → Add domain**, and add:

```
YOUR-USERNAME.github.io
```

Without this, the sign-in pop-up will refuse to work on your site.

### Part 5 – Invite your friends

Send them the GitHub Pages link. Each friend signs in with Google, picks a free spot (up to 6) and types their name.

---

## Good to know

- **Online status** means "had the page open in the last ~2 minutes". **Studying** means clocked in. If someone closes the page while clocked in, they still show as studying until they come back and clock out.
- **Who can see the league:** anyone with the link who signs in with Google can view it, and can join while spots are free. Once all 6 spots are taken, newcomers can only watch.
- **Fixing mistakes / removing a player:** in Firebase → Firestore Database → Data, open `members`, and edit or delete that person's document.
- **Free limits:** Firebase's free plan (Spark) easily covers 6 people. It allows about 50,000 reads and 20,000 writes per day.
- **Updating the site:** edit the file, then upload it again to the repository (Add file → Upload files). GitHub Pages updates within a minute or two.
