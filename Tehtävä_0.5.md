sequenceDiagram
    participant browser
    participant server
    
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa
    activate server
    server-->>browser: HTML document - spa
    deactivate server
    
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: CSS file
    deactivate server
    
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa.js
    activate server
    server-->>browser: JavaScipt File - spa.js
    deactivate server
    
    Note right of browser: Browser executes JavaScript file
    
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: [{ "content": "jjofdjopfdopjfsdjopopjfd", "date": "2024-01-19T11:31:57.948Z"}, ... ]
    deactivate server    

    Note right of browser: The browser executes the callback function that renders the notes 