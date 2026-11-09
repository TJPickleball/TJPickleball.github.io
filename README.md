# Trader Jacks Pickleball League IV

The league website for TJPL4, run by Pickleball Cook Islands.

Live site: https://tjpickleball.github.io

## How the site is built

| File | What it is | Who edits it |
|---|---|---|
| `data/league.json` | Teams, players, fixtures, scores, news and the subs list | Admins, after every round |
| `index.html` | Layout, styling and app logic | Rarely, only to change how the site works |
| `images/` | Logos | Rarely |

The ladders are worked out automatically from the scores, so you never edit them by hand.

Any change merged to the `main` branch goes live on GitHub Pages within a minute or two.

## Updating the site with Claude

With the GitHub connector set up in Claude, ask in plain English. For example:

- "In the TJPickleball site, enter the Round 5 Division 1 scores: Franks & Beans 11 Jammin 7, …"
- "Add a news post dated Sat 14 Nov titled ROUND 5 WRAP with this text: …"
- "Add Mere Tauira to the subs list, phone 55555, Divisions 2 and 3."
- "Update the 'updated' line to say Updated after Round 5 (Sat 14 Nov)."

Claude should only change `data/league.json` for these updates.

## Updating by hand

Open `data/league.json` on GitHub, click the pencil icon, make the change and click **Commit changes**.

- **Scores:** find the game in `games` and change `"score": null` to `"score": [11, 7]`. The first number is `teamA`'s score and the second is `teamB`'s.
- **News:** add a new line at the top of `news` with the next `id` number. The newest post shows a "new announcement" banner on the home page.
- **Subs:** add or remove lines in `subs`. `divs` lists the divisions the player can sub in. Use `"rank": 1` etc. to set an order.
- **Updated line:** change `season.updated` after each round.

Keep the commas and quote marks exactly as they are. If the site shows "Could not load league data", the JSON has a typo; check the last edit.

## Analytics

`index.html` has a GoatCounter snippet commented out near the top. Sign up free at goatcounter.com, then uncomment the snippet and put your code into its URL.

## Privacy

This repository is public. Everything in `data/league.json`, including subs' phone numbers, can be read by anyone, and it stays in the Git history even after it's removed. Only list numbers people have agreed to share publicly.
