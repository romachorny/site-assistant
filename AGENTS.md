# AGENTS.md

## Project overview

GenVidPro Site Assistant — two standalone client-side JavaScript files (`assistant.js`, `push.js`) designed to be loaded by pages on genvidpro.com. No framework, no build step, no backend in this repo.

- `assistant.js` — floating chat widget: pill button, chat panel, multilingual greetings (en/ru/he), dictation, TTS, posts to `/chat` endpoint, lead notifications via Web3Forms API (key hardcoded).
- `push.js` — web push subscription UI: needs an element with `id="gvAppBtn"` or `data-gv-push` attribute to attach its buttons. Posts to `/push-sub` and `/push-test` endpoints.

## Running in Base44

Served as static files via `nginx:alpine` on port 3000. The repo root is bind-mounted read-only into the container. See `docker-compose.base44.yml`.

The `/chat`, `/tts`, `/push-sub`, and `/push-test` endpoints do not exist in this repo (they live on the genvidpro.com server). The chat widget falls back gracefully to a "no connection" message; push buttons show but subscription requests will fail. The UI itself is fully functional.

## No external credentials required

Web3Forms access key and VAPID public key are hardcoded in the JS source. No secrets needed to boot.

## The preview address has to be short enough to resolve

The sandbox hostname is `<port>-<appId>[--b-<short>]-<sandboxId>.imported.base44-preview.app`,
and a DNS label may hold 63 characters. On **main** that label is 54 and resolves. On a
**named branch** Base44 inserts `--b-xxxxxxx`, which takes it to 65 — over the limit, so the
address resolves nowhere, in any browser or client. Measured 30.09.2026:

    3000-<appId>-<sandboxId>                 54 characters, resolves
    3000-<appId>--b-xxxxxxx-<sandboxId>      65 characters, "label too long"

So the preview has to run on **main**. A branch preview of this repo cannot be opened at all,
and the failure looks nothing like the 403 this setup was built to fix: the name simply does
not exist, and nothing ever reaches nginx.
