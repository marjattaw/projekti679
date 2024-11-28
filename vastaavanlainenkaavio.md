sequenceDiagram
    participant user as Käyttäjä
    participant browser as Selain
    participant server as Palvelin

    user->>browser: Kirjoittaa muistiinpanon ja painaa "Tallenna"-nappia
    browser->>server: POST /new_note
    activate server
    Note right of server: Palvelin vastaanottaa JSON-muodossa:<br>{ "content": "Uusi muistiinpano", "date": "2024-11-27" }
    server-->>browser: HTTP 302 Found (Redirect -> /notes)
    deactivate server

    browser->>server: GET /notes
    activate server
    server-->>browser: HTML-sivu
    deactivate server

    browser->>server: GET /main.css
    activate server
    server-->>browser: CSS-tiedosto
    deactivate server

    browser->>server: GET /main.js
    activate server
    server-->>browser: JavaScript-tiedosto
    deactivate server

    browser->>server: GET /data.json
    activate server
    server-->>browser: [{ "content": "Uusi muistiinpano", "date": "2024-11-27" }, ...]
    deactivate server

    Note right of browser: Selain renderöi päivitetyn muistiinpanolistan