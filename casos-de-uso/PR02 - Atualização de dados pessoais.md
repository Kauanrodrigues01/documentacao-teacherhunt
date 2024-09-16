# PR03 - Atualização de dados pessoais

## Rotas

| Rota                  | Método | Descrição                             |
| --------------------- | ------ | ------------------------------------- |
| /api/professores      | PUT    | Atualiza os dados do professor logado |
| /api/professores/foto | POST   | Atualiza a foto de um professor       |

## links para visualização das rotas:
➤ [PUT /api/professores](#rota-put-api-professores) </br>
➤ [POST /api/professores/foto](#rota-post-api-professores-foto)

<a id="rota-put-api-professores"></a>

## Rota PUT /api/professores

### Requisição

**Query Parameters**

Não se aplica

**Headers**

| Campo         | Tipo   | Descrição       | Exemplo                                              |
| ------------- | ------ | --------------- | ---------------------------------------------------- |
| Authorization | string | Token de acesso | "Bearer 303Xs5g4co7glr4xtJHXHvbNI4Pl0y1hgyZZWOENHMx" |

**Body**

| Campo                 | Tipo   | Descrição                                 | Exemplo                   |
| --------------------- | ------ | ----------------------------------------- | ------------------------- |
| nome                  | string | Nome do professor                         | "João da Silva"           |
| email                 | string | Email do professor                        | "joao@mail.com"           |
| idade                 | int    | Idade do professor                        | 30                        |
| descricao             | string | Descrição do professor                    | "Professor de matemática" |
| password              | string | Senha do professor                        | "123456"                  |
| password_confirmation | string | Confirmação da senha do professor         | "123456"                  |
| valor_aula            | float  | Valor da aula do professor                | 50.0                      |
| materias              | list   | Lista das materias relacionadas a um prof | [1, 4]                    |

Regras de validação:

- `nome`: opicional, mínimo 3 caracteres, máximo 100 caracteres
- `email`: opicional, formato de email válido
- `idade`: opicional, mínimo 18 anos, máximo 100 anos
- `descricao`: opicional, mínimo 10 caracteres, máximo 500 caracteres
- `password`: obrigatorio, mínimo 6 caracteres
- `password_confirmation`: obrigatorio, mínimo 6 caracteres, deve ser igual ao campo `password`
- `valor_aula`: opicional, mínimo 10.0, máximo 500.0
- `materias`: opicional, sem litimes de matérias, recebe os id's das matérias

### Resposta

**Status Code**

| Status Code | Descrição                         |
| ----------- | --------------------------------- |
| 200         | Atualização realizada com sucesso |
| 400         | Erro de validação                 |
| 401         | Token inválido                    |

**Body**

| Campo            | Tipo   | Descrição                                      | Exemplo                                                           |
| -----------      | ------ | --------------------------------------------   | ----------------------------------------------------------------- |
| id               | int    | ID                                             | 1                                                                 |
| nome             | string | Nome do professor                              | "João da Silva"                                                   |
| email            | string | Email do professor                             | "joao@mail.com                                                    |
| idade            | int    | Idade do professor                             | 30                                                                |
| descricao        | string | Descrição do professor                         | "Professor de matemática"                                         |
| valor_aula       | float  | Valor da aula do professor                     | 50.0                                                              |
| foto_perfil      | string | Foto de perfil do professor                    | "https://github.com/joao_silva.png"                               |
| materias         | list   | Lista das materias relacionadas a um prof      | [1, 4]                                                            |
| materias_objetos | list   | Lista das materias relacionadas a um prof      | [{"id": 1, "nome": "Matematica"}, {"id" "4": "nome: ""Física"}]   |
| created_at       | string | Data de criação                                | "2020-10-10T00:00:00.000Z"                                        |
| updated_at       | string | Data de atualização                            | "2020-10-10T00:00:00.000Z"                                        |

### Exemplos

**Requisição**

```
PUT /api/professores HTTP/1.1
Host: localhost:3000
Content-Type: application/json
Accept: application/json
Authorization: Bearer 303Xs5g4co7glr4xtJHXHvbNI4Pl0y1hgyZZWOENHMx

{
  "nome": "João da Silva",
  "email": "joao@mail.com",
  "idade": 30,
  "descricao": "Professor de matemática",
  "password": "123456",
  "password_confirmation": "123456",
  "valor_aula": 50.0
}
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
  "password": "123456",
  "password_confirmation": "123456",
  "valor_aula": 50.0,
  "foto_perfil": "https://github.com/joao_silva.png",
  "materias" : [1, 5],
  "materias_objetos": [
		{
			"id": 1,
			"nome": "Matemática"
		},
    {
      "id": 1,
			"nome": "Física"
    }
  ],
  "created_at": "2020-10-10T00:00:00.000Z",
  "updated_at": "2020-10-10T00:00:00.000Z"
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

<a id="rota-post-api-professores-foto"></a>

## Rota POST /api/professores/foto

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
POST /api/professores/foto HTTP/1.1
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
