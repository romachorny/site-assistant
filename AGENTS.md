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
