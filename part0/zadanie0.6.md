```mermaid
sequenceDiagram
participant browser
participant server

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa
    activate server
    server-->>browser: Dane odpowiedzi zawierające nowo utworzoną notatkę
    deactivate server

    Note right of browser: Przeglądarka wykonuje funkcję zwrotną, która wyświetla notatki
```
