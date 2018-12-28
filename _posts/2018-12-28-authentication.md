---
title: Autenticazione sulle API
updated: 2018-12-28 16:00
---
### Autenticazione
#### Per eseguire qualsiasi operazione tramite API è necessario eseguire l'autenticazione per ottenere il token di riferimento
#### Prefisso: _/v1/auth/_

URL | Metodo | Descrizione
--- | --- | ---
[/login](#login) | POST | Login su account per ottenere token
[/refresh](#refresh) | POST | Rigenerazione token se scaduto
[/me](#me) | POST | Informazioni account connesso

<div id="login"></div>

### POST /login
#### Login su account
Header
```
Accept: application/json
```
Body
```
 - email
 - password 
```
Response di esempio
```json
{
  "access_token": "******", //Encrypted token
  "expires_in": 3600,
  "name": "Michelangelo",
  "surname": "Morrillo"
}
```

<div id="refresh"></div>

### POST /refresh
#### Rigenerazione token se scaduto
Header
```
Authorization: Bearer ...

Accept: application/json
```
Response di esempio
```json
{
  "access_token": "******", //NEW encrypted token
  "expires_in": 3600,
  "name": "Michelangelo",
  "surname": "Morrillo"
}
```

<div id="me"></div>

### POST /me
#### Informazioni account connesso
Header
```
Authorization: Bearer ...

Accept: application/json
```
Response di esempio
```json
{
  "id": "******",
  "name": "Michelangelo",
  "surname": "Morrillo",
  "email": "******",
  "email_verified_at": null,
  "gender": 0,
  "created_at": "2018-11-03 17:32:05",
  "updated_at": "2018-11-19 19:47:39",
  "telephone": "******"
}
```