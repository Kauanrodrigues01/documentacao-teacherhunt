# PR01 - Cadastro de professor

Abaixo você encontrará todas as informações necessárias para a implementação do caso de uso **Cadastro de professor**.

## Rotas

| Rota             | Método | Descrição             |
| ---------------- | ------ | --------------------- |
| /api/professores | POST   | Cadastra um professor |

## Rota POST /api/professores

### Requisição

**Query Parameters**

Não se aplica

**Headers**

Não se aplica

**Body**

| Campo                 | Tipo   | Descrição                                  | Exemplo                   |
| --------------------- | ------ | -------------------------------------------| ------------------------- |
| nome                  | string | Nome do professor                          | "João da Silva"           |
| email                 | string | Email do professor                         | "joao@mail.com"           |
| idade                 | int    | Idade do professor                         | 30                        |
| descricao             | string | Descrição do professor                     | "Professor de matemática" |
| password              | string | Senha do professor                         | "@Password6"              |
| password_confirmation | string | Confirmação da senha do professor          | "@Password6"              |
| valor_hora            | float  | Valor da aula do professor                 | 50.0                      |
| materias              | List   | Id's das materias relacionadas a um prof   | [1, 23]                   |

Regras de validação:

- `nome`: obrigatório, mínimo 3 caracteres, máximo 100 caracteres
- `email`: obrigatório, formato de email válido
- `idade`: obrigatório, mínimo 18 anos, máximo 100 anos
- `descricao`: obrigatório, mínimo 10 caracteres, máximo 500 caracteres
- `password`: obrigatório, mínimo 8 caracteres, pelo menos um número, pelo menos um caracter especial(@, #, $, %, etc.).
- `password_confirmation`: obrigatório, mínimo 6 caracteres, pelo menos um número, pelo menos um caracter especial(@, #, $, %, etc.), deve ser igual ao campo password
- `valor_hora`: obrigatório, mínimo 10.0, máximo 500.0
- `materias`: obrigatório, não tem mínimo e nem máximo de matérias que podem ser associadas a um professor

### Resposta

**Status Code**

| Status Code | Descrição                        |
| ----------- | -------------------------------- |
| 201         | Professor cadastrado com sucesso |
| 400         | Erro de validação                |

**Body**

| Campo            | Tipo   | Descrição                                 | Exemplo                                             |
| ---------------- | ------ | ----------------------------------------- | -----------------------------------                 |
| id               | int    | ID                                        | 1                                                   |
| nome             | string | Nome do professor                         | "João da Silva"                                     |
| email            | string | Email do professor                        | "joao@mail.com                                      |
| idade            | int    | Idade do professor                        | 30                                                  |
| descricao        | string | Descrição do professor                    | "Professor de matemática"                           |
| valor_hora       | float  | Valor da aula do professor                | 50.0                                                |
| foto_perfil      | string | Foto de perfil do professor               | "https://github.com/joao_silva.png"                 |
| materias         | list   | Lista das materias relacionadas a um prof | [1, 4]                                              |
| materias_objetos | list   | Lista das materias relacionadas a um prof | [{"id": 1, "nome": "Matematica"}, {"id": "Física"}] |
| created_at       | string | Data de criação                           | "2020-10-10T00:00:00.000Z"                          |
| updated_at       | string | Data de atualização                       | "2020-10-10T00:00:00.000Z"                          |

### Exemplos

**Requisição**

```
POST /api/professores HTTP/1.1
Host: localhost:3000
Content-Type: application/json
Accept: application/json

{
  "nome": "João da Silva",
  "email": "joao@mail.com",
  "idade": 30,
  "descricao": "Professor de matemática",
  "password": "@P123456",
  "password_confirmation": "@P123456",
  "valor_hora": 50.0,
  "materias": [1, 2]
}
```

**Resposta com sucesso**

```
HTTP/1.1 201 Created
Content-Type: application/json

{
  "nome": "João da Silva",
  "email": "joao@mail.com",
  "idade": 30,
  "descricao": "Professor de matemática",
  "password": "123456",
  "password_confirmation": "123456",
  "valor_hora": 50.0,
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