---
version: 1.0
conf: 0.80
last_updated: {{DATA_YYYY-MM-DD}}
phase: {{FAZA}}
---

# CHECKLIST — {{NAZWA_PROJEKTU}}

> Jedyne źródło prawdy o aktualnej pracy. Agent ZAWSZE pracuje według tej checklisty.

---

## BLOCKED

| ID | Blocker | Typ | Zależy od | Od kiedy |
|----|---------|-----|-----------|----------|
| A1 | {{Opis blockera}} | {{DATA/TECH/PRODUCT/EXTERNAL/LEGAL}} | {{Kto/co}} | {{Data}} |

---

## IN PROGRESS

| ID | Zadanie | Przypisany | Start |
|----|---------|-----------|-------|
| — | {{Nic w toku}} | — | — |

---

## NEXT (priorytet od góry)

| # | Zadanie | Proof wymagany | Zależy od |
|---|---------|----------------|-----------|
| 1 | {{Następne zadanie}} | {{Co udowodni ukończenie}} | {{Blocker/warunek}} |
| 2 | {{Zadanie 2}} | {{Proof}} | {{Zależy}} |
| 3 | {{Zadanie 3}} | {{Proof}} | {{Zależy}} |
| 4 | {{Zadanie 4}} | {{Proof}} | {{Zależy}} |

---

## BACKLOG

### {{Kategoria 1 — np. UI}}
- [ ] {{Zadanie backlog 1}}
- [ ] {{Zadanie backlog 2}}

### {{Kategoria 2 — np. Backend}}
- [ ] {{Zadanie backlog 3}}
- [ ] {{Zadanie backlog 4}}

### {{Kategoria 3 — np. Strategia}}
- [ ] {{Zadanie backlog 5}}

---

## DONE (ostatnie 15)

| # | Zadanie | Data | Proof |
|---|---------|------|-------|
| — | {{Brak ukończonych}} | — | — |

---

## Zasady dla agentów

1. **CHECKLIST IS KING** — pracuj ZAWSZE według tej listy. Nie z głowy.
2. **Max 1 IN PROGRESS** — skończ bieżące zanim zaczniesz nowe.
3. **NEXT = priorytet** — bierz od góry, nie wybieraj co ci pasuje.
4. **PROOF = DONE** — bez dowodu ukończenia zadanie NIE jest DONE.
5. **BLOCKED ≠ SKIP** — zablokowane zadanie wymaga ROOT_CAUSE, nie ignorowania.
6. **SCOPE LOCK** — nie dodawaj zadań do NEXT w trakcie sprintu (nowe → BACKLOG).
7. **Sync po każdym DONE** — odhacz + zaktualizuj STATE_OF_SYSTEM.md.
8. **Archiwizuj** — po 15 DONE przenieś najstarsze do 🅖_ARCHIVE/checklists/.
