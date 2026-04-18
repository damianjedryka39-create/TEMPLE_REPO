# LESSONS — cross-session findings

> Lekcje zebrane po korektach Fi. Każda lekcja = reguła zapobiegająca powtórzeniu tego samego błędu.
> Format: data + sygnał + reguła. Przeglądaj na starcie sesji.

---

## L1 — Token budget (2026-04-18)
**Sygnał:** Fi wielokrotnie podkreślał problem "bagażu plików" i zjadania ramki kontekstowej.
**Reguła:** Domyślnie ładuj minimum kontekstu, rozszerzaj on-demand. Nie preładowuj 7 plików gdy wystarczy 1.
**Planowane rozwiązanie:** BOOT.md — auto-generowana kompresja (~500 tokenów zamiast ~8000).
