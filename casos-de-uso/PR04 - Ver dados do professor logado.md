# AL04 - Ver dados do professor logado

## Rotas

| Rota                            | Método | Descrição                        |
| ------------------------------- | ------ | -------------------------------- |
| /api/professores/me             | GET    | Ver dados do professor logado    |

## Rota GET /api/professores/me

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
GET /api/professores/me HTTP/1.1
Host: localhost:3000
Content-Type: application/json
Accept: application/json
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