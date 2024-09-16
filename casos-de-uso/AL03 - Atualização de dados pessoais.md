# AL04 - Atualização dos dados do Aluno

## Rotas

| Rota                            | Método | Descrição                         |
| ------------------------------- | ------ | --------------------------------- |
| /api/alunos                     | PUT    | Atualizar os dados de um aluno    |
| /api/alunos/foto                | POST   | Atualiza foto de perfil do aluno  |

## links para visualização das rotas:
➤ [PUT /api/alunos](#rota-put-api-alunos) </br>
➤ [POST /api/alunos/foto}](#rota-post-api-alunos-foto)

<a id="rota-put-api-alunos"></a>

## Rota PUT /api/alunos

### Requisição

**Query Parameters**

Não se aplica

**Headers**

| Campo         | Tipo   | Descrição       | Exemplo                                              |
| ------------- | ------ | --------------- | ---------------------------------------------------- |
| Authorization | string | Token de acesso | "Bearer 303Xs5g4co7glr4xtJHXHvbNI4Pl0y1hgyZZWOENHMx" |

**Body**

| Campo                 | Tipo   | Descrição                                  | Exemplo                   |
| --------------------- | ------ | -------------------------------------------| ------------------------- |
| email                 | string | Email do aluno                             | "joao@mail.com"           |
| nome                  | string | Nome do aluno                              | "João da Silva"           |
| password              | string | Senha do aluno                             | "@Password6"              |
| password_confirmation | string | Confirmação da senha do aluno              | "@Password6"              |

Regras de validação:

- `nome`: opcional, mínimo 3 caracteres, máximo 100 caracteres
- `email`: opcional, formato de email válido
- `password`: opcional, mínimo 8 caracteres, pelo menos um número, pelo menos um caracter especial(@, #, $, %, etc.).
- `password_confirmation`: opcional, mínimo 6 caracteres, pelo menos um número, pelo menos um caracter especial(@, #, $, %, etc.), deve ser igual ao campo password

### Resposta

**Status Code**

| Status Code | Descrição                        |
| ----------- | -------------------------------- |
| 201         | Aluno cadastrado com sucesso     |
| 400         | Erro de validação                |
| 401         | Token inválido                   |

**Body**

| Campo            | Tipo   | Descrição                                 | Exemplo                                             |
| ---------------- | ------ | ----------------------------------------- | -----------------------------------                 |
| id               | int    | ID                                        | 1                                                   |
| nome             | string | Nome do aluno                             | "João da Silva"                                     |
| email            | string | Email do aluno                            | "joao@mail.com                                      |
| foto_perfil      | string | Foto de perfil do aluno                   | "https://github.com/joao_silva.png"                 |
| created_at       | string | Data de criação                           | "2020-10-10T00:00:00.000Z"                          |
| updated_at       | string | Data de atualização                       | "2020-10-10T00:00:00.000Z"                          |

### Exemplos

**Requisição**

```
PUT /api/alunos HTTP/1.1
Host: localhost:3000
Content-Type: application/json
Accept: application/json
Authorization: Bearer 303Xs5g4co7glr4xtJHXHvbNI4Pl0y1hgyZZWOENHMx

{
  "nome": "Carlos Eduardo",
  "email": "carloscz@mail.com",
  "password": "@Senha123",
  "password_confirmation": "@Senha123",
}
```

**Resposta com sucesso**

```
HTTP/1.1 201 Created
Content-Type: application/json

{
	"id": 6,
	"nome": "Carlos Eduardo",
	"email": "carloscz@mail.com",
	"foto_perfil": null,
	"created_at": "2024-09-15T20:58:54.140266Z",
	"updated_at": "2024-09-15T20:58:54.140266Z"
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
      "e-mail já cadastrado"
    ],
    "password_confirmation": [
      "deve ser igual ao campo password"
    ]
  }
}
```

**Resposta com token inválido**

```
HTTP/1.1 401 Unauthorized
Content-Type: application/json

{
  "message": "Token expirado",
  "status": 401,
  "error": "Unauthorized",
  "cause": "TokenExpiredError"
}
```

<a id="rota-post-api-alunos-foto"></a>

## Rota POST /api/alunos/foto

### Requisição

**Query Parameters**

Não se aplica

**Headers**

| Campo         | Tipo   | Descrição       | Exemplo                                              |
| ------------- | ------ | --------------- | ---------------------------------------------------- |
| Authorization | string | Token de acesso | "Bearer 303Xs5g4co7glr4xtJHXHvbNI4Pl0y1hgyZZWOENHMx" |

**Body**

| Campo | Tipo   | Descrição                   | Exemplo |
| ----- | ------ | --------------------------- | ------- |
| foto  | binary | Foto de perfil do professor |         |

Regras de validação:

- `foto`: obrigatório, formato de imagem válido

### Resposta

**Status Code**

| Status Code | Descrição                         |
| ----------- | --------------------------------- |
| 200         | Atualização realizada com sucesso |
| 400         | Erro de validação                 |
| 401         | Token inválido                    |

**Body**

| Campo   | Tipo   | Descrição           | Exemplo                                 |
| ------- | ------ | ------------------- | --------------------------------------- |
| message | string | Mensagem de sucesso | "Foto de perfil atualizada com sucesso" |

### Exemplos

**Requisição**

```
POST /api/alunos/foto HTTP/1.1
Host: localhost:3000
Content-Type: multipart/form-data
Accept: application/json
Authorization: Bearer 303Xs5g4co7glr4xtJHXHvbNI4Pl0y1hgyZZWOENHMx

------WebKitFormBoundaryOqsbCkX4yVlUXiWO
Content-Disposition: form-data; name="foto"; filename="foto.jpg"
Content-Type: image/jpeg


------WebKitFormBoundaryOqsbCkX4yVlUXiWO--
```

**Resposta com sucesso**

```
HTTP/1.1 200 OK
Content-Type: application/json

{
  "message": "Foto de perfil atualizada com sucesso"
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
    "foto": [
      "Fazer upload de uma imagem válida. O arquivo enviado não é um arquivo de imagem ou está corrompido."
    ]
  }
}
```

**Resposta com token inválido**

```
HTTP/1.1 401 Unauthorized
Content-Type: application/json

{
  "message": "Token expirado",
  "status": 401,
  "error": "Unauthorized",
  "cause": "TokenExpiredError"
}
```