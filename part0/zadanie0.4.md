```mermaid
sequenceDiagram
participant browser
participant server

Note right of browser: User writes a note into the text field and clicks Save

browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
activate server

Note right of server: Server reads the note from req.body
Note right of server: Server adds the new note to the notes array

server-->>browser: HTTP 302 Redirect
deactivate server
Note right of browser: Browser follows the redirect

browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
 activate server
    erver-->>browser: HTML document
deactivate server

browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
activate server
server-->>browser: CSS file
deactivate server

browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
activate server
    server-->>browser: JavaScript file
    deactivate server

    Note right of browser: Browser executes main.js

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: JSON data containing the notes, including the new note
    deactivate server

    Note right of browser: Browser executes the callback function
    Note right of browser: DOM is updated and the notes are displayed
