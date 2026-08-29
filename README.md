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

1. **Calendly-Link** (`#calendly-todo`, zwei Stellen: CTA-Panel im Hero + Schluss-CTA
   vor dem Footer): noch kein echter Link hinterlegt. Beide Buttons ("Jetzt Termin
   für die erste kostenlose Stunde buchen") verlinken aktuell auf nichts.
2. **Fächer-Benachrichtigung-Link** (`#benachrichtigen-todo`, Für-wen-Section): noch
   kein Ziel — es existiert noch kein Mechanismus, über den sich Interessierte für
   weitere Fächer benachrichtigen lassen können.
3. **Kontakt**: es gibt aktuell keinen Kontakt-Link mehr auf der Seite (Footer wurde
   auf Startseite/Impressum/Datenschutz/Login reduziert). Sobald eine echte
   Kontakt-E-Mail existiert, prüfen ob sie irgendwo rein soll.
4. **Impressum / Datenschutz** (`impressum.html`, `datenschutz.html`): nur Platzhalter
   (`[Platzhalter: ...]`), rechtlich noch nicht verwendbar. Echte Angaben (Name,
   Anschrift, Verantwortlicher, Datenverarbeitung) müssen vor dem Launch rein.
5. **Gründer-Foto** (`index.html#team`): SVG-Platzhalter, echtes Foto fehlt noch. Der
   Bio-Text ist bereits echt (von Jonas diktiert).

Erledigt: Login-Button (Nav + Footer) zeigt auf
`https://web-production-b1ad9.up.railway.app/login`. Der Demo-Button im Hero zeigt
auf `https://web-production-b1ad9.up.railway.app/demo` — ein öffentlicher,
passwortloser Einstieg in einen dedizierten `is_demo`-Schüler-Account (echtes
Testmaterial zu Ableitungsregeln + bedingter Wahrscheinlichkeit, echter sokratischer
Chat). Upload/Verarbeiten/Pinnwand-Erstellen sind für diesen Account serverseitig
gesperrt, der Chat ist rate-limitiert (15 Nachrichten/Session, 200/Tag). Details und
Code dazu in `../tutoring_second_brain/app.py` (`_reject_if_demo`, `/demo`-Route) und
`../tutoring_second_brain/supabase/migration_demo.sql`.

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
sokratisches Grundprinzip) → Gründer (Jonas, echter Bio-Text) → Für wen
(Fach/Jahrgangsstufe als Fließtext) → Schluss-CTA (nochmal der Calendly-Button) →
Footer.

Kopf- und Fußzeile bewusst auf das Minimum reduziert: nur noch Impressum,
Datenschutz, Login sowie ein Link zur Startseite (Logo bzw. "Startseite" im Footer).
Kein Demo-Button mehr im Nav — der Demo-Einstieg lebt jetzt ausschließlich als
Primary-Button im Hero. Keine Eyebrow-Labels mehr über den Section-Headlines (bewusst
entfernt, gilt für alle Sections gleich).

"Second Brain" wurde als Produktname überall (Landingpage + Tool-Frontend in
`../tutoring_second_brain/templates/_student_base.html`) durch "Intelligente
Bibliothek" ersetzt.
