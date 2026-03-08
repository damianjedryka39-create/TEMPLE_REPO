# TASK CONTRACT — Template delegacji do Codex/Gemini

Użyj tego szablonu ZAWSZE gdy delegujesz zadanie do Codex CLI lub Gemini CLI.
Wypełnij KAŻDE pole. Puste pole = słaba delegacja = słaby output.

---

## TASK CONTRACT: [nazwa zadania]

### CEL
[1 zdanie — co ma powstać. Konkretnie, mierzalnie.]

### INPUT
[Pliki/dane które agent dostaje. Pełne ścieżki.]
- Plik 1: `🅓_SYSTEM/SKILL/...`
- Plik 2: ...
- Kontekst: [krótki opis sytuacji, max 3 zdania]

### OUTPUT
[Dokładnie co ma zwrócić — format, pliki, nazwy, gdzie zapisać.]
- Plik wynikowy: `🅕_PRODUKT/...`
- Format: [HTML/MD/JSON/kod]

### AC (Acceptance Criteria)
[3-5 sprawdzalnych punktów. Każdy musi być TAK/NIE.]
1. [ ] ...
2. [ ] ...
3. [ ] ...

### ZAKAZ (Scope Guard)
[Czego NIE robić. Co jest poza zakresem.]
- NIE: ...
- NIE: ...

### DoD (Definition of Done)
[Jak sprawdzić że gotowe. Komenda, test, wizualna weryfikacja.]
- Sprawdzenie: ...
- Proof: ...

---

## PRZYKŁAD WYPEŁNIONEGO CONTRACTU

### CEL
Wygeneruj landing page v1 w stylu nowoczesnym.

### INPUT
- Spec: `🅓_SYSTEM/SKILL/...`
- Referencja: `🅕_PRODUKT/assets/reference.jpg`
- Kontekst: Pierwsza wersja landing page. Founder chce "stronę jak grę".

### OUTPUT
- 3 pliki: `🅕_PRODUKT/landing/index.html` + `style.css` + `app.js`
- Max 60KB total, 0 external images

### AC
1. [ ] Responsywność desktop + mobile
2. [ ] 0 console errors
3. [ ] Load time < 3s

### ZAKAZ
- NIE używaj external images (wszystko w kodzie)
- NIE dodawaj nowych sekcji poza spec
- NIE zmieniaj kolorystyki ze spec

### DoD
- Preview: `python3 -m http.server 8081` → wizualna weryfikacja
- Console: 0 errors
- Size: `du -sh 🅕_PRODUKT/landing/` < 60KB
