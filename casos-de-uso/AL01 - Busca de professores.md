# AL01 - Busca de professores

## Rotas

| Rota                                   | Método | Descrição                        |
| -------------------------------------- | ------ | -------------------------------- |
| /api/professores                       | GET    | Lista os professores             | 
| /api/professores/{professor_id}        | GET    | Detalhes do professor            |
| /api/professores/{materia_id}/materias | GET    | Lista os professores por matéria |

## links para visualização das rotas:
➤ [GET /api/professores](#rota-get-api-professores) </br>
➤ [GET /api/professores/{professor_id}](#rota-get-api-professores-professor-id) </br>
➤ [GET /api/professores/{materia_id}/materias](#rota-get-professores-por-materia)

<a id="rota-get-api-professores"></a>
## Rota GET /api/professores

### Requisição

**Query Parameters**

| Nome            | Tipo   | Descrição                              | Exemplo    |
| --------------- | ------ | -------------------------------------- | ---------- |
| q               | string | Busca pela descrição do professor      | Matemática |
| avaliacao_min   | float  | Busca um professor pela avaliação min  | 2.5        |
| preco_max       | float  | Busca um professor peo valor hora max  | 77.0       |

Regras de validação:

- `q`: opcional, deve ter no mínimo 3 caracteres, máximo 100 caracteres
- `avaliacao_min`: opcional, deve ser um número 
- `preco_max`: opcional, deve ser um número

**Headers**

Não se aplica

**Body**

Não se aplica

### Resposta

**Status Code**

| Status Code | Descrição                   |
| ----------- | --------------------------- |
| 200         | Busca realizada com sucesso |

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
| avaliacao        | float  | Avaliação de um professor                 | 2.5                                                 |
| materias         | list   | Lista das materias relacionadas a um prof | [1, 4]                                              |
| materias_objetos | list   | Lista das materias relacionadas a um prof | [{"id": 1, "nome": "Matematica"}, {"id": "Física"}] |
| created_at       | string | Data de criação                           | "2020-10-10T00:00:00.000Z"                          |
| updated_at       | string | Data de atualização                       | "2020-10-10T00:00:00.000Z"                          |

### Exemplos

**Requisição**

```
GET /api/professores HTTP/1.1
Host: localhost:3000
Accept: application/json
```

**Resposta com sucesso**

```
HTTP/1.1 200 OK
Content-Type: application/json

[
	{
		"id": 3,
		"nome": "João Carlos",
		"email": "testeddddd@example.scom",
		"idade": 40,
		"descricao": "Um professor que ensinou Matemática na UECE",
		"valor_hora": 10.0,
		"foto_perfil": null,
		"avaliacao": 3.0,
		"materias": [
			1
		],
		"materias_objetos": [
			{
				"id": 1,
				"nome": "Matemática"
			}
		],
		"create_at": "2024-09-15T20:08:28.404638Z",
		"update_at": "2024-09-15T20:08:28.404692Z"
	},
	{
		"id": 2,
		"nome": "Felix Ferreira",
		"email": "teste@example.com",
		"idade": 40,
		"descricao": "Um professor que ensinou Física no IFCE",
		"valor_hora": 60.0,
		"foto_perfil": null,
		"materias": [
			4
		],
		"materias_objetos": [
			{
				"id": 4,
				"nome": "Física"
			}
		],
		"create_at": "2024-09-14T14:32:20.416581Z",
		"update_at": "2024-09-14T14:32:20.416581Z"
	},
]
```
<a id="rota-get-api-professores-professor-id"></a>
## Rota GET /api/professores/{professor_id}

### Requisição

**Query Parameters**

Não se aplica

**Headers**

Não se aplica

**Body**

Não se aplica

### Resposta

**Status Code**

| Status Code | Descrição                   |
| ----------- | --------------------------- |
| 200         | Busca realizada com sucesso |
| 404         | Professor não encontrado    |

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
| avaliacao        | float  | Avaliação de um professor                 | 2.5                                                 |
| materias         | list   | Lista das materias relacionadas a um prof | [1, 4]                                              |
| materias_objetos | list   | Lista das materias relacionadas a um prof | [{"id": 1, "nome": "Matematica"}, {"id": "Física"}] |
| created_at       | string | Data de criação                           | "2020-10-10T00:00:00.000Z"                          |
| updated_at       | string | Data de atualização                       | "2020-10-10T00:00:00.000Z"                          |


### Exemplos

**Requisição**

```
GET /api/professores/1 HTTP/1.1
Host: localhost:3000
Accept: application/json
```

**Resposta com sucesso**

```
HTTP/1.1 200 OK
Content-Type: application/json

{
  "id": 1,
  "nome": "João Carlos",
  "email": "testeddddd@example.scom",
  "idade": 40,
  "descricao": "Um professor que ensinou Matemática na UECE",
  "valor_hora": 10.0,
  "foto_perfil": null,
  "avaliacao": 4.5,
  "materias": [
    1
  ],
  "materias_objetos": [
    {
      "id": 1,
      "nome": "Matemática"
    }
  ],
  "create_at": "2024-09-15T20:08:28.404638Z",
  "update_at": "2024-09-15T20:08:28.404692Z"
}
```

**Resposta com professor não encontrado**

```
HTTP/1.1 404 Not Found
Content-Type: application/json

{
  "message": "Professor não encontrado",
  "status": 404,
  "error": "Not Found",
  "cause": "NotFoundError"
}
```

<a id="rota-get-professores-por-materia"></a>
## Rota GET /api/professores/{materia_id}/materias

### Requisição

**Query Parameters**

Não se aplica

**Headers**

Não se aplica

**Body**

Não se aplica

### Resposta

**Status Code**

| Status Code | Descrição                   |
| ----------- | --------------------------- |
| 200         | Busca realizada com sucesso |

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
| avaliacao        | float  | Avaliação de um professor                 | 2.5                                                 |
| materias         | list   | Lista das materias relacionadas a um prof | [1, 4]                                              |
| materias_objetos | list   | Lista das materias relacionadas a um prof | [{"id": 1, "nome": "Matematica"}, {"id": "Física"}] |
| created_at       | string | Data de criação                           | "2020-10-10T00:00:00.000Z"                          |
| updated_at       | string | Data de atualização                       | "2020-10-10T00:00:00.000Z"                          |

### Exemplos

**Requisição**

```
GET /api/professores/1/materias HTTP/1.1
Host: localhost:3000
Accept: application/json
```

**Resposta com sucesso**

```
HTTP/1.1 200 OK
Content-Type: application/json

[
	{
		"id": 3,
		"nome": "João Carlos",
		"email": "testeddddd@example.com",
		"idade": 40,
		"descricao": "Um professor que ensinou Matemática na UECE",
		"valor_hora": 10.0,
		"foto_perfil": null,
		"avaliacao": 1.6,
		"materias": [
			1
		],
		"materias_objetos": [
			{
				"id": 1,
				"nome": "Matemática"
			}
		],
		"create_at": "2024-09-15T20:08:28.404638Z",
		"update_at": "2024-09-15T20:08:28.404692Z"
	},
	{
		"id": 2,
		"nome": "Felix Ferreira",
		"email": "teste@example.com",
		"idade": 40,
		"descricao": "Um professor que ensinou Física no IFCE",
		"valor_hora": 60.0,
		"foto_perfil": null,
		"avaliacao": 4.3,
		"materias": [
			1,
			4
		],
		"materias_objetos": [
			{
				"id": 1,
				"nome": "Matemática"
			},
			{
				"id": 4,
				"nome": "Física"
			}
		],
		"create_at": "2024-09-14T14:32:20.416581Z",
		"update_at": "2024-09-14T14:32:20.416581Z"
	},
]
```