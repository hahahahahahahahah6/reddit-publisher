# reddit-publisher

One-tap Reddit publishing from your phone. A single static HTML page — no server, no build step.

## Why

Posting to Reddit from a datacenter IP gets you blocked by Reddit's bot detection. This page runs entirely in your phone's browser: you OAuth once, then every post goes straight from your device to Reddit's API. Nothing in between.

## Setup (one time, ~3 min)

1. On your phone, open `reddit.com/prefs/apps` in Safari and log in
2. Tap "are you a developer? create an app…"
3. Name: `one-tap-publisher`, type: **installed app**
4. Redirect URI: `https://hahahahahahahahah6.github.io/reddit-publisher/`
5. Copy the **client id** under the app name
6. Open the publisher page, paste the client id, tap "Connect with Reddit"

## Use

Pick a draft (or write your own), choose a subreddit, optionally pick a flair, tap Publish. Drafts live in your browser's localStorage — nothing leaves your device except the post itself.

## How it works

- Reddit OAuth 2.0 with PKCE (`response_type=code` + `code_challenge_method=S256`)
- Installed-app flow: `Authorization: Basic base64(client_id:)` — no secret
- Posts via `POST https://oauth.reddit.com/api/submit` directly from the browser
- Token refresh handled automatically (`duration=permanent`)

## License

MIT
