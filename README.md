# personal_apps

Four small static web apps with a landing page, hosted on GitHub Pages:
**https://coppolajonathan-lab.github.io/personal_apps/**

| App | Path | What it does | Refresh |
|---|---|---|---|
| 🎭 Baritenor Casting Call | `/theater/` | Upcoming community-theater musical auditions within about an hour of Tampa, filtered to baritenor roles, with musical, role, theater group, audition dates and show dates | Daily, 12:00 AM ET |
| 🏈 Scoreboard | `/sports/` | USF Bulls, Munster, Leicester Tigers, Buccaneers, Patriots: last result, form, standings, playoff odds | Daily, 12:00 AM ET |
| 🏠 Brandon 3/2 Watch | `/housing/` | Average 3-bed rent in Brandon, FL vs. the monthly payment on a typical 3/2 at 4.5%, with an interactive calculator | Mondays, 12:00 AM ET |
| 🐉 Campaign Forge | `/campaign-forge/` | Chatbot that turns a campaign pitch into a starter kit (D&D/fantasy or Dungeon Crawler Carl) | On demand (table passphrase via proxy, or your own key) |

## How it works

- Everything is plain HTML, CSS and JavaScript. There's no build step.
- Each data app reads its own `data.json`. Scheduled Claude tasks refresh those files and push to `main`, which triggers `.github/workflows/pages.yml` to redeploy.
- The update procedures live in [`agents/`](agents/). Edit those files to change what the agents do.
- Campaign Forge reaches Claude through a small Cloudflare Worker ([`worker/`](worker/)) that holds Jonathan's API key as a secret. Players enter a shared passphrase in Settings. Anyone can still choose "My own Anthropic API key" in Settings instead.

## Run locally

```bash
python3 -m http.server 8000
# open http://localhost:8000
```
