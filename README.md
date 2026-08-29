# The Neural Academy — Landingpage

Öffentliche Marketing-Website für The Neural Academy (KI-natives Mathe-Nachhilfe-
Institut). Eigenständiges Projekt, technisch getrennt vom Tutoring-Tool in
`../tutoring_second_brain/`.

Statische Single-Page-Site, kein Build-Tooling: `index.html` enthält Markup, Styles
und das kleine Theme-Toggle-Script inline. Kann direkt auf jedem statischen Host
(Netlify, Vercel, GitHub Pages, Railway Static) deployt werden.

## Design-System

Folgt `../frontend-design.md` (Skill `institut-precision-ui`) 1:1: Design-Tokens,
Typografie (Outfit für Headlines, Inter für Fließtext), Formensprache, Copy-Voice und
Pre-Delivery-Checkliste. Bei Änderungen an dieser Seite zuerst dort nachlesen, nicht
neu erfinden.

## Offene TODOs vor dem Launch

1. **Domain**: noch nicht registriert. Sobald entschieden, `<title>`, Meta-Tags und
   die Railway-URLs unten durch die echte Domain ersetzen.
2. **Kontakt** (`#kontakt-todo`, Footer): noch keine echte Kontakt-E-Mail hinterlegt.

Erledigt: Login-Button (Nav + Footer) zeigt auf
`https://web-production-b1ad9.up.railway.app/login`. Der Demo-Button zeigt auf
`https://web-production-b1ad9.up.railway.app/demo` — ein öffentlicher, passwortloser
Einstieg in einen dedizierten `is_demo`-Schüler-Account (echtes Testmaterial zu
Ableitungsregeln + bedingter Wahrscheinlichkeit, echter sokratischer Chat).
Upload/Verarbeiten/Pinnwand-Erstellen sind für diesen Account serverseitig gesperrt,
der Chat ist rate-limitiert (15 Nachrichten/Session, 200/Tag). Details und Code dazu
in `../tutoring_second_brain/app.py` (`_reject_if_demo`, `/demo`-Route) und
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

Hero → Methode (3-Schritt-Ablauf + sokratisches Grundprinzip als Callout) → Für wen
(Schüler:innen / Eltern) → Live-Demo-CTA → Footer.

Noch nicht abgestimmt mit Jonas, da bislang nur "grober Überblick" spezifiziert war.
Kandidaten für weitere Abschnitte, falls gewünscht: Preise/Pilotphase-Details,
Über-uns/Tutor-Vorstellung, FAQ.
