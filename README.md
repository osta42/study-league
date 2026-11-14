# Study League

A live study competition for up to 6 friends. Open the link, pick a spot, type your name and a 4-digit PIN, and you're in. No accounts, no sign-up.

Live site: https://osta42.github.io/study-league/

- Each full hour = 100 points, each extra minute = 1 point (1h 30m = 130 pts).
- Weekly (Monday–Sunday), monthly and yearly leaderboards. Totals reset on their own; study sessions are never deleted.
- Clock in while you study. Everyone sees who's online and who's studying.
- You can only change your own profile and hours.

Built with plain HTML, CSS and JavaScript, hosted on GitHub Pages, with Firebase (Firestore + anonymous sign-in) for the shared league.

## How players use it

- **Join:** open the link, choose a free spot, type a name and a 4-digit PIN, then tap **Join the league**. That browser now remembers you.
- **On another phone or computer:** tap **That's me** on your profile and enter your PIN.
- **Log out on a shared device:** tap **Log out of my profile** under the clock button. Your profile and hours stay.

## Firebase setup (already done for this league)

1. **Authentication → Sign-in method:** enable **Anonymous**. Leave "Auto clean-up" off.
2. **Firestore Database:** create the database in production mode.
3. **Firestore → Rules:** paste the whole of `firestore.rules` and click **Publish**.
4. **index.html:** the `firebaseConfig` block holds the project's web config.

## Managing the league

- **Remove a player or free up a spot:** in Firebase → Firestore Database → Data, delete that player's document under `profiles` (s1 to s6) and the matching document under `secrets`.
- **Someone forgot their PIN:** in `secrets`, open their spot (e.g. `s3`) and change `pin` to a new 4-digit number. Their already-linked devices will need the new PIN too.
- **Updating the site:** upload the changed files to this repository (Add file → Upload files). GitHub Pages updates within a minute or two.

## Good to know

- A 4-digit PIN is fine for friends, but it isn't bank-grade security; someone determined could guess it.
- Firebase's free plan easily covers 6 people.
