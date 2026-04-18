---
version: 1.0
status: ACTIVE
rule: "Nie debatuj ponownie — jeśli temat był tu zdecydowany, agent czyta decyzję zamiast otwierać dyskusję od nowa."
---

# DECISIONS — {{NAZWA_PROJEKTU}}

> Log decyzji architektonicznych. Każda strategiczna decyzja ląduje tu — nie w głowie, nie w chacie.

---

## Decyzje

| # | Data | Decyzja | Opcje rozważane | Dlaczego | CONF |
|---|------|---------|-----------------|----------|------|
| D1 | 2026-04-18 | CHECKLIST.md = SSOT zadań (nie todo.md) | todo.md vs CHECKLIST.md | MIND i CO_PILOT miały sprzeczne systemy. Jeden SSOT eliminuje chaos | 0.95 |
| D2 | 2026-04-18 | Agent decyduje sam o skillach (wg CO_PILOT §4) | autonomia vs zgoda usera | CO_PILOT §4 = SSOT procedur. MIND definiuje zasady, CO_PILOT egzekwuje | 0.90 |
| D3 | 2026-04-18 | Reflect wbudowany w router (krok 0+8) i SYNC (krok 0) | manualny vs automatyczny | Pętla samodoskonalenia musi być zamknięta — manual nie działał (LESSONS pusty) | 0.92 |
| D4 | 2026-04-18 | Partial rehydrate: core/state/decisions | full-only vs partial | 8k tokenów na start to za dużo. Partial pozwala na 1.5k refresh mid-session | 0.88 |
| D5 | 2026-04-18 | BOOT.md jako domyślny rehydrate (planowane) | full vs BOOT vs hybrid | 500 tokenów vs 8000. Agent ładuje resztę on-demand. Wymaga implementacji | 0.85 |

---

## Jak dodać nową decyzję

```markdown
| D{{N}} | {{DATA}} | {{DECYZJA}} | {{OPCJE}} | {{DLACZEGO}} | {{CONF}} |
```

**Zasady:**
1. Numer sekwencyjny (D1, D2, D3...)
2. Data w formacie YYYY-MM-DD
3. Decyzja = co zdecydowano (krótko, imperatywnie)
4. Opcje rozważane = jakie alternatywy były na stole
5. Dlaczego = twarde uzasadnienie (dane, fakty, źródła — nie "wydaje mi się")
6. CONF = confidence level (0.75-1.00; niska = decyzja może się zmienić)

**Reguła systemowa:** Jeśli agent chce zmienić zdecydowany temat → MUSI najpierw przeczytać tę tabelę i uzasadnić DLACZEGO nowa informacja zmienia kalkulację.
