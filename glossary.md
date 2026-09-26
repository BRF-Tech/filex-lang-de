# filex — German glossary (de)

The terminology used across `translations/de.json`. One English concept → one German term,
everywhere in the product. When a term below does not fit a sentence, rephrase the sentence —
do not switch terms.

## Voice and register

- **Sie, consistently** — the standard for software that addresses a person: *Geben Sie Ihr Passwort ein*,
  *Ihr Konto*, *Bitten Sie einen Administrator …*. Never *du / dich / dir / dein*. Where a hint reads more
  naturally without addressing anyone, use the impersonal infinitive (*Datei auswählen*, *Pfad eingeben*).
- **Buttons and menu items are infinitives**, verb last: *Speichern*, *Löschen*, *Umbenennen*,
  *Link kopieren*, *In den Papierkorb verschieben*. Headings and labels are nouns: *Einstellungen*,
  *Papierkorb*, *Versionen*.
- **Status words are past participles** (no gender agreement in German predicates): *Gespeichert*,
  *Kopiert*, *Aktiviert*, *Abgebrochen*.
- **Capitalisation**: German rules (nouns capitalised), otherwise sentence case — never English Title
  Case: *Endgültig löschen* for "Delete Permanently", *Tastenkürzel* for "Keyboard Shortcuts".
- **Compounds** are written as one word (*Speicherort*, *Freigabelink*). With an acronym, a brand, a
  code token or a placeholder, join with a hyphen: *S3-Bucket*, *API-Schlüssel*, *WebDAV-Adresse*,
  *SFTP-Zugang*, *{name}-Ordner* (Duden: Durchkopplung).
- **Quotation marks**: English “ ” become German „ “ (*„{name}“ gelöscht*). Straight `"` quotes the
  English uses around literal values, menu names or input examples stay straight `"`.
- **Dashes**: the English spaced em dash " — " becomes the German spaced en dash " – ".
- *e.g.* → *z. B.*, *i.e.* → *d. h.*, *etc.* → *usw.* (with the thin, normal space German uses: `z. B.`).
- Keep UI labels short. German runs 30 %+ longer than English and builds long compounds; in buttons,
  tabs, chips, table headers, the side nav and dashboard tiles prefer the shortest **natural** wording
  (see "Length" below). Never hyphenate a word just to make it break.
- **Generic masculine** for roles (*Benutzer*, *Administrator*, *Eigentümer*, *Betreiber*), as German
  Windows, macOS and most admin software do; neutral wording (*Person*, *Konto*) where it costs nothing.

## Syntax that must survive (never translated)

