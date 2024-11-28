sequenceDiagram
    participant user as Käyttäjä
    participant browser as Selain
    participant server as Palvelin

    Note over user: Käyttäjä kirjoittaa tekstikenttään<br>ja painaa "Tallenna"-nappia.
    
    user->>browser: Syöttää tiedot käyttöliittymään
    browser->>browser: Lisää uusi muistiinpano käyttöliittymän muistiinpanojen listaan

    browser->>server: POST /new_note_spa
    activate server
    Note right of server: Palvelin tallentaa uuden muistiinpanon<br>esim. { "content": "Uusi muistiinpano", "date": "2024-11-27" }
    server-->>browser: HTTP 201 Created (vahvistus)
    deactivate server

    Note right of browser: Selain päivittää muistiinpanot ilman sivun uudelleenlatausta
