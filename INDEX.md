# INDEX — {{NAZWA_PROJEKTU}}

> Entry point dla agentów i ludzi. Przeczytaj w 60 sekund.

---

## Kolejność czytania dla agenta

| Krok | Plik | Cel | Czas |
|------|------|-----|------|
| 1 | **INDEX.md** (ten plik) | Struktura repo | 60 sek |
| 2 | **🅒_NOW/CHECKLIST.md** | NEXT ACTION | 30 sek |
| 3 | **🅐_OPIS/OPIS_PROJEKTU.md** | Kontekst projektu (jeśli potrzebny) | 2 min |
| 4 | **🅕_PRODUKT/** | Kod produkcyjny (jeśli deployment) | on-demand |
| 5 | **CONSTITUTION.md** | Wartości (jeśli wątpliwość) | 1 min |

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

**Kolejność ładowania (4 pliki):**
1. `🅓_SYSTEM/AVATAR/AVATAR.md` — KIM jestem (avatar)
2. `🅓_SYSTEM/AGENT/CO_PILOT.md` — JAK pracuję (konstytucja operacyjna)
3. `🅒_NOW/STATE_OF_SYSTEM.md` — STAN systemu (top-10 facts, blockers)
4. `🅒_NOW/CHECKLIST.md` — CO ROBIMY (single source of truth)

**Format odpowiedzi po rehydrate:**
```
REHYDRATE: DONE
LOADED: Avatar + Constitution + State + Checklist
AVATAR: {{NAZWA_AVATARA}} ACTIVE
CURRENT GOAL: <z CHECKLIST → NEXT>
CONF: 0.xx
```

**Następnie:** NATYCHMIAST NEXT ACTION z checklisty.
