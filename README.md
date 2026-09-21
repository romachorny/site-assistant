# Site Assistant


The assistant that sits on [genvidpro.com](https://genvidpro.com): it answers a visitor, works out what they actually need, and hands over a qualified brief instead of a bare "contact us" form.


## Why it exists


A small studio loses most leads in the gap between interest and the first message. The assistant closes that gap: it replies immediately, in the visitor's own language, and asks the three questions that decide whether a job is real — what, when, what budget.


## What it does


- Answers in the language the page is rendered in, Hebrew and Arabic included, right to left.
- Collects the brief step by step instead of dumping a form: one question at a time, each answer stored locally so a reload does not lose it.
- Recognises the service the visitor is circling around (film, PWA, WhatsApp automation, site) and routes the brief to the matching page.
- Hands the finished brief to WhatsApp with the text already written, so the visitor only presses send.
- Falls back to a plain form when scripting is blocked, so no lead is lost to an ad blocker.


## Files


- `assistant.js` — dialogue engine, language handling, brief state, WhatsApp handoff
- `push.js` — web push subscription and notification payloads


## How this is built

Every idea, product decision and creative direction here is mine. The code is written in pair with Claude: I design, decide and review, the agent types and tests.

## Notes


No framework, no chat SDK, no third party widget: the whole thing is one script that the page loads, so it costs nothing per conversation and sends no visitor data to anyone but the site owner.

# Site Assistant

The assistant that sits on [genvidpro.com](https://genvidpro.com): it answers a visitor, works out what they actually need, and hands over a qualified brief instead of a bare "contact us" form.

## Why it exists

A small studio loses most leads in the gap between interest and the first message. The assistant closes that gap: it replies immediately, in the visitor's own language, and asks the three questions that decide whether a job is real — what, when, what budget.

## What it does

- Answers in the language the page is rendered in, Hebrew and Arabic included, right to left.
- Collects the brief step by step instead of dumping a form: one question at a time, each answer stored locally so a reload does not lose it.
- Recognises the service the visitor is circling around (film, PWA, WhatsApp automation, site) and routes the brief to the matching page.
- Hands the finished brief to WhatsApp with the text already written, so the visitor only presses send.
- Falls back to a plain form when scripting is blocked, so no lead is lost to an ad blocker.

## Files

- `assistant.js` — dialogue engine, language handling, brief state, WhatsApp handoff
- `push.js` — web push subscription and notification payloads

## Notes

No framework, no chat SDK, no third party widget: the whole thing is one script that the page loads, so it costs nothing per conversation and sends no visitor data to anyone but the site owner.
