---
title: Biblioteca Open API
updated: 2018-12-28 17:00
---

### Endpoints
#### Prefisso: _/v1/library/_

URL | Metodo | Descrizione
--- | --- | ---
[/books](#books_get) | GET | Lista dei libri
[/books](#books_post) | POST | Nuovo libro

<div id="books_get"></div>

### GET /books
#### Lista dei libri
Header
```
Authorization: Bearer ...
Accept: application/json
```
Response di esempio
```json
{
  "success": true,
  "can": {
    "create": true,
    "edit": true,
    "delete": false
  },
  "books": {
    "current_page": 1,
    "data": [
      {
        "id": 1,
        "category_id": 1,
        "title": "Datacrazia. Politica, cultura algoritmica e conflitti al tempo dei big data",
        "author": "D. Gambetta",
        "isbn": "978-8894830149",
        "publishedDate": "2018",
        "created_at": "2018-11-04 11:41:20",
        "updated_at": "2018-11-04 14:22:55",
        "category": {
          "id": 1,
          "name": "Società"
        }
      }
    ],
    "first_page_url": "https:\/\/spaz.test\/v1\/library\/books?page=1",
    "from": 1,
    "last_page": 24,
    "last_page_url": "https:\/\/spaz.test\/v1\/library\/books?page=24",
    "next_page_url": "https:\/\/spaz.test\/v1\/library\/books?page=2",
    "path": "https:\/\/spaz.test\/v1\/library\/books",
    "per_page": 20,
    "prev_page_url": null,
    "to": 20,
    "total": 463
  }
}
```

<div class="divider"></div>

<div id="books_post"></div>

### POST /books
#### Creazione nuovo libro
##### _il permesso library.create è necessario_
Header
```
Authorization: Bearer ...
Accept: application/json
```

Body
```
isbn : valid isbn
category_id : valid category ID
title : book title
author : book author
publishedDate : book published date
```

Response di esempio
```json
{
  "success": true //Libro creato
}
```
oppure
```json
{
  "message": "The given data was invalid.", 
  //Errore nella validazione del body
  "errors": {
    "isbn": [
      "isbn è stato già utilizzato."
    ]
  }
}
```
