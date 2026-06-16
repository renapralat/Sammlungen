# 📚 Sammlungen

Persönliche Sammlungsverwaltung als Web-App auf GitHub Pages mit Supabase-Backend.

**Live-App:** https://renapralat.github.io/Sammlungen/

---

## Was die App kann

- **Kategorien** anlegen mit eigenem Icon (Emoji per Tastatur), Farbe und frei definierbaren Feldern
- **Kategorie umbenennen** — ✏️-Button pro Kategorie-Karte
- **Einträge** als Tabelle erfassen, bearbeiten, löschen (mit Bestätigung), duplizieren (📋)
- **Textfelder** als Textarea: kompakt in Ruhestellung, beim Klick auf vollen Inhalt aufgeklappt, manuell ziehbar
- **Bilder** — bis zu 4 Fotos pro Eintrag hochladen (📷-Button), vergrößern per Klick, einzeln löschen
- **Suche** mit Wortgrenzen-Logik: `Ei` = exakt · `Ei*` = beginnt mit · `*ei` = endet mit
- **Spracheingabe** für die Suche (Deutsch, wo vom Browser unterstützt)
- **Sortierung** jeder Spalte per Klick auf den Spaltenkopf
- **CSV-Export** (↓) und **CSV-Import** (↑) — nur Textfelder, keine Bilder
- **ZIP-Export** (📦) — alle Bilder der aktuellen Kategorie als ZIP, Dateiname = Wert der ersten Spalte + Slot-Nummer (z.B. `42_1.jpg`, `42_2.jpg`)
- **Drucken** — Tabelle mit Textfeldern, lange Texte in eigener Zeile, Bilder unterhalb jedes Eintrags (ohne Beschriftung, bis zu 4 pro Eintrag)
- **Login / Registrierung** mit E-Mail + Passwort (Supabase Auth)
- **Fehler-Screen** mit "Erneut versuchen"-Button falls die Verbindung beim Start nicht klappt

---

## Technischer Aufbau

| Komponente | Detail |
|---|---|
| Hosting | GitHub Pages (Branch: `main`) |
| Backend | Supabase (Projekt: `csyqtynnvoggydofgaua`) |
| Datenbank | Tabellen `categories` + `items` |
| Bilder | Supabase Storage Bucket `sammlungen-images`, öffentliche URLs |
| Frontend | React 18 + Supabase JS v2, alles lokal (kein CDN) |
| Libraries | `react.min.js`, `react-dom.min.js`, `supabase.min.js`, `jszip.min.js` |
| Build | JSX vorab kompiliert (kein Babel zur Laufzeit) |

---

## Sicherheitshinweis Bilder

Bilder werden über **öffentliche URLs** ausgeliefert — wer die genaue URL kennt, kann das Bild ohne Login öffnen. Für Sammlungen ohne persönliche Fotos ist das akzeptabel. Falls Bilder gesichert werden sollen: Bucket auf **privat** stellen und **signierte URLs** (z.B. 1 Stunde gültig) verwenden — das ist ein separater Schritt.

---

## Entwicklungs-Branch

Änderungen werden auf `claude/github-pages-deployment-AuGo4` entwickelt und nach `main` gemergt, wo GitHub Pages automatisch deployt.

---

## Offene Punkte / Ideen

- Bilder-Sicherung auf signierte URLs umstellen (falls benötigt)
- Farbpalette pro Kategorie erweiterbar machen
- Globale Suche über alle Kategorien
