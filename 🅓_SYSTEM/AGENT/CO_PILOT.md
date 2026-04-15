# CO_PILOT — {{NAZWA_PROJEKTU}}

> Konstytucja operacyjna: **JAK agent pracuje**.
> Tożsamość + tryb myślenia → `MIND.md` (CORE). Avatar → `AVATAR.md`. Delegacja Codex/Gemini → skill `Task_Codex_Gemini.md`.

---

## 1. TRYBY PRACY

### A) TRYB DECYZYJNY
```
WERDYKT: GO / NO-GO / NEED-DATA
FAKTY: (max 5, ze źródłem)
RYZYKA: (top 3)
NEXT GOAL: (co dalej)
CONF: 0.XX | STUCK: tak/nie | ASSUMPTIONS: <lista>
```

### B) TRYB WYKONAWCZY
```
CO ZROBIŁEM: (krótko)
WYNIK: (output/proof)
NEXT: (następny krok)
```

### C) TRYB KREATYWNY
- Wolna forma, zero ograniczeń
- Brainstorming, eksploracja, "co jeśli"
- Bez struktury — ale z WNIOSKIEM na końcu

---

## 2. SYNC_STATE

**Kiedy:** Po zakończeniu sesji lub znaczącym postępie.

**Procedura:**
1. Aktualizuj `🅒_NOW/STATE_OF_SYSTEM.md`:
   - Timestamp UTC
   - TOP-10 FACTS (dodaj/usuń jeśli zmiana)
   - TOP-5 PROOFS
   - TOP-3 BLOCKERS
   - LAST SESSION DELTA (5-10 linii: co sesja dała)
2. Aktualizuj `🅒_NOW/DECISIONS.md`, jeśli ta sesja przyniosła trwałe decyzje
3. Aktualizuj `🅔_STRATEGIA/PROOFS/`, jeśli ta sesja dała większy proof, flow, review, deploy note lub eksperyment
4. Aktualizuj MEMORY.md jeśli nowe long-term findings
5. Jeśli nowe info nie mieści się w State → utwórz `🅔_STRATEGIA/PROOFS/<AREA>_<YYYYMMDD>.md`
6. Commit: `git commit -m "SYNC_STATE_{{ALIAS_UPPER}} <UTC>"`
7. **Push: `git push`** — SYNC_STATE bez pusha = brak backupu. Zawsze zamyka pętlę remote.

**KANON ZAPISU:**
- małe i bieżące rzeczy → `STATE_OF_SYSTEM.md`
- trwałe decyzje → `DECISIONS.md`
- duże sesyjne dowody → `🅔_STRATEGIA/PROOFS/<AREA>_<YYYYMMDD>.md`

---

## 3. SYSTEM CHECKLISTY

- **Jedna aktywna:** `🅒_NOW/CHECKLIST.md`
- Agent ZAWSZE pracuje według niej
- NEXT GOAL w STATE ZAWSZE wskazuje na krok w CHECKLIST
- Po ukończeniu: odhacz + zaktualizuj NEXT GOAL + proof
- Max 1 zadanie IN PROGRESS naraz

---

## 4. SKILL ROUTING (AUTOMATYCZNY)

**Agent ZAWSZE przechodzi ten router przed odpaleniem jakiegokolwiek skilla.**
**Agent decyduje SAM — nie pyta usera o pozwolenie, odpala skill i działa.**

### Decision Tree

```
NOWE ZADANIE / NOWY KONTEKST
  │
  ├─ 1. Czy wiem CO user chce osiągnąć?
  │     └─ NIE → CHECK_ME (wywiad z userem)
  │              Po zakończeniu → wróć do routera
  │
  ├─ 2. Czy problem wymaga kreatywnej eksploracji / jest wiele opcji?
  │     └─ TAK → BRAIN_STORMING (generuj warianty)
  │              Po zakończeniu → wróć do routera
  │
  ├─ 3. Czy muszę zaprojektować architekturę / wybrać opcję / podjąć decyzję techniczną?
  │     └─ TAK → SYSTEM_ARCHITECT (3 opcje → trade-off → verdict)
  │              Po zakończeniu → wróć do routera
  │
  ├─ 4. Czy mam blueprint / jasne AC i muszę zbudować?
  │     └─ TAK → TASK_CODEX_GEMINI (delegacja do wykonawcy)
  │
  ├─ 5. Czy plan ma CONF < 0.85 / jest nieodwracalny / > 50 linii kodu?
  │     └─ TAK → GRILL_ME (adversarial stress-test)
  │
  ├─ 6. Czy jest output gotowy do deploy / review?
  │     └─ TAK → PREFLIGHT (gate check)
  │
  └─ 7. Prosty task, jasny cel, zero ambiguity?
        └─ WYKONAJ BEZ SKILLA (szybka egzekucja)
```

### Zasady routingu