| What | Rule |
|---|---|
| `{placeholder}` | kept verbatim; words around it are translated (German word order may move it) |
| a syntax token in angle brackets (`root:<storage>://<folder>`) | **translated**, like the Turkish catalogue's `root:<depo>://<klasör>` — it describes what the reader types, it is not a literal (Burak, 2026-09-23). The number of `<…>` tokens must stay the same |
| `a \| b` (admin SPA plurals) | exactly TWO branches, `one \| other` — German's CLDR categories, singular first |
| `key` / `key_one` (explorer / server plurals) | one key per CLDR category; the plain key is `other` (see “Plurals” below) |
| `{'@'}` | kept exactly (vue-i18n literal); never a bare `@` in an admin-SPA string |
| `@` in explorer strings | literal, never escaped (the explorer's `t()` is a plain replace) |
| a literal bar / `{` / `}` in an admin string | `{'\|'}` / `{'{'}` / `{'}'}` — a bare bar would start a plural form |
| `%` right before `{x}` in an admin string | `{'%'}{x}` — vue-i18n's old `%{x}` form eats the `%` |
| the 55 keys in both tables (`storages.fields.*`, `storages.fieldHelp.*`, …) | no `@`, no bar, no `{'…'}` — one value must satisfy both renderers |
| `` `code` `` spans, `<…>` tokens, env vars, CLI flags, paths, key combos | verbatim (key names in prose: *Strg* for Ctrl, *Umschalt* for Shift, *Entf* for Delete, *Eingabetaste* for Enter — but never inside a code span) |
| `tag:` search syntax | verbatim — the server parses it (`tag:rechnung` is fine; `schlagwort:` would not work) |
| `plugin:<driver>`, `name://folder`, `storage://folder`, `main://projects/acme` | verbatim |
| leading/trailing spaces, trailing `…` `:` | kept |

## Product and proper names — untouched

filex, ONLYOFFICE / OnlyOffice (as the English writes it), draw.io / diagrams.net, WebDAV, SFTP, FTP, FTPS,
NFS / NFSv3, SMB / CIFS, NAS, S3, MinIO, Hetzner, AWS, Backblaze B2, ClamAV, clamd, MCP, API,
REST, PIN, OIDC, LDAP, Active Directory, SSO, TOTP, 2FA, RBAC, JWT, SMTP, TLS, HTTPS, CIDR, DN,
ETag, MIME, SHA-256, HMAC, ed25519, PEM, PKCS#8, WebAssembly, Wasm, GitHub, Claude, rclone,
restic, Cyberduck, WinSCP, FileZilla, PuTTYgen, davfs2, sshfs, s3fs, WinFsp, macFUSE, Finder,
GNOME Files, Dolphin, PowerShell, Markdown, CSV, PDF, PWA, Windows, macOS, Linux, Keycloak,
Auth0, Authentik, Bleve, Vue, React, Go, cron.

German IT loanwords used as German nouns (capitalised, German grammar): *das Token* (pl. *Tokens*),
*der Webhook*, *der Bucket*, *der Host*, *der Port*, *der Proxy*, *das Backend*, *der Server*,
*der Client*, *das Secret* (client/webhook secret), *der Claim* (OIDC), *der Header* (HTTP),
*der Snapshot*, *das Update*, *die App*, *das Plug-in*, *der Link*, *der Upload* / *der Download*.

## Terms

| English | German | Notes |
|---|---|---|
| file | Datei | |
| folder | Ordner | directory → *Verzeichnis* |
| item (a file or folder) | Element | 1 Element / {n} Elemente |
| **storage** (a mounted backend) | **Speicher** (pl. *Speicher*) | "Add storage" → *Speicher hinzufügen*; "Storages" → *Speicher*; storage plugin → *Speicher-Plug-in* |
| location (where an item lives) | Speicherort | "Open file location" → *Speicherort öffnen*; not a synonym for a storage |
| disk space / storage used | Speicherplatz / belegter Speicher | |
| drive | Laufwerk | Windows drive letter → *Laufwerksbuchstabe*; "map network drive" → *Netzlaufwerk verbinden*. ⚠ a drive on the READER’s own machine only — never a filex storage. v0.43.0 removed that sense from the English ("Drives" in the destination picker became "Storages"), so no string here may borrow it back |
| mount / mounted | einbinden / Einbindung / eingebunden | "mount point" → *Einhängepunkt* (the Linux term) |
| connection / connect | Verbindung / verbinden | "How to connect" → *So verbinden Sie sich* |
| share (verb) | teilen | *Teilen* in menus |
| **share** / share link (filex's own) | **Freigabe** / Freigabelink | admin "Shares" → *Freigaben*; "My shares" → *Meine Freigaben*; "shared" → *geteilt* |
| shared with me | Mit mir geteilt | |
| SMB share (a network share) | SMB-Freigabe | share name → *Freigabename* (the term German Windows uses); only in SMB/CIFS context |
| link | Link | "Copy link" → *Link kopieren* |
| request files / file request | Dateien anfordern / Dateianforderung | |
| upload link, request link, drop link | Upload-Link / Anforderungslink | |
| upload (verb / noun) | hochladen / Upload | "Uploaded" → *Hochgeladen*; "Uploading…" → *Wird hochgeladen…* |
| download (verb / noun) | herunterladen / Download | |
| sync | synchronisieren / Synchronisierung; *Sync* in compounds | "Sync now" (button) → *Synchronisieren*; "Sync runs" → *Sync-Läufe*; "Active syncs" → *Aktive Syncs* |
| trash | Papierkorb | "Move to trash" → *In den Papierkorb verschieben*; "Empty trash" → *Papierkorb leeren* |
| delete / delete permanently | löschen / endgültig löschen | |
| purge | bereinigen | versions purge → *Versionen bereinigen* |
| remove | entfernen | (detaching things: a key, a tag, a plugin) |
| restore | wiederherstellen | |
| rename | umbenennen | |
| move / copy / cut / paste | verschieben / kopieren / ausschneiden / einfügen | |
| version | Version | "Version history" → *Versionsverlauf* |
| snapshot | Snapshot | |
| tag (noun / verb) | *das* Tag (pl. *Tags*, Duden: EDV) / prefer *Tags zuweisen* over *taggen* | "Tagged files" → *Dateien mit Tags*; ⚠ never use *Tag* for "label" |
| label (a name you give a token/key/export) | Bezeichnung | UI label/caption → *Beschriftung* |
| star / starred / unstar | zu Favoriten hinzufügen / Favoriten / aus Favoriten entfernen | column "Star" → *Favorit*; ⚠ not *markieren*, which in German UIs means "select" |
| select / selected / selection | auswählen / ausgewählt / Auswahl | |
| recent | zuletzt verwendet | nav "Recent" → *Zuletzt verwendet*; "Recent activity" → *Letzte Aktivitäten* |
| home | Start | |
| **app** (WebAssembly app) | **App** (pl. *Apps*) | "Apps" → *Apps*; "desktop app" → *Desktop-App* |
| **plugin** (storage plugin) | **Plug-in** (pl. *Plug-ins*) | "Storage plugins" → *Speicher-Plug-ins* |
| application (filex itself, software in general) | Anwendung | |
| driver | Treiber | |
| manifest | Manifest | |
| signature / sign (cryptographic: app, manifest, key) | Signatur / signieren | "signed app" → *signierte App* |
| sign / signature (a person signing a PDF) | unterschreiben / Unterschrift | |
| signer | Unterzeichner | |
| requester | anfordernde Person | |
| filled by | ausgefüllt von | |
| initials | Initialen | |
| box (a field placed on a PDF) | Feld | |
| field | Feld | |
| permission | Berechtigung | |
| grant (noun) / grant (verb) | Berechtigung / erteilen | "Grant revoked" → *Berechtigung widerrufen* |
| access | Zugriff | "People with access" → *Personen mit Zugriff* |
| revoke | widerrufen | |
| owner | Eigentümer | |
| administrator / admin | Administrator / Admin | "Admin panel" → *Adminbereich*; "Admins only" → *Nur Admins* |
| operator | Betreiber | |
| instance | Instanz | |
| tenant / multi-tenant | Mandant / mandantenfähig | |
| user / account | Benutzer / Konto | |
| role: Administrator / User / Viewer | Administrator / Benutzer / Betrachter | |
| permission level: Viewer / Editor / Owner | Betrachter / Bearbeiter / Eigentümer | |
| viewer / preview (the component that shows a file) | Vorschau | "Open in viewer" → *In der Vorschau öffnen* |
| sign in / sign out / sign-in | anmelden / abmelden / Anmeldung | "Log out" → *Abmelden* |
| username / password | Benutzername / Passwort | not *Kennwort* |
| email (v0.43.0 respelt English's "e-mail") | E-Mail | *E-Mail-Adresse*; the German spelling does not change |
| two-factor authentication / 2FA | Zwei-Faktor-Authentifizierung / 2FA | "second factor" → *zweiter Faktor* |
| authentication / auth provider | Authentifizierung / Anmeldeanbieter | page title "Authentication providers" → *Authentifizierungsanbieter* |
| recovery code / recovery key | Wiederherstellungscode / Wiederherstellungsschlüssel | |
| key escrow / escrow key | Schlüsselhinterlegung / Hinterlegungsschlüssel | |
| encrypted / encrypt / decrypt | verschlüsselt / verschlüsseln / entschlüsseln | "end-to-end encrypted" → *Ende-zu-Ende-verschlüsselt* |
| lock / locked / unlock | sperren / gesperrt / entsperren | file lock → *Sperre* |
| permission (what an API key may do) | die Berechtigung (pl. *Berechtigungen*) | ⚠ v0.43.0 retired English's "scope" for this: one term on every screen — the column, the field, the hint, the refusal from the server |
| API key (the ONE term since v0.43.0 — English retired "API token") | **der** API-Schlüssel (pl. *API-Schlüssel*) | ⚠ masculine, so the pronouns are *er / ihn / den* — *Token* was neuter and every sentence that referred back to it had to change |
| token (somebody else's — a Bearer token, an OIDC *token endpoint*, a plugin's remote token) | Token (das, pl. Tokens) | the only surviving use; never for a filex API key |
| access key / secret key | Zugriffsschlüssel / geheimer Schlüssel | |
| secret (a webhook/client secret) | Secret | *Client-Secret*, *Webhook-Secret* |
| scope (OIDC only) | Scope (pl. *Scopes*) | ⚠ ONLY the OIDC scope names an identity provider defines (`authProviders.fields.scopes` = *Zusätzliche Scopes*). What an API key may do is a **Berechtigung** since v0.43.0, and `search.scope` ("Look in") is *Suchen in* |
| claim (OIDC) | Claim | "Role claim" → *Rollen-Claim* |
| header (HTTP) | Header | |
| endpoint | Endpunkt | |
| bucket | Bucket | |
| export (NFS) | Export | |
| path / root | Pfad / Stammordner | |
| host / port | Host / Port | |
| quota | Kontingent | "storage quota" → *Speicherkontingent* |
| retention | Aufbewahrung | "retention period" → *Aufbewahrungsdauer* |
| job / queue / queued | Auftrag / Warteschlange / in der Warteschlange | status chip "Queued" → *Wartend* |
| operation | Vorgang | operations tray → *Vorgangsleiste* |
| audit log | Audit-Protokoll | |
| log | Protokoll | |
| replica / replication | Replikat / Replikation | admin "Replica" → *Replikation* |
| webhook | Webhook | |
| search index | Suchindex | |
| storage scan / scan exclusions | Scan / vom Scan ausgeschlossene Pfade | the walk over a storage (*Scanintervall*); a virus scan is *Virenscan* |
| catalogue (what the scan records) | katalogisieren | "not catalogued" → *nicht katalogisiert* |
| catalog (noun, v0.44.0) | Katalog | *Katalogverhalten*, *Katalog: {pct} %* |
| lazy catalog (a sync mode) | Lazy-Katalog | a chip beside *Echtzeit* / *Intervall* / *Bei Bedarf*, so it stays short; its behaviors *Geöffnetes zuerst, Rest im Hintergrund* / *Nur beim Öffnen*; the background pass → *Hintergrunddurchlauf* |
| watch / watched (a folder, for changes made outside filex) | überwachen / überwacht | |
| usage (the storage-used figure) | belegter Speicher | as *{used} belegt*; *Nutzung & Kosten* is a different page |
| archive / extract | Archiv / entpacken | as *Archiv entpackt* (audit) and *entpackt* (unzip); "Extract here" → *Hier entpacken*; "solid archive" → *solides Archiv* |
| package manager | Paketmanager | Homebrew, winget and Snap stay as written |
| attempt / attempt timeout / give up after (a storage's network settings, v0.45.0) | Versuch / Zeitlimit pro Versuch / Aufgeben nach | as *Verbindungszeitlimit*; "Attempts per request" → *Versuche pro Anfrage*; retrying → *Wiederholungen*; an S3 "store" is *der Dienst*, as in the other S3 hints |
| drag-out download (audit, v0.45.0) | Download durch Herausziehen | "downloaded by dragging it out" → *durch Herausziehen heruntergeladen* |
| what an update policy does here (badge, v0.45.0) | *Kündigt nur an* / *Installiert Patches* / *Installiert Nebenversionen* / *Prüfung aus* | third person, the install is the subject; the policy's own name stays an infinitive (*nur ankündigen*) |
| storage order (navigation panel and admin Storages, v0.46.0) | *Nach oben* / *Nach unten* / *Nach Name sortieren* / *Standardreihenfolge verwenden* | *Auf Standardreihenfolge zurücksetzen* on the admin page |
| pattern (glob) | Muster (Glob-Muster) | *Pfadmuster*; the pattern itself (`.git`, `*.tmp`, `downloads/incomplete/**`) stays as written |
| emptying the trash / server log | Leeren des Papierkorbs / Serverprotokoll | "Emptying the trash…" → *Papierkorb wird geleert…*; a trash purge is *endgültig löschen*, as in *Endgültig löschen* (`trash.purge`) |
| details panel (inspector) | Detailbereich | |
| command palette | Befehlspalette | |
| keyboard shortcut | Tastenkürzel | |
| tour | Tour | |
| explorer | Explorer | |
| computer | Computer | "Keep on this computer" → *Auf diesem Computer behalten* |
| settings / preferences | Einstellungen | |
| appearance / theme / palette | Darstellung / Design / Farbpalette | Light / Dark / Auto → *Hell / Dunkel / Automatisch* |
| branding | Branding | |
| dashboard | Übersicht | |
| usage & cost | Nutzung & Kosten | |
| update (software) / upgrade | Update / aktualisieren | "Updates" → *Updates* |
| default | Standard | "Reset to default" → *Auf Standard zurücksetzen* |
| custom / customize | eigene(r) / benutzerdefiniert / anpassen | prefer *eigen* where it reads naturally |
| enable / disable / enabled / disabled | aktivieren / deaktivieren / aktiviert / deaktiviert | chips "On" / "Off" → *An* / *Aus* |
| healthy / reachable / unreachable | Intakt / erreichbar / nicht erreichbar | |
| pending / running / failed / done | ausstehend / läuft / fehlgeschlagen / erledigt | "Done" button → *Fertig* |
| retry / try again | wiederholen / erneut versuchen | |
| dismiss | ausblenden | |
| undo | rückgängig machen | button → *Rückgängig* |
| refresh / reload | aktualisieren / neu laden | |
| reset | zurücksetzen | |
| enter (type into a field) | eingeben | *Geben Sie eine Zahl ein* |
| click / right-click / tap / tick | klicken / Rechtsklick / tippen / ankreuzen | |
| drag / drop | ziehen / ablegen | "Drop files here" → *Dateien hier ablegen* |
| required / optional | erforderlich / optional | |
| read-only | schreibgeschützt | a badge beside a name → *Nur lesen* (measured, see Length) |
| language pack | Sprachpaket | |
| probe (conformance) | Prüfung | "Conformance report" → *Konformitätsbericht* |
| wake-up (scheduled app) | Aufwecken | |
| payload / severity | Payload / Schweregrad | |
| slot (a free concurrency slot) | Slot | |
| backend | Backend | |

## Plurals — German's CLDR categories

Seit filex v0.43.0 wählt jede Tabelle die Form nach der **CLDR-Kategorie** der Zahl in der Sprache
der lesenden Person (`Intl.PluralRules` im Browser, `x/text` auf dem Server). Deutsch hat **zwei**:
`one` (genau 1) und `other` (alles andere, 0 eingeschlossen).

| Wo | Wie die Formen geschrieben werden |
|---|---|
| Explorer- / Server-Schlüssel | `key_one` neben dem einfachen Schlüssel, der die Form `other` ist (ein `key_other` gibt es nicht) |
| Admin-Schlüssel (vue-i18n) | **zwei** Formen in EINER Zeichenkette, getrennt durch einen Balken: `one | other`. ⚠ Niemals drei — bei drei Zweigen wechselt der Renderer zur klassischen Regel und schickt 0 in den ersten |

- **Jede Form behält den Zählerplatzhalter** — `"{n} Element"`, nie `"1 Element"`. Eine
  ausgeschriebene Ziffer ist genau der Fehler, den v0.43.0 im eigenen Englisch und Türkisch
  behoben hat; die zehn `server.*`-`_one`-Formen, deren Englisch noch `1` schreibt, tragen hier
  trotzdem `{count}` (der Server füllt ihn immer, `srvtext.Plural` setzt `count` zuerst).
- **Eine Form wird nur dort geschrieben, wo sich die Wörter ändern.** `"{n}%"`, `"{n} / {m}"`,
  `"Seite {n} von {m}"` lesen sich für jede Zahl gleich und haben absichtlich kein `_one`; der
  Validator listet sie unter `--plurals`, und das ist so gewollt. Umgekehrt braucht
  `sidenav.tags.more` eines (*das* Tag), obwohl das englische Katalog keines hat — erlaubt.
- **Niemals `_zero`, `_two`, `_few` oder `_many` schreiben.** Diese Kategorien hat Deutsch nicht;
  der Validator meldet den Schlüssel als `UNUSED`, und filex zeigt ihn nie an.

## Typography

- **Percent**: number, no-break space, `%` (DIN 5008): `{percent} %`, `{n} %` — the space is U+00A0 so
  the two never wrap apart. (In an admin-panel string `%` may follow a placeholder freely; only `%{` is
  the vue-i18n trap.)
- **Ranges**: en dash without spaces — *1–10 MB*, *1–40 Zeichen* (the English hyphen is kept inside
  code-like input rules such as `a-z`).
- **Numbers and dates** come from the browser's locale (*134.362*, *2,48 TB*, *22. Sept. 2026*), not
  from the pack.

## Length (German runs long — measured places)

German came out 28.7 % longer than English overall. The browser check (see the README) measured every
element that clips or spills its text at 1280 px and 390 px, against an English baseline, and these
were shortened:

| Where | English | First German | Measured | Final German |
|---|---|---|---|---|
| Dashboard tile | Total size | Gesamtgröße | *GESAMTGRÖSSE* spilled 30 px out of a 64 px tile | *Größe gesamt* (two short words wrap like the English) |
| Dashboard tile | Queue depth | Warteschlange | *WARTESCHLANGE* spilled 40 px; *Wartende Aufträge* still 2 px | *Offene Aufträge* |
| Storage card chip | Live watch | Live-Überwachung | pushed the storage name to "lo…" | *Echtzeit* |
| Storage card chip | Periodic poll | Regelmäßige Abfrage | wrapped to two lines | *Intervall* (and "poll mode" → *Intervallmodus*) |
| Storage card button | Sync now | Jetzt synchronisieren | wrapped to two lines | *Synchronisieren* |
| Explorer side nav + Home cards, badge | Read-only | Schreibgeschützt | cut the storage name to "of…" | *Nur lesen* (badges only; forms and sentences keep *schreibgeschützt*) |
| Sign-in subtitle | Sign in with your account on this server | Melden Sie sich … an | a lone "an" on the second line at 390 px | *Mit Ihrem Konto auf diesem Server anmelden* |

- **Admin side nav (240 px)**: every item fits — *Übersicht*, *Datei-Verlauf*, *Sync-Läufe*,
  *Anmeldeanbieter*, *Benachrichtigungen*, *Nutzung & Kosten*…
- **Dashboard stat tiles** (uppercase, 64 px, no hyphenation): one word of at most ~8 capitals, or two
  short words.
- **Table headers, chips, buttons**: prefer the base noun over a compound where the context makes it clear.

## Decisions that were hard (and why)

- **storage → *Speicher*** (pl. *Speicher*). Short (8 letters, it fits the side nav and the tiles), it is what
  Nextcloud and ownCloud call a mounted backend (*Externer Speicher*), and its plural is identical, which keeps
  labels short. The cost: *Speicher* also means RAM, so memory is always *Arbeitsspeicher*, and a file's place
  is *Speicherort* (location), never a synonym for a storage. A cost line billed per GB is *Speicherplatz*.
- **app → *App*, plugin → *Plug-in*, application → *Anwendung*.** filex has two kinds of extension. *App*
  (Duden, and the product's own word) for the WebAssembly apps; *Plug-in* (Duden spelling) for storage
  drivers. *Erweiterung* was rejected for plugins because *Speichererweiterung* reads as "more disk space".
  *Anwendung* is kept for filex itself / software in general, so "this app" (filex) and "an app" (a plugin)
  stay apart.
- **share → *Freigabe* (noun), *teilen* (verb).** The German-UI convention (Nextcloud: *Teilen*, *Freigaben*).
  An SMB network share is also a *Freigabe* in German Windows, so it is always qualified: *SMB-Freigabe*,
  *Freigabename*.
- **star → *Favoriten***, not *markieren*: in German UIs *markieren* means "select".
- **tag → *das Tag*** (Duden's gender for the IT sense), never *Schlagwort* — the `tag:` search syntax stays
  English, and *Tag* beside it reads naturally.
- **label → *Bezeichnung***, so it never collides with *Tag*.
- **signing**: cryptographic (apps, manifests) → *Signatur / signieren*; a person signing a PDF →
  *Unterschrift / unterschreiben / Unterzeichner*.
- **tenant → *Mandant*** (the established German term), multi-tenant → *mandantenfähig*.
- **token → *das Token*** (pl. *Tokens*); **secret → *Secret*** (as German admin UIs keep it: *Client-Secret*);
  **scope → *Scope*** only for OIDC scope names (openid, email); what an API key may do is a
  *Berechtigung* since v0.43.0, and `search.scope` ("Look in") is *Suchen in*.
- **Preferences tab → *Allgemein***: the dialog is already titled *Einstellungen*, and *Einstellungen /
  Einstellungen* would repeat itself.
- **Generic masculine** for roles (*Benutzer*, *Administrator*, *Eigentümer*), as German Windows and most admin
  software do; neutral wording (*Person*, *Wer … hochlädt*) where it costs nothing.
- **Client software instructions** use the German builds' menu names where known (Windows: *Dieser PC*,
  *Netzlaufwerk verbinden*, *Eingabeaufforderung*; macOS: *Gehe zu → Mit Server verbinden …*, *Orte*;
  FileZilla: *Datei → Servermanager → Neuer Server*; WinSCP: *Neues Verbindungsziel*). An option a German build
  may not translate stays English in quotes ("Use virtual host style"). **A reviewer should verify these
  against current German builds.**
