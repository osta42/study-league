# Study League

A live study competition for up to 6 friends. Open the link, pick a spot, type your name and a 4-digit PIN, and you're in. No accounts, no sign-up.

Live site: https://osta42.github.io/study-league/

- **Scoring per session:** hour 1 = 100 pts, hour 2 = 110, hour 3 = 120 (each extra full hour is worth 10 more); leftover minutes = 1 pt each. So 45m = 45, 1h 30m = 130, 2h = 210, 3h = 330.
- Weekly (Monday–Sunday), monthly and yearly leaderboards with an animated top-3 podium. Totals reset on their own; study sessions are never deleted.
- 🔥 Daily streaks, badges, weeks-won counts, last week's champion crown, and a Monday recap.
- Live feed of clock-ins, sessions and lead changes, with 🔥 👏 💀 reactions.
- Calendar with month view and a full-year heatmap.
- You can only change your own profile, hours and reactions.

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
