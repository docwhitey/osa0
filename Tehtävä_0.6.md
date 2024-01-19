sequenceDiagram
    participant browser
    participant server

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa
    Note right of browser: assumed that all parts from 0.5 sequence diagram have been executed
    activate server
    Note right of server: 201 Created
    server-->>browser: Application JSON - new note created and readable without refresh
    deactivate server
