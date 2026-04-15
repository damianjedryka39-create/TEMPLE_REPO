# INDEX — {{NAZWA_PROJEKTU}}

> Entry point dla agentów i ludzi. Przeczytaj w 60 sekund.

---

## Opis 

Stwórz nowy projekt [NAZWA] w katalogu [ŚCIEŻKA] na podstawie szablonu z /root/GOFANS-NEOVERSE/TEMPLE_REPO. Skopiuj całą strukturę, zamień wszystkie {{placeholdery}} na dane projektu. Projekt dotyczy: [2-3 zdania co to jest].
Zachowaj wszystkie skile takie jakie są. Skili nie zmieniaj. Poprostu je tylko skopiuj z Temple_Repo i umiesc w nowym REPO. 


## Kolejność czytania dla agenta

Agent po `rehydrate` ładuje 7 plików wg `AGENTS.md` (MIND.md jako #1).
Pliki pomocnicze do szybkiego zorientowania się w repo:

| Plik | Cel | Kiedy |
|------|-----|-------|
| **INDEX.md** (ten plik) | Struktura repo | Pierwsze wejście człowieka |
| **🅐_OPIS/OPIS_PROJEKTU.md** | Kontekst projektu | On-demand |
| **🅕_PRODUKT/** | Kod produkcyjny | Zadania deweloperskie |
| **CONSTITUTION.md** | Wartości niezmienne | Wątpliwość etyczna |

---

## Mapa Repozytorium

| Folder | Zawartość | Kiedy czytać |
|--------|-----------|-------------|
| `CONSTITUTION.md` | Niezmienne zasady, Dekalog, Non-negotiables | Zawsze pierwszy. Agent nigdy nie zmienia. |
| `INDEX.md` | Ten plik — mapa repo | Każde wejście |
| `🅐_OPIS/` | Pełny opis projektu (PROP) | Nowy agent, partner, sesja kreatywna |
| `🅑_ROADMAP/` | Event-driven plan działania | Co budować dalej, fazy |
| `🅒_NOW/` | Aktualny sprint + log decyzji | Codziennie. Jedyne źródło prawdy o TERAZ. |
| `🅓_SYSTEM/` | Agent OS: Avatar, Soul, Skills, Protokoły | Praca agenta, delegacja do narzędzi |
| `🅔_STRATEGIA/` | Archiwum analiz, Agent Teams, debaty | Research, background, deep context |
| `🅕_PRODUKT/` | Kod produkcyjny (landing, app, API) | Zadania deweloperskie |
| `🅖_ARCHIVE/` | Stare pliki, duplikaty, historia | Rzadko. Historia. |

---

## Produkcja

| Parametr | Wartość |
|----------|---------|
| URL | {{URL_PRODUKCJI}} |
| Root | `🅕_PRODUKT/{{KATALOG_ROOT}}/index.html` |
| Serwer | {{SERWER — np. Nginx, Vercel, Cloudflare}} |
| SSL | {{STATUS_SSL}} |
| Deploy | {{PROCEDURA_DEPLOY}} |

---

## Agenci w Projekcie

| Agent | Rola | Narzędzie |
|-------|------|-----------|
| Claude Code | Architektura, decyzje, integracja, gatekeeper | `claude` |
| Gemini CLI | Design, multimodal, duże pliki, generacja UI | `gemini -p "..." -y` |
| Codex CLI | Ticket-based implementacja | `codex exec --full-auto "..."` |

---

## Rehydrate Protocol

**Komenda:** `rehydrate {{ALIAS_PROJEKTU}}`

**Źródło prawdy:** `AGENTS.md` → sekcja REHYDRATE (7 pozycji, MIND.md jako #1).
Ten plik NIE duplikuje listy — zapobiega split-brain.

**Następnie:** NATYCHMIAST NEXT ACTION z checklisty.
