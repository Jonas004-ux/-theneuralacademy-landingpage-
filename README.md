# The Neural Academy — Landingpage

Öffentliche Marketing-Website für The Neural Academy (KI-natives Mathe-Nachhilfe-
Institut). Eigenständiges Projekt, technisch getrennt vom Tutoring-Tool in
`../tutoring_second_brain/`.

Statische Mehrseiten-Site, kein Build-Tooling: `index.html`, `impressum.html`,
`datenschutz.html` teilen sich `assets/theme.css` (Design-Tokens + Komponenten) und
je ein inline Theme-Toggle-Script.

**Live** auf GitHub Pages: https://www.theneuralacademy.de, Repo
[Jonas004-ux/-theneuralacademy-landingpage-](https://github.com/Jonas004-ux/-theneuralacademy-landingpage-)
(eigener Remote, siehe `git remote -v` — nicht dasselbe Repo wie
`tutoring_second_brain`). Pages baut automatisch aus `main`, ein `git push` auf
diesen Remote geht direkt live. Custom Domain per `CNAME`-Datei + DNS (4 A-Records
auf die GitHub-Pages-IPs für die nackte Domain, ein CNAME-Record `www` →
`jonas004-ux.github.io`).

## Design-System

Folgt `../frontend-design.md` (Skill `institut-precision-ui`) 1:1: Design-Tokens,
Typografie (Outfit für Headlines, Inter für Fließtext), Formensprache, Copy-Voice und
Pre-Delivery-Checkliste. Bei Änderungen an dieser Seite zuerst dort nachlesen, nicht
neu erfinden.

## Offene TODOs vor dem Launch

1. **Migration ausstehend**: `../tutoring_second_brain/supabase/migration_interest_signups.sql`
   muss einmal im Supabase-SQL-Editor laufen (legt `subject_interest_signups` an),
   sonst wirft das Fächer-Interesse-Formular unten auf der Seite einen 500er, sobald
   jemand absendet.
2. **Kontakt**: es gibt aktuell keinen Kontakt-Link mehr auf der Seite (Footer wurde
   auf Startseite/Impressum/Datenschutz/Login reduziert). Sobald eine echte
   Kontakt-E-Mail existiert, prüfen ob sie irgendwo rein soll.
3. **Impressum / Datenschutz** (`impressum.html`, `datenschutz.html`): nur Platzhalter
   (`[Platzhalter: ...]`), rechtlich noch nicht verwendbar. Echte Angaben (Name,
   Anschrift, Verantwortlicher, Datenverarbeitung) müssen vor dem Launch rein.

Erledigt: Login- und Demo-Button (Nav) zeigen auf
`https://web-production-b1ad9.up.railway.app/login` bzw. `/demo` — Demo ist ein
öffentlicher, passwortloser Einstieg in einen dedizierten `is_demo`-Schüler-Account
(echtes Testmaterial zu Ableitungsregeln + bedingter Wahrscheinlichkeit, echter
sokratischer Chat), serverseitig schreibgeschützt und rate-limitiert (15
Nachrichten/Session, 200/Tag). Details in `../tutoring_second_brain/app.py`
(`_reject_if_demo`, `/demo`-Route) und
`../tutoring_second_brain/supabase/migration_demo.sql`.

Beide Calendly-Buttons ("Jetzt Termin für die erste kostenlose Stunde buchen") zeigen
auf `https://calendly.com/jonas-hunglinger/nachhilfe-probestunde`.

Gründer-Foto ist ein echtes Foto (`assets/jonas.jpg`), kein Platzhalter mehr.

Das Fächer-Interesse-Formular (Für-wen-Section) postet an
`https://web-production-b1ad9.up.railway.app/interest-signup` (neue Route in
`../tutoring_second_brain/app.py`, CORS eng auf die Landingpage-Origins beschränkt,
Tages-Limit 100 Einreichungen). Speichert E-Mail + angekreuzte Fächer (Physik,
Latein, Englisch, Deutsch, Alle Nebenfächer) in der Supabase-Tabelle
`subject_interest_signups` — sichtbar für Tutor-Accounts über den normalen
Supabase-Table-Editor oder eine künftige Tutor-Ansicht, dafür existiert aktuell noch
keine UI im Tool selbst.

## Logo

`assets/logo-icon.svg`: geometrisches N-Monogramm (zwei weiße Balken, grüne
Diagonale) auf abgerundetem Ink-Badge. In Nav, Footer und als Favicon eingebunden.
Entwurf und verworfene Alternativen (Wissensnetz-Richtung, Tablet-Erstentwurf) liegen
als Design-Components-Quellen unter `design/logo/` (`Main.dc.html`,
`DirectionB.dc.html`, `canvas.json`) und im veröffentlichten Canvas
[The Neural Academy Logomark](https://claude.ai/code/artifact/6e2cbdf6-34d8-4edc-b54c-72cbfc0f9cdd).
Aktuell nur als SVG vorhanden, noch keine PNG-Exporte (z. B. für Social-Share-Bilder
oder ältere Favicon-Fallbacks) — bei Bedarf ergänzen.

## Seitenstruktur (aktueller Stand)

`index.html`: Hero (Headline + Lede + Demo-Button + großes CTA-Panel mit
Calendly-Button) → Ansatz ("Unsere intelligente Bibliothek", 3-Schritt-Ablauf,
sokratisches Grundprinzip) → Gründer (Jonas, echtes Foto + echter Bio-Text) → Für wen
(Fach/Jahrgangsstufe als Fließtext + Fächer-Interesse-Formular) → Schluss-CTA
(nochmal der Calendly-Button) → Footer.

Kopf- und Fußzeile auf Impressum/Datenschutz/Login/Demo (Nav) bzw.
Startseite/Impressum/Datenschutz/Login (Footer) reduziert. Keine In-Page-Anchor-Links
und keine Eyebrow-Labels mehr über den Section-Headlines (bewusst entfernt, gilt für
alle Sections gleich).

"Second Brain" wurde als Produktname überall (Landingpage + Tool-Frontend in
`../tutoring_second_brain/templates/_student_base.html`) durch "Intelligente
Bibliothek" ersetzt.
