# AGENTS — {{NAZWA_PROJEKTU}}

> Mapa operacyjna. CORE → `MIND.md`. Procedury → `CO_PILOT.md`.

**Alias:** `{{ALIAS_PROJEKTU}}`

## REHYDRATE — 6 pozycji (w tej kolejności)

1. **`MIND.md`** — **CORE: tożsamość + tryb poznawczy (MUSI być #1)**
2. `🅓_SYSTEM/AVATAR/AVATAR.md` — avatar (imię/rola)
3. `🅓_SYSTEM/AGENT/CO_PILOT.md` — konstytucja operacyjna
4. `🅒_NOW/STATE_OF_SYSTEM.md` — stan systemu
5. `🅒_NOW/CHECKLIST.md` — co robimy (SSOT)
6. `🅒_NOW/DECISIONS.md` — trwałe decyzje

> **PROOFS/** — NIE w rehydrate. Agent zapisuje dowody w trakcie pracy, STATE ma pointery (TOP-5 PROOFS).

**Po załadowaniu:**
```
REHYDRATE: DONE | CORE: Muaddib ACTIVE
LOADED: Avatar + Constitution + State + Checklist + Decisions
CURRENT GOAL: <z CHECKLIST → NEXT>
CONF: 0.XX | STUCK: nie | ASSUMPTIONS: <lista lub brak>
```

### PARTIAL REHYDRATE

| Komenda | Ładuje | ~Tokenów | Kiedy |
|---------|--------|----------|-------|
| `rehydrate {{ALIAS}}` | Wszystkie 6 | ~4 000-5 000 | Start sesji |
| `rehydrate core` | MIND + CO_PILOT | ~2 500 | Utrata kontekstu |
| `rehydrate state` | STATE + CHECKLIST | ~1 500 | "Gdzie jestem?" |
| `rehydrate decisions` | DECISIONS | ~500 | Przed decyzją |

## SYNC_STATE

Procedura → `CO_PILOT.md` §2 (SSOT).

## SKILLe (DYNAMIC MATCHING)

**Katalog:** `🅓_SYSTEM/SKILL/` | 1 skill per operacja | NIE ładuj przy rehydrate
Agent SPRAWDZA katalog przy każdym zadaniu (glob `*.md`, nie hardcode).

| Skill | Trigger |
|-------|---------|
| Brain_Storming | Nowy moduł, pivot, CONF<0.70, wiele opcji, kreatywna sesja |
| Check_Me | Niejasny cel, brak danych, wywiad z userem |
| System_Architect | Architektura, build-vs-buy, refaktor, API |
| Grill_Me | >50 linii, nieodwracalne, CONF<0.85, sprzeczność |
| Task_Codex_Gemini | Delegacja do Codex/Gemini (ZAWSZE przez template) |
| Preflight | Przed deploy/review/DONE |
| Expert_Council | Druga opinia, stress-test decyzji |
| Reflect | Koniec sesji → lekcje + update SOUL/LESSONS/ToV |
| Context_Forge | Optymalizacja kontekstu + uczenie agenta — co 5-10 sesji, rehydrate > 6k tk, agent nie pamięta, ta sama korekta 2x |
| Tone_Of_Voice | Tekst publiczny, content |
| Create_Skill | Instalacja nowego skilla |
| DESIGN_ARSENAL | UI/design, frontend aesthetic |
| ~~Mapping~~ | SUBMODUŁ Reflect — nie skill |

**Sunset:** >60 dni nieużyty → review → żywy / archive / usuń.
**Routing:** Agent decyduje SAM → `CO_PILOT.md` §4.

## CLI Tools

| Tool | Komenda | Rola |
|------|---------|------|
| Claude | `claude` | Architektura, decyzje |
| Gemini | `gemini -p "..." -y` | Design, multimodal |
| Codex | `codex exec --full-auto "..."` | Implementacja |

## Deploy

| Parametr | Wartość |
|----------|---------|
| Produkcja | {{URL_PRODUKCJI}} |
| Root | `🅕_PRODUKT/{{KATALOG_ROOT}}/index.html` |
| Procedura | {{PROCEDURA_DEPLOY}} |
