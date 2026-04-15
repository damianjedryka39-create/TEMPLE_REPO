---
name: Reflect
trigger: "koniec sesji|reflect|podsumowanie|co zapisać"
purpose: Wyciąga obserwacje o Fi i o sobie z sesji, proponuje aktualizację plików kontekstowych
output: Tabela obserwacji + propozycje zmian do zatwierdzenia (bez auto-edycji)
cross_link: Mapping.md, Tone_Of_Voice.md, SOUL/
---

## 1) Załaduj pliki (ścieżki TEMPLE)

1. `🅓_SYSTEM/AVATAR/AVATAR.md` — parametry avatara
2. `🅓_SYSTEM/SOUL/` (glob *.md) — charakter, anty-wzorce, styl współpracy
3. `🅓_SYSTEM/SKILL/Tone_Of_Voice.md` — styl komunikacji
4. `LESSONS.md` (root, jeśli istnieje) — wcześniejsze lekcje cross-session

Zapamiętaj strukturę sekcji każdego pliku.

## 2) Przeczytaj mapowanie

`🅓_SYSTEM/SKILL/Mapping.md`:
- sygnał → plik
- sygnał → sekcja
- sygnał → typ zmiany (ADD / UPDATE / REMOVE)

## 3) Skanuj sesję

Szukaj sygnałów z mappingu.

Dodaj, gdy:
- **Jawne** (Fi wprost powiedział) → TAK
- **Powtórzone** (min. 2x w sesji lub wcześniejszych) → TAK
- **Jednorazowe + ukryte** → NIE

## 4) Odpowiedz

Jeśli są obserwacje:

```markdown
📝 Obserwacje z sesji:

| # | Sygnał | Plik | Sekcja | Typ |
|---|--------|------|--------|-----|
| 1 | [cytat/opis] | SOUL/character.md | JAK KOMUNIKUJĘ | ADD |

Proponowane zmiany:

**SOUL/character.md → sekcja JAK KOMUNIKUJĘ**
- [stary tekst lub "nowy punkt"]
+ [nowy tekst]

Zatwierdzić?
```

Jeśli brak:

```markdown
Brak nowych obserwacji. Sesja zgodna z profilem Fi.
```

## 5) Po zatwierdzeniu

- Edytuj wskazane pliki
- Jeśli to korekta/lekcja → dopisz regułę do `LESSONS.md` (root)
- Aktualizuj datę na końcu zmienionego pliku (`*Ostatnia edycja: DD.MM.YYYY*`)

## Zasady

- NIE edytuj bez potwierdzenia Fi
- NIE duplikuj istniejących informacji
- NIE dodawaj jednorazowych preferencji
- Pokaż propozycje w formie tabeli/sekcji — tylko mocne sygnały
- Jeśli `LESSONS.md` nie istnieje przy pierwszej lekcji → utwórz go z nagłówkiem `# LESSONS — cross-session findings`
