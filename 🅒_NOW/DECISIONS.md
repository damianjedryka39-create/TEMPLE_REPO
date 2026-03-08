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
| D1 | {{YYYY-MM-DD}} | {{Krótki opis decyzji}} | {{Opcja A vs Opcja B vs ...}} | {{Uzasadnienie — twarde fakty}} | {{0.XX}} |

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
