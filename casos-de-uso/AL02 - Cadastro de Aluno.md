# AL02 - Cadastro de Aluno

## Rotas

| Rota                            | Método | Descrição             |
| ------------------------------- | ------ | --------------------- |
| /api/alunos                     | POST   | Cadastrar um aluno    |

## Rota POST /api/alunos

### Requisição

**Query Parameters**

Não se aplica

**Headers**

Não se aplica

**Body**

| Campo                 | Tipo   | Descrição                                  | Exemplo                   |
| --------------------- | ------ | -------------------------------------------| ------------------------- |
| email                 | string | Email do aluno                             | "joao@mail.com"           |
| nome                  | string | Nome do aluno                              | "João da Silva"           |
| password              | string | Senha do aluno                             | "@Password6"              |
| password_confirmation | string | Confirmação da senha do aluno              | "@Password6"              |

Regras de validação:

- `nome`: obrigatório, mínimo 3 caracteres, máximo 100 caracteres
- `email`: obrigatório, formato de email válido
- `password`: obrigatório, mínimo 8 caracteres, pelo menos um número, pelo menos um caracter especial(@, #, $, %, etc.).
- `password_confirmation`: obrigatório, mínimo 6 caracteres, pelo menos um número, pelo menos um caracter especial(@, #, $, %, etc.), deve ser igual ao campo password

### Resposta

**Status Code**

| Status Code | Descrição                        |
| ----------- | -------------------------------- |
| 201         | Aluno cadastrado com sucesso     |
| 400         | Erro de validação                |

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

{
  "nome": "João da Silva",
  "email": "joao@mail.com",
  "password": "@P123456",
  "password_confirmation": "@P123456",
}
```

**Resposta com sucesso**

```
HTTP/1.1 201 Created
Content-Type: application/json

{
	"id": 6,
	"nome": "João da Silva",
	"email": "joao@mail.com",
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