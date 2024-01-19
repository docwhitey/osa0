sequenceDiagram
    participant browser
    participant server
    
    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
    Note right of server: 302 Found
    activate server
    server-->>browser: HTML Document - new_note
    deactivate server

    %%En ole varma pitäisikö POST aiheuttama redirect merkata vain niin, että palvelin palauttaa suoraan päivitetyn /notes.html selaimelle
    
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate server
    server-->>browser: HTML Document - notes
    deactivate server
    
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: CSS file
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server
    server-->>browser: JavaScript File
    deactivate server
    
    Note right of browser: Browser executes JavaScript file
    
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: [{ "content": "test", "date": "2024-01-19T11:02:47.982Z"} ... ]
    deactivate server    

    Note right of browser: The browser executes the callback function that renders the notes 