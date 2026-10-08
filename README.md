# TuneGuessr

A free, ad-free browser music-guessing party game by **Mike Wong**. Built with React, TypeScript, Vinext, and Cloudflare D1.

## Important: placeholder audio

**The game does not currently include or stream copyrighted popular-song recordings. I have not obtained the licenses or provider approval needed to use them.**

The built-in audio is temporary royalty-free filler: synthesized public-domain melodies, mostly familiar children’s songs such as *Twinkle, Twinkle, Little Star*, *Mary Had a Little Lamb*, and *Row, Row, Row Your Boat*. These demonstrate the game mechanics; they are not Spotify tracks or current chart hits.

My goal is to replace this filler with real song intros when I find a workable, authorized solution, such as a licensed clip provider or permission from rights holders. All online categories currently share the same demo catalog. Noncommercial status does not automatically grant music rights.

## Features

- Five-round solo games and multiplayer rooms for up to 12 players
- Server-checked answers, shared timers, and persistent demo leaderboards
- Trending, Rap, Pop, Rock, and Indie category selection
- System, Light, and Dark themes, with saved manual preferences
- Local audio-file mode with 1-, 3-, 6-, and 12-second intros
- Tutorial slideshow, responsive layouts, and stream-friendly view
- No advertising, subscriptions, or paid upgrades

## How to play

Choose a nickname and category. Play solo, create a room, or enter a friend’s room code. Tap play, type the song title, and lock in one answer within 25 seconds. Each correct answer earns one point; the host advances through five rounds.

For actual recordings you are authorized to use, choose **Play intros from your audio files**. Edit the answer titles, then start a random set. Files remain in the browser session and are never uploaded. Local scores do not enter the global leaderboard, and file ownership does not grant broadcasting rights.

## Current limitations

- Spotify and commercial music catalogs are not connected.
- Google, email, and Spotify sign-in are not configured; the hosted beta uses ChatGPT sign-in.
- Discord, Twitch, Kick, and TikTok support is through room links and screen capture, not native bots or Activities.
- The hosted beta is private until its sharing settings are changed.
- Build, type checks, and backend gameplay tests passed; browser audio and multi-device testing remain.

## Source and architecture

The source includes the React UI, Worker JSON API, D1 schema and migrations, music/audio adapters, mascot, and dependency lockfile. Private deployment identifiers and local build files are excluded.

- `app/page.tsx`: game interface and theme controls
- `app/local-music.tsx`: local recording intros
- `app/api/game/route.ts`: profiles, rooms, guesses, and scoring
- `lib/catalog.ts` and `lib/audio.ts`: demo catalog and audio adapter
- `db/` and `drizzle/`: persistent data and migrations

## Development

Requires Node.js 22.13+ and pnpm.

```sh
pnpm install --frozen-lockfile
pnpm exec tsc --noEmit
pnpm run build
```

Online rooms and saved scores require a configured D1 database and the trusted hosting authentication adapter. See the detailed README in the source for deployment and API notes. No credentials are included.

## Future work

Integrate an authorized popular-song catalog, configure public authentication, test multi-device playback, and add native streaming integrations. The separated rules, JSON API, and audio adapter provide a starting point for future iOS and Android apps; native apps are not included yet.
