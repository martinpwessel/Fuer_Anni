# Die Schatztruhe der Erinnerungen 🔐

Ein echtes kleines Escape-Game für Anni. Fünf Schlösser bewachen eine
Schatztruhe – jedes ist ein eigenständiges Rätsel mit einer versteckten Ziffer.
Sind alle fünf geknackt, ergeben die Ziffern (in Reihenfolge der Schlösser) den
Code der Truhe, und sie öffnet sich zu „Ich liebe dich“.

**So spielt ihr:** Anni öffnet den Link, teilt ihren Bildschirm im Call, und ihr
löst zusammen. Der Fortschritt wird im Browser gespeichert (Neuladen verliert
nichts). Ganz unten gibt es „Spiel zurücksetzen“.

Alles steckt in einer einzigen `index.html` – kein Server, keine Build-Tools.
Zum Testen einfach doppelklicken.

---

## 🧩 Die fünf Rätsel (mit Lösung – nur für dich, Martin)

| # | Schloss | Mechanik | Lösung → Ziffer |
|---|---------|----------|-----------------|
| 1 | Der verschlüsselte Brief | **Vigenère-Chiffre**. Schlüsselwort = **FERNWEH** – versteckt als **Akrostichon** im Gedicht (Anfangsbuchstaben senkrecht: F-E-R-N-W-E-H). Entschlüsselter Brief: „…Zahl der Seiten eines Würfels“ → Würfel = 6 | **6** |
| 2 | Das zerbrochene Bild | Puzzle: Kacheln tauschen (antippen) & drehen (↻), bis das Bild stimmt | **9** |
| 3 | Licht im Dunkeln | Kleiner Lichtkegel; im Dunkeln versteckt: goldene Buchstaben **V₁ I₂ E₃ R₄** (nach kleiner Zahl ordnen → „VIER“) + Regel; rote Buchstaben K/X/Z/Q/B sind Fallen | **4** (VIER) |
| 4 | Das Sternbild (Kreuz des Südens) | Die 5 Sterne vom hellsten (größten) zum dunkelsten verbinden; dann erscheint das Kreuz des Südens | **8** |
| 5 | Die Gleichung der Liebe | 🌙=4, ⭐=3, also ⭐×❤️=21 → ❤️ | **7** |

**Truhen-Code: `6 9 4 8 7`** (Reihenfolge Schloss 1 → 5).

Jedes Schloss hat zwei eingebaute Hinweise (💡 Hinweis), falls ihr feststeckt.

> Design-Hinweise:
> - Es sind bewusst „echte“ Logik-/Geschicklichkeitsrätsel (kein abfragbares Wissen).
> - Schloss 1 ist eine Vigenère-Chiffre (nicht durch simples Durchklicken lösbar) und
>   Schloss 3 verlangt gründliches Absuchen + richtiges Ordnen – beide sind bewusst kniffliger.
> - Das ursprünglich geplante Landkarten-Rätsel hätte euer gemeinsames Wissen gebraucht;
>   es ist durch das **Kreuz des Südens** ersetzt, das man rein logisch (nach Helligkeit) löst.

---

## 📸 Fotos hinzufügen (optional)

Zwei Bild-Slots. Leg passende Dateien in den Ordner `images/`:

| Datei | Wo es erscheint |
|---|---|
| `images/puzzle.jpg` | Schloss 2 – das Puzzle-Bild (am besten quadratisch) |
| `images/finale.jpg` | Das Finale, über „Ich liebe dich“ |

Fehlt eine Datei, wird **automatisch eine gezeichnete Illustration** verwendet –
es sieht also nie kaputt aus. (Bei `images/puzzle.jpg` steckt die Ziffer 9 nicht
im Foto selbst; das Rätsel gilt als gelöst, sobald das Bild korrekt liegt, und
gibt die Ziffer dann frei.)

---

## ✏️ Texte, Lösungen & Finale ändern

Alles steht oben in `index.html`:
- **Texte & Hinweise:** im Array `const LOCKS = [ ... ]`.
- **Finale-Nachricht:** in `renderFinale()`.
- **Eine Lösung ändern:** die betreffende `digit` in `LOCKS` anpassen **und**
  die zugehörige Rätsel-Logik (z. B. bei der Chiffre den `shift`, bei der Algebra
  die Gleichungen). Der Truhen-Code `CODE` oben muss dann zu den fünf Ziffern passen.

**Praktische Test-Links** (nur zum Ausprobieren):
`?reset` (Fortschritt löschen) · `?solveall` (alle Schlösser als gelöst) ·
`?view=finale` (direkt zum Finale).

---

## 🚀 Online stellen mit GitHub Pages

1. Neues **öffentliches** Repo anlegen, z. B. `schatztruhe` (öffentlich, weil
   GitHub Pages sonst kostenpflichtig ist; die Seite ist auf `noindex` gesetzt).
2. Im Projektordner:
   ```bash
   git init
   git add .
   git commit -m "Escape-Game für Anni"
   git branch -M main
   git remote add origin https://github.com/martinpwessel/schatztruhe.git
   git push -u origin main
   ```
3. GitHub → **Settings → Pages → Source: „Deploy from a branch“**, Branch `main`,
   Ordner `/ (root)` → **Save**.
4. Nach ~1 Minute live unter **https://martinpwessel.github.io/schatztruhe/**
5. Fotos später: Dateien in `images/` legen, `git add . && git commit -m "Fotos" && git push`.

Tipp: Vor dem Date einmal selbst durchspielen und dann „Spiel zurücksetzen“, damit
Anni frisch startet. 💗
