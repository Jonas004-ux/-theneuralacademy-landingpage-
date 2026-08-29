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

Im Code mit `<!-- TODO: ... -->`-Kommentaren markiert:

1. **Domain**: noch nicht registriert. Sobald entschieden, `<title>`, Meta-Tags und
   alle internen Verweise entsprechend anpassen.
2. **Login-Button** (`#login-todo`, Nav + Footer): muss auf die echte Login-Route der
   deployten `tutoring_second_brain`-App zeigen. Aktuell existiert noch keine
   öffentliche Railway-/Domain-URL für das Tool, dieser Wert war zum Zeitpunkt des
   Bauens dieser Seite nicht bekannt.
3. **Demo-Zugang** (`#demo-todo`, Abschnitt „Live-Demo"): verlinkt aktuell auf nichts.
   Die Demo selbst existiert noch nicht. Das ist eine Architekturentscheidung im
   `tutoring_second_brain`-Repo (`auth.py`/`app.py`), nicht Teil dieses Projekts:
   entweder ein dedizierter Demo-Schüler-Account mit serverseitig gesperrten
   Upload-/Process-Routen, oder ein separater schreibgeschützter Snapshot. Muss mit
   Jonas geklärt werden, bevor daran gebaut wird, insbesondere weil das nicht-
   verhandelbare sokratische Chat-Verhalten dabei erhalten bleiben muss.
4. **Kontakt** (`#kontakt-todo`, Footer): noch keine echte Kontakt-E-Mail hinterlegt.

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
