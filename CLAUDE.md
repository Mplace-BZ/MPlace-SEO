## KRYTYCZNE ZASADY — CZEGO NIE RUSZAC

### Agent / Cloudflare Worker / SSE
- NIE modyfikuj funkcji fetch wysylajcej zapytania do Cloudflare Worker
- NIE zmieniaj obslugi odpowiedzi SSE (stream reader, chunks, delta.text)
- NIE zastepuj SSE readera zwyklym response.json()
- Worker URL: https://red-haze-5f37mplace-agent.contactmplace.workers.dev
- Worker zawsze zwraca SSE (text/event-stream) — kod MUSI to obslugiwac
- Jesli Agent dziala poprawnie → nie dotykaj kodu fetch/stream/Worker

### Zapis danych
- Save = zawsze saveAllWithSync() — nigdy saveAll()
- Nie modyfikuj logiki zapisu bez wyraznej instrukcji

### Firebase
- Flaga _fsLoaded — nie usuwaj, chroni przed nadpisaniem swiezych danych
- onAuthStateChanged moze strzelac wielokrotnie — to normalne, nie "naprawiaj"

### Print CSS
- Nigdy nie modyfikuj @media print — bez wyjatkow

### Playbook
- PLAYBOOK_SECTIONS musi byc zdefiniowany PRZED funkcja openPlaybook()
- Nie skracaj promptow — wszystkie 100 musi byc zachowane w pelnej tresci
