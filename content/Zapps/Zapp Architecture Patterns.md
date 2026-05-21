---
title: Zapp Architecture Patterns
tags:
  - zapps
  - architecture
---

The constraints of the [[Zapp Manifesto|Zapp philosophy]] (no servers, no accounts, no tracking) rule out the standard Web 2.0 architectures. The patterns below are the recurring engineering techniques that make Zapps possible anyway.

## 1. Bring Your Own Key (BYOK)

**Problem:** Some apps need to call third-party services (GitHub, OpenAI, Strava, Hacker News). Embedding a developer-owned API key into a public client-side app is unsafe — anyone can scrape and abuse it.

**Solution:** The app prompts the user to supply their own Personal Access Token (PAT) or API key. The key is stored only in the user's local storage. All API calls are made directly from the client to the third party. The developer never proxies requests.

**Implications:** Users with technical literacy handle this easily. For non-technical users, generating a PAT or API key is a real onboarding hurdle — Zapps should accept that trade-off rather than try to mask it with a "convenience" backend.

## 2. The Napkin Pattern (URL state encoding)

**Problem:** Sharing data between users normally requires a database to hold the shared state.

**Solution:** Serialize the app's entire state to JSON, compress it (LZMA or base64), and append it to the URL hash. The receiving client decodes the URL to recreate the exact state locally.

```
app.com/#state=eJyrVkrLzC1WslJQys9LTU8t...
```

**Implications:**

- Sharing is stateless — no server holds anyone's data.
- Privacy is structural: each shared URL is a one-time, self-contained payload. Even if leaked, only that exact snapshot is revealed; the database is not.
- A subtle catch: URLs may be logged by corporate firewalls and ISPs. For sensitive data, encrypt the payload client-side with a password kept *only in the URL fragment* (which never reaches the server).

Used in Back-of-the-Napkin-style calculation Zapps.

## 3. The Walkie-Talkie Pattern (P2P networking)

**Problem:** Real-time collaboration (multiplayer games, shared editing, voice/video) normally requires a centralised signaling server.

**Solution:** Treat the network like a walkie-talkie, not a cell phone. Use peer-to-peer transports and public, decentralised signaling infrastructure:

- **WebRTC over LAN** — for same-room collaboration, no internet required.
- **Web Bluetooth** — direct device-to-device pairing.
- **Public WebTorrent trackers** — used as a free signalling layer to introduce two peers.
- **Public Nostr relays** — broadcast WebRTC signalling data to a public relay to find another peer.
- **Public DHTs** — find peers via the BitTorrent network without a central server.

**Implications:** P2P comes with distance and reliability limitations, just like a real walkie-talkie. For some classes of app (live multiplayer at global scale), the Zapp model genuinely cannot compete with a server-backed approach. For local games, classroom collaboration, and family sharing, it works fine.

## 4. Git as Backend

**Problem:** Browser local storage is volatile. iOS and Android will clear it when space is needed. Users who haven't exported their data recently can lose it forever.

**Solution:** Use a user-provided GitHub Personal Access Token to commit their JSON or SQLite state file directly to a private repository via the GitHub REST API.

- Every save or sync action pushes the latest state file to the user's repo.
- The user gets free, version-controlled, cloud-backed storage that the developer doesn't pay for.
- The user can access the same state from multiple devices by reading the latest file from their repo on load.

**Implications:** Same BYOK caveat — easy for developers, harder for non-technical users. For a Jekyll-style headless blog publisher Zapp this is a natural fit; for a casual game it's overkill.

## 5. Naked Data (open file formats only)

**Rule:** Internal storage may be optimized (IndexedDB, Hive, SQLite WASM). The *export* must be universal.

A Zapp must include a one-click export to open, human-readable formats. See [[Zapp Data Formats]] for the recommended formats per data type.

The Zapp should also actively *prompt* the user to back up periodically — "It's been 7 days, download your data" — because relying on volatile browser storage alone is fragile.

## 6. Local-First Sync via OS Folders

**Problem:** Some users want continuity across devices without dealing with GitHub PATs.

**Solution:** Save state files directly into a folder that's already synced by iCloud Drive, Google Drive, Dropbox, or OneDrive. The Zapp doesn't manage the sync; the OS does. The Zapp just reads and writes a file.

**Implications:** Free cross-device sync for users who already use a cloud-storage service, with zero developer infrastructure.

## 7. Static Hosting Only

A Zapp web app is a bundle of static files (HTML, CSS, JS, WASM) that any free static host can serve: GitHub Pages, Cloudflare Pages, Netlify free tier. No serverless functions (which can have egress charges), no databases, no auth providers.

Cost to scale from 1 to 1,000,000 users: $0.

## 8. Offline-First as a Strict Requirement

A web Zapp must work offline after first load. Implement a service worker that caches the entire app shell and all required assets. If the user lands on the page once, the app must remain usable forever even if the user later goes offline or the developer takes the site down.

## Where Zapps cannot reach

Knowing the limits is part of the discipline:

- **Secret-dependent third-party APIs** without a BYOK alternative. Apps that need OpenAI or weather data without exposing user keys often need a backend.
- **Massive dynamic datasets** that can't be downloaded to the client (e.g. flight aggregators searching 50GB of inventory).
- **Reliable push notifications**, especially on iOS — these require a central server holding device tokens.
- **Real-time global multiplayer** at scale — possible with public signalling, but unreliable.

For these, the Zapp model is a poor fit. Better to pick a different architecture honestly than to fake the philosophy.

## See also

- [[Zapp Manifesto]]
- [[Zapp Data Formats]]
- [[Zapp Cursor Rules]]
- [[Forking Over Modding]]
