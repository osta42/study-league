# Study Leagues

A live study competition anyone can start. Create a league, send your friends the link and code, and compete on weekly, monthly and yearly leaderboards.

Live site: https://osta42.github.io/study-league/leagues/

- **Create a league:** open the site, pick a league name, a join code, how many players (2–10), your name and a 4-digit PIN. You become the league admin.
- **Invite friends:** tap **Copy invite link**. As admin it copies the link and the code together.
- **Join:** open the invite link, pick a free spot, enter the league code, your name and a PIN.
- **On another device:** tap **That's me** on your profile and enter your PIN.
- **Admin (⚙️ League settings):** rename the league, change the join code, reset a player's PIN, remove a player.

Scoring per session: hour 1 = 100 pts, hour 2 = 110, hour 3 = 120 (each extra full hour is worth 10 more); leftover minutes = 1 pt each. Streaks, weekly medals, achievements, ranks, profile photos and banners, live feed with reactions, and chat are all per league.

Built with plain HTML, CSS and JavaScript, hosted on GitHub Pages, with Firebase (Firestore + anonymous sign-in).

## Firebase setup (already done)

1. **Authentication → Sign-in method:** Anonymous enabled.
2. **Firestore Database:** production mode.
3. **Firestore → Rules:** the whole of `firestore.rules`, published.
4. **index.html:** the `firebaseConfig` block holds the project's web config.

Data layout: everything lives under `leagues/{leagueId}`. A league can only be opened by its exact id (the invite link); nobody can list all leagues. Join codes and PINs are never readable by players.
