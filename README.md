# Gillich Automobile — Website

Statische Single-Page-Site für Gillich Automobile (Olfen, Münsterland).
Light-Theme mit cinematic Dark-Hero, Editorial-Leistungen, Inzahlungnahme-Formular.

## Formspree einrichten (Pflicht, sonst gehen Formulare ins Leere)

Sowohl das **Kontakt-Formular** als auch das **Inzahlungnahme-Formular** schicken über Formspree.
Beide teilen sich **eine einzige Form-ID** — der E-Mail-Betreff macht den Unterschied
(„Kontakt-Anfrage…" vs. „Inzahlungnahme-Anfrage…").

### Schritt-für-Schritt

1. **Account anlegen** auf [https://formspree.io](https://formspree.io) mit `gillich@gillich-automobile.de`.

2. **Form erstellen**:
   - „+ New Form" klicken
   - Name: `Gillich Website`
   - Save

3. **Form-ID kopieren** — sie steht in der Endpoint-URL und sieht so aus:
   `https://formspree.io/f/`**`xkgjbrwn`** (die 8 Zeichen nach `/f/`)

4. **In der Website eintragen**:
   - Datei `index.html` öffnen
   - Im `<script>`-Block (Zeile ~1652) die Konstante setzen:
     ```javascript
     const FORMSPREE_ID = 'xkgjbrwn'; // ← deine echte ID
     ```
   - Speichern, hochladen, fertig.

### Plan-Auswahl

| Plan | Preis | Was geht |
|---|---|---|
| **Free** | 0 € | 50 Submissions/Monat. Reicht für Kontakt-Form. Inzahlungnahme funktioniert **ohne** Datei-Anhang (Fahrzeugschein-Dateinamen erscheinen nur als Text in der Mail). |
| **Bronze** | ca. 12 €/Monat | 1.000 Submissions, **Datei-Anhänge inklusive**. Empfehlung, wenn ihr Fahrzeugschein-Uploads direkt in der Mail bekommen wollt. |

Free reicht für den Start — du kannst jederzeit upgraden, wenn das Volumen steigt.

## Lokale Vorschau

Einfach `index.html` in einem Browser öffnen — keine Build-Pipeline, keine Dependencies.

## Auf Hostinger hochladen

Hostinger hPanel → Dateimanager → `public_html/` → `index.html` ersetzen.
Wenn sich Bilder oder Fonts geändert haben, auch `hero.webp`, `nico.jpg`,
`showroom.jpg` und den `fonts/`-Ordner mit hochladen.

## Tech

- Statisches HTML, inline CSS, Vanilla JS
- Inter Font selbst-gehostet (`fonts/inter-latin.woff2` / `…-italic.woff2`)
- OpenStreetMap lazy-load (Karte lädt erst nach Click — DSGVO-konform)
- Formspree für Form-Submissions
- Sticky Bottom-Bar Mobile für Anrufen / WhatsApp
