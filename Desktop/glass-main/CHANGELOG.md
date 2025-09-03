## Changelog

### Unreleased

- Security: webSecurity activé; validation `open-external` (http/https/mailto)
- Secrets: Portkey API via env; Firebase config via env (Electron & Next)
- Functions: engines Node 20
- IPC/UI: cleanup listeners `AskView`; gating capture écran/audio + loopback Windows
- LLM: retry/backoff (OpenAI/Anthropic)
- Windows: `electron-builder.yml` cscLink via env; NSIS installer hooks; userData path normalisé
- Frontend: optimisations React (memo/callbacks) et cache TTL API (10s)
- Deps: `dotenv@^16.4.5`


