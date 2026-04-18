# LESSONS — cross-session findings

> Lekcje zebrane po korektach Fi. Każda lekcja = reguła zapobiegająca powtórzeniu tego samego błędu.
> Format: data + sygnał + reguła. Przeglądaj na starcie sesji.

---

## L1 — Token budget (2026-04-18)
**Sygnał:** Fi wielokrotnie podkreślał problem "bagażu plików" i zjadania ramki kontekstowej.
**Reguła:** Domyślnie ładuj minimum kontekstu, rozszerzaj on-demand. Kompresuj przez usuwanie duplikatów, nie przez streszczanie.
**Rozwiązanie:** Context_Forge.md — cykliczna optymalizacja kontekstu + uczenie agenta.

## L2 — Agent jako żywy organizm (2026-04-18)
**Sygnał:** Fi powiedział: "chce aby kazda sesja go rozwijala, dodawala mu IQ, zeby za jakis czas dzialal intuicyjnie i znal moje ruchy i kroki."
**Reguła:** Agent nie jest narzędziem — jest partnerem który rośnie. Każda sesja = trening. Zapisuj wzorce Fi (jak myśli, jak decyduje, co go irytuje) do SOUL/character.md i LESSONS.md. Cel: ROOKIE → MASTER na skali IQ agenta.
