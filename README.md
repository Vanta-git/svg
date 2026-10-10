# Vanta Browser

Uses **only** your local proxy files:

| Folder | Role |
|--------|------|
| `vanta/` | Proxy engine + controller (`$vanta`, `$vantaController`) |
| `black/` | Epoxy transport (`EpoxyTransport`) |
| `67/` | Libcurl transport (`LibcurlClient`) |
| `sw.js` | Service worker → `vanta/vanta.sw.js` |

No `scramjet/` or `controller/` folders.

## Prefix

Proxied paths use `/~/sj/` (same style as Breeze), handled by the Vanta controller.

## Run

Serve this folder over **HTTPS or localhost**, open `index.html`.
Set a working WISP in Settings if defaults fail.


## Repository-subpath proxy prefix

The controller now derives its proxy prefix from the current deployment path (`new URL('./~/sj/', location.href).pathname`). This keeps the `/~/sj/` route beneath a repository subpath such as `/gh/Vanta-git/svg@main/` instead of forcing it to the domain root. The hosting origin must still support service workers and the proxy runtime; static jsDelivr CDN hosting does not provide a service-worker runtime for a hosted proxy app.
