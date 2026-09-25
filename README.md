# filex — German (de) language pack

The whole [filex](https://github.com/BRF-Tech/filex) interface in German — the file explorer, the admin
panel, the settings dialog and the public pages a share link opens — as an installable **language pack**:
one manifest, `filex-app.json`, no code and no build.

> **AI-translated, awaiting review by a native speaker — corrections welcome.**
> Formal German (*Sie*), a plain product voice. Terminology is fixed in [`glossary.md`](glossary.md);
> please keep to it (or change it there first) when you correct a string.

| | |
|---|---|
| Version | 0.1.1, for filex 0.44.0 |
| Written against | the filex **v0.44.0** catalogue (`catalogue/`, 3,728 strings — 1,846 admin, 1,591 explorer, 233 the server's, 58 drawn by both) |
| Coverage | 100 % — 3,728 of 3,728 strings, plus 1 extra plural form |
| Validators | platform: 0 errors · 0 warnings — German check: 0 errors · 0 warnings ([`validate-output.txt`](validate-output.txt)) |

## Install

On a filex server (v0.43.0 or newer): **Plugins → Apps → Install an app**, then either

- **GitHub** — `BRF-Tech/filex-lang-de` (optionally a tag). filex reads `filex-app.json` from
  the repository root; no release is needed; or
- **Files** — upload `filex-app.json` and leave the module empty: a language pack has none.

Then choose **Deutsch** in **Settings → Preferences → Language** (or in the language row of a public share
page). A string the pack lacks after a filex upgrade shows in English, never as a raw key.

## What is in here

| Path | What it is |
|---|---|
| `translations/de.json` | **the file you edit** — one flat object `{ "<key>": "<text>" }`, exactly `ui_locales["de"]` |
| `filex-app.json` | the pack filex installs — written from `translations/` by `node scripts/pack.mjs build` |
| `glossary.md` | terminology, voice, the syntax each renderer needs, typography, the measured length fixes and the hard decisions |
| `catalogue/` | the authoritative English catalogue with per-key context (which renderer, the Turkish reference, the source files) |
| `scripts/pack.mjs` | the template's workflow: `next` · `build` · `sync` |
| `scripts/validate.mjs` | the platform validator, copied verbatim from filex |
| `scripts/validate-de.mjs` | this pack's own, stricter check (see below) |
| `validate-output.txt` | the last run of both validators, with the length report |

This repository follows [filex-lang-template](https://github.com/BRF-Tech/filex-lang-template); its workflow
(`pack.mjs`, `validate.mjs`, the CI check) is unchanged.

## Validate

Node 18+. `npm install` once adds vue-i18n's own message parser, which both validators then use.

```sh
node scripts/pack.mjs build --check                  # filex-app.json matches translations/
node scripts/validate.mjs filex-app.json --complete  # the platform's rules; a missing key is an error
node scripts/validate-de.mjs --lengths               # the German check, plus the length report
```

`validate-de.mjs` adds to the platform validator what a German translation needs on top: a value left in
English is an error unless it is a name, a unit or a word German shares; the number of plural forms must equal
the English; code spans, `<…>` tokens, leading/trailing whitespace and a trailing `…` / `:` must survive;
any *du* form is an error; a glossary lint (*Passwort*, *E-Mail*, *Plug-in*, „…“ quotes, spaced en dashes,
*z. B.*); a consistency report (one short English label translated two ways) and a length report.

## How it was made, and checked

1. Glossary first, then the catalogue translated in parallel chunks that all shared it, merged, and every
   string read side by side with its English.
2. Both validators to 0 errors and 0 warnings.
3. A browser check: the filex web build served inside Playwright with a mocked API, the pack delivered the way
   the server delivers it (`/api/public/branding` lists the language, `/api/public/ui-locales/de` returns the
   strings), German selected, and the sign-in page, dashboard (1280 and 390 px), storages, new storage, users,
   settings, sync runs, audit log, plugins, connections, the explorer (1280 and 390 px) and Home measured for
   every element that clips or spills its text — against an English baseline of the same screens. The seven
   fixes this produced are listed in `glossary.md` → *Length*.

The one clip left: on Home, a read-only storage's card caption *81 GB belegt · Nur lesen* is 4 px wider than
its fixed 124 px slot and ends in an ellipsis (the English *81 GB used · Read-only* just fits).

## Corrections

Open an issue or a pull request against `translations/de.json`; run `node scripts/pack.mjs build` so
`filex-app.json` follows, and keep both validators at zero. Menu names quoted from other programs (Windows,
macOS, FileZilla, WinSCP, Cyberduck) are the ones their German builds use as far as we know — a reviewer with
those builds at hand is especially welcome.

## License

MIT — see [`LICENSE`](LICENSE).
