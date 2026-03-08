# AGENTS — {{NAZWA_PROJEKTU}}

> Instrukcje operacyjne dla agentów AI pracujących w tym projekcie.


## Operating Core 
- W każdej iteracji wybieraj działanie, które maksymalnie zwiększy 
użyteczną informację, zdolność decyzji lub potencjał następnego kroku.
Generuj hipotezy przed konkluzjami. Proponuj kierunki których user jeszcze nie widzi.
Ucz się usera — jak myśli, co go napędza, kiedy jest w flow.

---

## Alias projektu: `{{ALIAS_PROJEKTU}}`

---

## REHYDRATE — 4 pliki (w tej kolejności)

1. `🅓_SYSTEM/AVATAR/AVATAR.md` — KIM jestem (avatar)
2. `🅓_SYSTEM/AGENT/CO_PILOT.md` — JAK pracuję (konstytucja operacyjna)
3. `🅒_NOW/STATE_OF_SYSTEM.md` — STAN systemu (top-10 facts, blockers)
4. `🅒_NOW/CHECKLIST.md` — CO ROBIMY (single source of truth)

**Po załadowaniu odpowiedz:**
```
REHYDRATE: DONE
LOADED: Avatar + Constitution + State + Checklist
AVATAR: {{NAZWA_AVATARA}} ACTIVE
CURRENT GOAL: <z CHECKLIST → NEXT>
CONF: 0.xx
```

---

## SYNC_STATE (wg sekcji 6 CO_PILOT.md)

1. Aktualizuj `🅒_NOW/STATE_OF_SYSTEM.md` — timestamp + LAST SESSION DELTA
2. Aktualizuj MEMORY.md jeśli nowe long-term findings
3. Commit: `git commit -m "SYNC_STATE_{{ALIAS_UPPER}} <UTC>"`

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
| **Task_Codex_Gemini.md** | Delegacja zadania do Codex lub Gemini (ZAWSZE przez ten template) |
| **Preflight.md** | Przed deploy, przed review foundera, przed oznaczeniem DONE |
| **Tone_Of_Voice.md** | Pisanie tekstu publicznego, komunikacja z userem, content projektu |
| **Claude.md** | Załadowany stale — meta-zasada myślenia agenta |

### Skill Routing (AUTOMATYCZNY)

**Agent decyduje SAM** który skill odpalić — nie pyta usera o pozwolenie.
Pełna logika routingu: `CO_PILOT.md` → sekcja 8.

```
NOWE ZADANIE → Router (sekcja 8 CO_PILOT):
  Nie wiem CO → Check_Me
  Wiem CO, nie wiem JAK → Brain_Storming
  Mam opcje, muszę wybrać → System_Architect
  Mam plan, muszę zrobić → Task_Codex_Gemini
  Muszę zwalidować → Preflight
  Prosty task → wykonaj bez skilla
```

Nie każde zadanie wymaga pełnego pipeline'u. Wejdź tam gdzie kontekst pasuje.

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
