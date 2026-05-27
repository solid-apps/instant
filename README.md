# instant

A **WebTorrent client in your browser**, à la [instant.io](https://instant.io).
Paste a **magnet** / infohash, drop a **`.torrent`** file, or **seed any file** to
get a shareable magnet — files stream/render inline (video, audio, images, PDF)
and download. One self-contained HTML file, no build, **no server, no pod**.

## How it works

- Loads `webtorrent` from a CDN and runs a client entirely in the page.
- **Add** a magnet/infohash/.torrent → downloads over WebRTC; media files render
  inline, everything has a download link; live progress / peers / speed.
- **Seed** a file → it announces over `wss` trackers and shows a magnet to share;
  whoever opens it in `instant` (or any WebTorrent client) fetches it peer-to-peer.

## The honest caveat

WebTorrent only talks to **WebRTC / `wss`-tracker peers** — other browsers and
hybrid seeders. It **can't reach plain TCP/UDP BitTorrent peers** from a browser.
So it works *when web peers are around* (WebTorrent-seeded content) — which is
exactly why **seeding** is built in: seed to each other and it just works. It's a
general P2P transfer tool (same tech as webtorrent.io).

## Notes

- Pure client — nothing is stored on your pod (this is the instant.io-equivalent
  scope). Saving your magnet library to the pod is a possible follow-up.
- Uses default `wss` trackers (openwebtorrent / btorrent / webtorrent.dev).

## Run

Static — open `index.html`, or install via the **store** to `/public/apps/instant/`.

AGPL-3.0-only.