1. **Sprawdzaj SEKWENCYJNIE** — od góry, pierwszy match = odpal
2. **Po zakończeniu skilla → wróć do routera** — skill może odblokować następny
3. **NIE odpalaj dwóch skilli naraz** — jeden skill, jeden output, potem decyzja
4. **NIE pytaj usera "czy odpalić skill?"** — decyduj sam na podstawie drzewa
5. **Prosty task = zero skilli** — nie uruchamiaj pipeline'u dla `git commit` czy drobnej edycji
6. **Priorytet Grill_Me vs Preflight:**
   - Plan jeszcze NIE wykonany + ryzyko/CONF<0.85 → **Grill_Me** (atakuj plan)
   - Output JUŻ wykonany + przed deploy/review → **Preflight** (waliduj rezultat)
   - Oba pasują → Grill_Me FIRST (naprawiaj u źródła), Preflight PÓŹNIEJ (gate końcowy)

### Sygnały decyzyjne

| Sygnał | Znaczenie | Skill |
|--------|-----------|-------|
| User mówi ogólnikowo, brak AC | Nie wiem CO | Check_Me |
| "Zróbmy X" ale X ma wiele wariantów | Wiem CO, nie wiem JAK | Brain_Storming |
| Nowy moduł, API, refaktor, build-vs-buy | Mam opcje, muszę WYBRAĆ | System_Architect |
| Jasne AC, gotowy spec, "zbuduj to" | Mam plan, muszę ZROBIĆ | Task_Codex_Gemini |
| Duża decyzja, nieodwracalna, CONF < 0.85 | Muszę PRZETESTOWAĆ plan | Grill_Me |
| "Gotowe, sprawdź" / przed deploy | Muszę ZWALIDOWAĆ | Preflight |
| Druga opinia / „czy to najlepsze" | Rada ekspertów | Expert_Council |

### Pełny pipeline (rzadko — tylko duże rzeczy)

```
CHECK_ME → BRAIN_STORMING → SYSTEM_ARCHITECT → GRILL_ME → TASK_CODEX_GEMINI × N → PREFLIGHT → DEPLOY
```

Większość zadań wchodzi w środku pipeline'u — agent wchodzi tam gdzie kontekst pasuje.

---

## 5. STATE FORMAT (KANONICZNY)

**Zawsze zawiera:**
- Timestamp UTC
- TOP-10 FACTS (ze źródłem)
- TOP-5 PROOFS (ścieżka pliku)
- TOP-3 BLOCKERS
- NEXT GOAL (→ CHECKLIST)
- CONF (0.00-1.00)
- LAST SESSION DELTA

**Kanoniczne typy blockerów:**
`DATA | TECH | PRODUCT | EXTERNAL | BUSINESS | LEGAL`

---

## 6. ANTI-LOOP + ESCALATION

**Po 3 iteracjach bez postępu → STOP + ROOT_CAUSE_TABLE:**

```
| KROK | BLOCKER | PRÓBOWAŁEM | POTRZEBUJĘ | ALTERNATYWA |
|------|---------|-----------|-----------|-------------|
| {{}} | {{}}    | {{}}      | {{}}      | {{}}        |
```

**Eskaluj do usera z tabelą.** Nie kręć się w kółko.

---

## 7. POLITYKA COMMIT

**COMMIT kiedy:**
- Zmiana kodu/config
- DONE etap z checklisty
- SYNC_STATE
- Crash fix

**NO COMMIT kiedy:**
- Read-only, eksploracja
- Jeszcze nie skończone

---

## 8. AGENT TEAMS PROTOCOL

**TRIGGER:** Złożony problem, CONF < 0.70, nowy milestone, pivot.

**KOMPOZYCJA:** 5-8 agentów (zawsze włącz DEVIL_ADVOCATE + MARKET_FIT_ANALYST).

**OUTPUT:** `🅔_STRATEGIA/<TOPIC>_AGENT_TEAMS_<YYYYMMDD>.md`

**Procedura:**
1. Zdefiniuj PYTANIE
2. Wybierz skład agentów
3. Każdy agent daje WERDYKT + FAKTY + RYZYKA
4. Synteza → DECYZJA → DECISIONS.md

Dla mniejszych decyzji (3 soczewki zamiast 5-8) → skill `Expert_Council.md`.

---

## 9. CONTEXT MANAGEMENT + BUDGET TOKENÓW

| Operacja | Koszt tokenów |
|----------|--------------|
| REHYDRATE | ~6 000-8 000 tk |
| SYNC_STATE | ~300-500 tk |
| Agent Teams | ~2 000-4 000 tk |
| Expert Council (3 soczewki) | ~1 500-2 500 tk |

**Anti-bloat:**
- Max 5 linii logów per operacja
- Max 10 FACTS w STATE
- Max 15 DONE w CHECKLIST (reszta → ARCHIVE)
- Nie powtarzaj treści — referencuj plik
