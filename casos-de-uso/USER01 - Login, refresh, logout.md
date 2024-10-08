# PR02 - Login, refresh, logout de um aluno ou professor

## Rotas

| Rota              | Método | Descrição                          |
| ----------------- | ------ | ---------------------------------- |
| /api/auth/login   | POST   | Faz login                          |
| /api/auth/refresh | POST   | Atualiza o token de acesso         |
| /api/auth/logout  | POST   | Faz logout                         |

## links para visualização das rotas:
➤ [POST /api/auth/login](#rota-post-api-auth-login) </br>
➤ [POST /api/auth/refresh](#rota-post-api-auth-refresh) </br>
➤ [POST /api/auth/logout](#rota-post-api-auth-logout) </br>

<a id="rota-post-api-auth-login"></a>

## Rota POST /api/auth/login

### Requisição

**Query Parameters**

Não se aplica

**Headers**

Não se aplica

**Body**

| Campo    | Tipo   | Descrição        | Exemplo         |
| -------- | ------ | ---------------- | --------------- |
| email    | string | Email do usuário | "joao@mail.com" |
| password | string | Senha do usuário | "123456"        |

Regras de validação:

- `email`: obrigatório, formato de email válido
- `password`: obrigatório, mínimo 6 caracteres, máximo 20 caracteres

### Resposta

**Status Code**

| Status Code | Descrição                   |
| ----------- | --------------------------- |
| 200         | Login realizado com sucesso |
| 400         | Erro de validação           |
| 401         | Credenciais inválidas       |

**Body**

| Campo         | Tipo   | Descrição        | Exemplo                                       |
| ------------- | ------ | ---------------- | --------------------------------------------- |
| token         | string | Token de acesso  | "303Xs5g4co7glr4xtJHXHvbNI4Pl0y1hgyZZWOENHMx" |
| refresh_token | string | Token de refresh | "303Xs5g4co7glr4xtJHXHvbNI4Pl0y1hgyZZWOENHMx" |

### Exemplos

**Requisição**

```
POST /api/auth/login HTTP/1.1
Host: localhost:3000
Content-Type: application/json
Accept: application/json

{
  "email": "joao@mail.com",
  "password": "123456"
}
```

**Resposta com sucesso**

```
HTTP/1.1 200 OK
Content-Type: application/json

{
  "token": "303Xs5g4co7glr4xtJHXHvbNI4Pl0y1hgyZZWOENHMx",
  "refresh_token": "303Xs5g4co7glr4xtJHXHvbNI4Pl0y1hgyZZWOENHMx"
}
```

**Resposta com erro de validação**

```
HTTP/1.1 400 Bad Request
Content-Type: application/json

{
  "message": "Validation fails",
  "status": 400,
  "error": "Bad Request",
  "cause": "ValidationError",
  "errors": {
    "email": [
      "é obrigatório"
    ],
    "password": [
      "deve ter no mínimo 6 caracteres"
    ]
  }
}
```

**Resposta com credenciais inválidas**

```
HTTP/1.1 401 Unauthorized
Content-Type: application/json

{
  "message": "Credenciais inválidas",
  "status": 401,
  "error": "Unauthorized",
  "cause": "InvalidCredentialsError"
}
```
<a id="rota-post-api-auth-refresh"></a>

## Rota POST /api/auth/refresh

### Requisição

**Query Parameters**

Não se aplica

**Headers**

Não se aplica

**Body**

| Campo         | Tipo   | Descrição        | Exemplo                                       |
| ------------- | ------ | ---------------- | --------------------------------------------- |
| refresh_token | string | Token de refresh | "303Xs5g4co7glr4xtJHXHvbNI4Pl0y1hgyZZWOENHMx" |

Regras de validação:

- `refresh_token`: obrigatório

### Resposta

**Status Code**

| Status Code | Descrição                   |
| ----------- | --------------------------- |
| 200         | Login realizado com sucesso |
| 400         | Erro de validação           |
| 401         | Token inválido              |

**Body**

| Campo         | Tipo   | Descrição        | Exemplo                                       |
| ------------- | ------ | ---------------- | --------------------------------------------- |
| token         | string | Token de acesso  | "303Xs5g4co7glr4xtJHXHvbNI4Pl0y1hgyZZWOENHMx" |
| refresh_token | string | Token de refresh | "303Xs5g4co7glr4xtJHXHvbNI4Pl0y1hgyZZWOENHMx" |

### Exemplos

**Requisição**

```
POST /api/auth/refresh HTTP/1.1
Host: localhost:3000
Content-Type: application/json
Accept: application/json

{
  "refresh_token": "303Xs5g4co7glr4xtJHXHvbNI4Pl0y1hgyZZWOENHMx"
}
```

**Resposta com sucesso**

```
HTTP/1.1 200 OK
Content-Type: application/json

{
  "token": "303Xs5g4co7glr4xtJHXHvbNI4Pl0y1hgyZZWOENHMx",
  "refresh_token": "303Xs5g4co7glr4xtJHXHvbNI4Pl0y1hgyZZWOENHMx"
}
```

**Resposta com erro de validação**

```
HTTP/1.1 400 Bad Request
Content-Type: application/json

{
  "message": "Validation fails",
  "status": 400,
  "error": "Bad Request",
  "cause": "ValidationError",
  "errors": {
    "refresh_token": [
      "é obrigatório"
    ]
  }
}
```

**Resposta com token inválido**

```
HTTP/1.1 401 Unauthorized
Content-Type: application/json

{
  "message": "Token inválido",
  "status": 401,
  "error": "Unauthorized",
  "cause": "InvalidTokenError"
}
```

<a id="rota-post-api-auth-logout"></a>

## Rota POST /api/auth/logout

### Requisição

**Query Parameters**

Não se aplica

**Headers**

| Campo         | Tipo   | Descrição       | Exemplo                                              |
| ------------- | ------ | --------------- | ---------------------------------------------------- |
| Authorization | string | Token de acesso | "Bearer 303Xs5g4co7glr4xtJHXHvbNI4Pl0y1hgyZZWOENHMx" |

**Body**

| Campo         | Tipo   | Descrição        | Exemplo                                       |
| ------------- | ------ | ---------------- | --------------------------------------------- |
| refresh_token | string | Token de refresh | "303Xs5g4co7glr4xtJHXHvbNI4Pl0y1hgyZZWOENHMx" |

Regras de validação:

- `refresh_token`: obrigatório

### Resposta

**Status Code**

| Status Code | Descrição                    |
| ----------- | ---------------------------- |
| 205         | Logout realizado com sucesso |
| 400         | Erro de validação            |
| 401         | Token inválido               |

**Body**

Não se aplica

### Exemplos

**Requisição**

```
POST /api/auth/logout HTTP/1.1
Host: localhost:3000
Content-Type: application/json
Accept: application/json
Authorization: Bearer 303Xs5g4co7glr4xtJHXHvbNI4Pl0y1hgyZZWOENHMx

{
  "refresh_token": "303Xs5g4co7glr4xtJHXHvbNI4Pl0y1hgyZZWOENHMx"
}
```

**Resposta com sucesso**

```
HTTP/1.1 205 OK
Content-Type: application/json
```

**Resposta com erro de validação**

```
HTTP/1.1 400 Bad Request
Content-Type: application/json

{
  "message": "Validation fails",
  "status": 400,
  "error": "Bad Request",
  "cause": "ValidationError",
  "errors": {
    "refresh_token": [
      "é obrigatório"
    ]
  }
}
```

**Resposta com token inválido**

```
HTTP/1.1 401 Unauthorized
Content-Type: application/json

{
  "message": "Token inválido",
  "status": 401,
  "error": "Unauthorized",
  "cause": "InvalidTokenError"
}
```

## Rota GET /api/me

### Requisição

**Query Parameters**

Não se aplica

**Headers**

| Campo         | Tipo   | Descrição       | Exemplo                                              |
| ------------- | ------ | --------------- | ---------------------------------------------------- |
| Authorization | string | Token de acesso | "Bearer 303Xs5g4co7glr4xtJHXHvbNI4Pl0y1hgyZZWOENHMx" |

**Body**

Não se aplica

### Resposta

**Status Code**

| Status Code | Descrição                   |
| ----------- | --------------------------- |
| 200         | Dados do usuário retornados |
| 401         | Token inválido              |

**Body**

| Campo       | Tipo   | Descrição                   | Exemplo                             |
| ----------- | ------ | --------------------------- | ----------------------------------- |
| id          | int    | ID do professor             | 1                                   |
| nome        | string | Nome do professor           | "João da Silva"                     |
| email       | string | Email do professor          | "joao@mail.com                      |
| idade       | int    | Idade do professor          | 30                                  |
| descricao   | string | Descrição do professor      | "Professor de matemática"           |
| valor_aula  | float  | Valor da aula do professor  | 50.0                                |
| foto_perfil | string | Foto de perfil do professor | "https://github.com/joao_silva.png" |
| created_at  | string | Data de criação             | "2020-10-10T00:00:00.000Z"          |
| updated_at  | string | Data de atualização         | "2020-10-10T00:00:00.000Z"          |

### Exemplos

**Requisição**

```
GET /api/me HTTP/1.1
Host: localhost:3000
Accept: application/json
Authorization: Bearer 303Xs5g4co7glr4xtJHXHvbNI4Pl0y1hgyZZWOENHMx
```

**Resposta com sucesso**

```
HTTP/1.1 200 OK
Content-Type: application/json

{
  "nome": "João da Silva",
  "email": "joao@mail.com",
  "idade": 30,
  "descricao": "Professor de matemática",
  "valor_aula": 50.0,
  "foto_perfil": "https://github.com/joao_silva.png",
  "created_at": "2020-10-10T00:00:00.000Z",
  "updated_at": "2020-10-10T00:00:00.000Z"
}
```

**Resposta com token inválido**

```
HTTP/1.1 401 Unauthorized
Content-Type: application/json

{
  "message": "Token inválido",
  "status": 401,
  "error": "Unauthorized",
  "cause": "InvalidTokenError"
}
```
