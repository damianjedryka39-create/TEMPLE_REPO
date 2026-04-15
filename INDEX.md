# INDEX — {{NAZWA_PROJEKTU}}

> Entry point dla agentów i ludzi. Przeczytaj w 60 sekund.
> **Jedyny plik, który powinieneś otworzyć jako pierwszy.** Wszystkie inne ścieżki są stąd.

---

## 0. Jak się tu poruszać (30 sekund)

1. **Nowy agent** → `rehydrate {{ALIAS_PROJEKTU}}` (ładuje 7 plików wg `AGENTS.md`)
2. **Nowy człowiek** → czytaj ten plik (INDEX), potem `🅐_OPIS/OPIS_PROJEKTU.md`
3. **Nowy projekt z TEMPLE** → czytaj `INIT.md` (tylko raz, potem się usuwa)

---

## 1. ROOT FILES — kto jest właścicielem i po co (Single Source of Truth)

| Plik | Owner | Temat (SSOT) | Kto czyta | Kiedy |
|------|-------|--------------|-----------|-------|
| **`MIND.md`** | Agent (CORE) | **Tożsamość + tryb myślenia Muaddib** | Agent | Pierwszy przy rehydrate (#1) |
| **`AGENTS.md`** | Agent + Codex CLI | **Mapa operacyjna + REHYDRATE list** | Agent, Codex auto-discovery | Rehydrate, bootstrap |
| **`CONSTITUTION.md`** | Projekt ({{OWNER}}) | **Wartości niezmienne + Dekalog** | Agent, człowiek | Wątpliwość etyczna, nowa decyzja |
| **`INDEX.md`** (ten plik) | Projekt | **Mapa repo + ownership** | Człowiek, nowy agent | Pierwsze wejście |
| **`INIT.md`** | TEMPLE bootstrap | **Procedura forku TEMPLE → nowy projekt** | Agent (tylko przy INIT) | Tylko raz — potem `rm -f INIT.md` |
| **`LESSONS.md`** | Agent (pamięć) | **Cross-session lessons (reguły po korektach)** | Agent | Na starcie sesji + po Reflect |
| **`MEMORY.md`** | Agent (pamięć) | **Long-term findings (destylat wielu sesji)** | Agent | Podczas sync_state |

---

## 2. SINGLE SOURCE OF TRUTH — kto mówi o czym

> **Zasada:** Jeśli temat X jest w tabeli poniżej — TYLKO ten plik jest autorytatywny.
> Inne pliki mogą się odnosić (`patrz X.md §Y`), ale **NIE duplikują treści**.

| Temat | Źródło prawdy | Komentarz |
|-------|---------------|-----------|
| Tożsamość agenta, tryb myślenia, zasady poznawcze | `MIND.md` | CORE — czytany jako #1 |
| Lista REHYDRATE (7 plików), aliasy, mapa skilli | `AGENTS.md` | Konwencja + trigger table |
| Procedura SYNC_STATE, skill routing, polityka commit, token budget | `🅓_SYSTEM/AGENT/CO_PILOT.md` | Konstytucja operacyjna |
| Wartości projektu, Dekalog, Non-negotiables, misja | `CONSTITUTION.md` | Wartości — nie "jak pracować" |
| Avatar (imię, rola, kompetencje) | `🅓_SYSTEM/AVATAR/AVATAR.md` | Per-projekt |
| Charakter / głos agenta (ton, anty-wzorce) | `🅓_SYSTEM/SOUL/character.md` | Rośnie przez Reflect |
| Bieżące zadania (NEXT, IN PROGRESS, DONE) | `🅒_NOW/CHECKLIST.md` | Jedyna aktywna checklist |
| Stan systemu (TOP-10 facts, blockers) | `🅒_NOW/STATE_OF_SYSTEM.md` | Aktualizowany przy sync_state |
| Trwałe decyzje projektu | `🅒_NOW/DECISIONS.md` | Nie debatuj ponownie |
| Proofy sesyjne (duże dowody) | `🅔_STRATEGIA/PROOFS/<AREA>_<YYYYMMDD>.md` | Kanon: "małe → STATE, duże → PROOFS" |
| Lekcje cross-session | `LESSONS.md` | Dopisywane przez skill Reflect |
| Long-term findings | `MEMORY.md` | Destylat, nie dziennik |

**Reguła:** Jeśli masz zmienić coś o procedurach pracy → idziesz do `CO_PILOT.md`, NIE do MIND ani AGENTS. MIND = **kim jesteś**, CO_PILOT = **jak pracujesz**, AGENTS = **co ładować**.

---

## 3. MAPA FOLDERÓW 🅐-🅖

| Folder | Zawartość | Owner | Kiedy czytać |
|--------|-----------|-------|-------------|
| `🅐_OPIS/` | Pełny opis projektu (PROP), kontekst, tło | Projekt | Nowy agent, nowa sesja kreatywna |
| `🅑_ROADMAP/` | Event-driven plan działania, fazy | Projekt | Co budować dalej |
| `🅒_NOW/` | **Aktualny sprint** — CHECKLIST, STATE, DECISIONS | Projekt (bieżące) | Codziennie. Jedyne źródło prawdy o TERAZ |
| `🅓_SYSTEM/` | **Agent OS** — Avatar, Soul, Skills, CO_PILOT | Agent | Praca agenta, delegacja, router skilli |
| `🅔_STRATEGIA/` | Archiwum analiz, Agent Teams, debaty, PROOFS | Projekt (historia) | Research, background, deep context |
| `🅕_PRODUKT/` | Kod produkcyjny (landing, app, API) | Projekt | Zadania deweloperskie |
| `🅖_ARCHIVE/` | Stare pliki, duplikaty, historia | Archiwum | Rzadko |

### Podkatalogi `🅓_SYSTEM/`

- `AGENT/CO_PILOT.md` — konstytucja operacyjna (procedury, router, sync, token budget)
- `AVATAR/AVATAR.md` — tożsamość agenta w projekcie (imię, rola, kompetencje)
- `SOUL/character.md` — charakter, ton, anty-wzorce, styl współpracy (rośnie przez Reflect)
- `SKILL/*.md` — skille dynamiczne (Check_Me, Brain_Storming, Grill_Me, itd.) — ładowane on-demand przez router w `CO_PILOT.md §4`

---

## 4. Produkcja

| Parametr | Wartość |
|----------|---------|
| URL | {{URL_PRODUKCJI}} |
| Root | `🅕_PRODUKT/{{KATALOG_ROOT}}/index.html` |
| Serwer | {{SERWER — np. Nginx, Vercel, Cloudflare}} |
| SSL | {{STATUS_SSL}} |
| Deploy | {{PROCEDURA_DEPLOY}} |

---

## 5. Agenci w Projekcie

| Agent | Rola | Narzędzie |
|-------|------|-----------|
| Claude Code | Architektura, decyzje, integracja, gatekeeper | `claude` |
| Gemini CLI | Design, multimodal, duże pliki, generacja UI | `gemini -p "..." -y` |
| Codex CLI | Ticket-based implementacja | `codex exec --full-auto "..."` |

Delegacja do Codex/Gemini → **zawsze przez skill** `🅓_SYSTEM/SKILL/Task_Codex_Gemini.md`.

---

## 6. Rehydrate Protocol

**Komenda:** `rehydrate {{ALIAS_PROJEKTU}}`

**Źródło prawdy:** `AGENTS.md` → sekcja REHYDRATE (7 pozycji, MIND.md jako #1).
**Ten plik NIE duplikuje listy** — zapobiega split-brain.

**Po rehydrate:** STOP na statusie. `NEXT ACTION` ustala dopiero agent wykonujący `sync_state` (wg kanonu `CO_PILOT.md §2`).

---

## 7. Quick Reference — gdzie co zmieniam

| Chcę zmienić... | Idę do... |
|-----------------|-----------|
| Sposób myślenia agenta | `MIND.md` |
| Procedurę pracy (sync, commit, routing) | `🅓_SYSTEM/AGENT/CO_PILOT.md` |
| Listę plików do rehydrate | `AGENTS.md §REHYDRATE` |
| Wartość / zasadę projektu | `CONSTITUTION.md` |
| Imię/rolę avatara | `🅓_SYSTEM/AVATAR/AVATAR.md` |
| Bieżące zadanie | `🅒_NOW/CHECKLIST.md` |
| Trwałą decyzję | `🅒_NOW/DECISIONS.md` |
| Skill (istniejący) | `🅓_SYSTEM/SKILL/<nazwa>.md` |
| Nowy skill | `🅓_SYSTEM/SKILL/_TEMPLATE_SKILL.md` → kopia |
