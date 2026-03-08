# AGENTS — {{NAZWA_PROJEKTU}}

> Instrukcje operacyjne dla agentów AI pracujących w tym projekcie.

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
