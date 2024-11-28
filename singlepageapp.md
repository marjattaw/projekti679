sequenceDiagram
    participant browser as Selain
    participant server as Palvelin

    browser->>server: GET /spa
    activate server
    server-->>browser: HTML-dokumentti
    deactivate server

    browser->>server: GET /main.css
    activate server
    server-->>browser: CSS-tiedosto
    deactivate server

    browser->>server: GET /spa.js
    activate server
    server-->>browser: JavaScript-tiedosto
    deactivate server

    Note right of browser: Selain suorittaa spa.js-tiedoston<br>ja alustaa SPA:n käyttöliittymän

    browser->>server: GET /data.json
    activate server
    server-->>browser: [{ "content": "Muistiinpano 1", "date": "2024-11-01" }, ...]
    deactivate server

    Note right of browser: Selain renderöi muistiinpanot käyttöliittymään
