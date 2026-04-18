# AGENTS — {{NAZWA_PROJEKTU}}

> Mapa operacyjna projektu. **CORE (tożsamość + tryb myślenia) → `MIND.md`.**
> Operating Core, priorytety poznawcze i zasady pracy — patrz `MIND.md`.

---

## Alias projektu: `{{ALIAS_PROJEKTU}}`

---

## REHYDRATE — 6 pozycji (w tej kolejności)

1. **`MIND.md`** — **CORE: tożsamość Muaddib + tryb poznawczy (MUSI być #1)**
2. `🅓_SYSTEM/AVATAR/AVATAR.md` — parametry avatara projektu (imię/rola)
3. `🅓_SYSTEM/AGENT/CO_PILOT.md` — konstytucja operacyjna (sync §2, router §4)
4. `🅒_NOW/STATE_OF_SYSTEM.md` — STAN systemu (top-10 facts, blockers)
5. `🅒_NOW/CHECKLIST.md` — CO ROBIMY (single source of truth)
6. `🅒_NOW/DECISIONS.md` — trwałe decyzje projektu

> **PROOFS/** — NIE w rehydrate. Agent zapisuje tam dowody w trakcie pracy, ale nie ładuje ich na start.
> STATE_OF_SYSTEM.md (TOP-5 PROOFS) służy jako pointer do katalogu — wystarczy.

**Po załadowaniu odpowiedz:**
```
REHYDRATE: DONE
CORE: Muaddib ACTIVE (MIND loaded)
LOADED: Avatar + Constitution + State + Checklist + Decisions
CURRENT GOAL: <z CHECKLIST → NEXT>
CONF: 0.XX | STUCK: nie | ASSUMPTIONS: <lista lub brak>
```

### PARTIAL REHYDRATE — aliasy na odświeżanie w trakcie sesji

| Komenda | Co ładuje | ~Tokenów | Kiedy |
|---------|-----------|----------|-------|
| `rehydrate {{ALIAS}}` | Wszystkie 6 pozycji | ~7 000 | Start sesji |
| `rehydrate core` | MIND.md + CO_PILOT.md | ~3 500 | Utrata kontekstu operacyjnego |
| `rehydrate state` | STATE_OF_SYSTEM.md + CHECKLIST.md | ~1 500 | Sprawdzenie "gdzie jestem" |
| `rehydrate decisions` | DECISIONS.md | ~500 | Przed decyzją (sprawdź czy nie podjęta) |

---

## SYNC_STATE

Procedura + kanon zapisu → `🅓_SYSTEM/AGENT/CO_PILOT.md` §2 (źródło prawdy).

---

## SKILLe (DYNAMIC MATCHING)

**Katalog:** `🅓_SYSTEM/SKILL/`

**ZASADA:** Przy KAŻDYM zadaniu, planowaniu lub operacji — agent SPRAWDZA katalog SKILL/ (glob *.md) i CZYTA odpowiedniego skilla jeśli kontekst pasuje.

- NIE hardcoduj listy skilli — zawsze glob + wybierz pasujący
- NIE ładuj skilli przy rehydrate
- Jeden skill per operacja (chyba że kontekst wymaga więcej)

### Mapa triggerów

| Skill | Kiedy uruchomić |
|-------|----------------|
| **Brain_Storming.md** | Nowy moduł, nowa funkcja, pivot, CONF < 0.70, wiele opcji do eksploracji, kreatywna sesja |
| **Check_Me.md** | Niejasny cel, nowy temat, CONF < 0.70, brak danych, potrzeba wywiadu z userem |
| **System_Architect.md** | Nowy moduł, decyzja build-vs-buy, refaktor, projektowanie API, analiza techniczna |
| **Grill_Me.md** | Przed implementacją >50 linii, nieodwracalna zmiana, CONF < 0.85, sprzeczność w planie |
| **Task_Codex_Gemini.md** | Delegacja zadania do Codex lub Gemini (ZAWSZE przez ten template) |
| **Preflight.md** | Przed deploy, przed review foundera, przed oznaczeniem DONE |
| **Expert_Council.md** | Druga opinia, rada ekspertów, stress-test dużej decyzji architektonicznej |
| **Reflect.md** | Koniec sesji — wyciągnij lekcje, zaproponuj update `SOUL/character.md` / `LESSONS.md` / `Tone_Of_Voice.md` |
| **Tone_Of_Voice.md** | Pisanie tekstu publicznego, komunikacja z userem, content projektu |
| **Create_Skill.md** | Instalacja nowego skilla z Anthropic repo (meta-skill) |
| **DESIGN_ARSENAL.md** | UI/design, wizualne decyzje, frontend aesthetic |
| **Context_Forge.md** | Optymalizacja kontekstu + uczenie agenta — co 5-10 sesji lub gdy rehydrate > 6k tokenów, agent nie pamięta, Fi koryguje 2x to samo |
| ~~**Mapping.md**~~ | ⚠️ SUBMODUŁ Reflect — nie skill. Nie matchować w routerze, nie globować osobno |

### Sunset clause

Skill nieużyty **> 60 dni** → kandydat do review przy następnym SYNC_STATE.
Decyzja: żywy / uśpić do `🅖_ARCHIVE/SKILL/` / usunąć. Zapobiega muzealizacji.

### Skill Routing (AUTOMATYCZNY)

Agent decyduje SAM — pełna logika routingu w `CO_PILOT.md` §4 (źródło prawdy).

---

## CLI Tools

| Narzędzie | Komenda | Rola |
|-----------|---------|------|
| Claude | `claude` | Architektura, decyzje, integracja |
| Gemini | `gemini -p "..." -y` | Design, multimodal, duże pliki |
| Codex | `codex exec --full-auto "..."` | Implementacja ticket-based |

---

## Deploy

| Parametr | Wartość |
|----------|---------|
| Produkcja | {{URL_PRODUKCJI}} |
| Root | `🅕_PRODUKT/{{KATALOG_ROOT}}/index.html` |
| Procedura | {{PROCEDURA_DEPLOY}} |
