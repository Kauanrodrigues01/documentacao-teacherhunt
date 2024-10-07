# AL09 - Lista de Professores Favoritos

## Rotas

| Rota                                            | Método | Descrição                                        |
| ----------------------------------------------- | ------ | ------------------------------------------------ |
| /api/alunos/professores-favoritos               | GET    | Lista os professores favoritos de um aluno       |
| /api/alunos/professores-favoritos/{professor_id}| POST   | Adiciona um professor a lista de favoritos       |
| /api/alunos/professores-favoritos/{professor_id}| DELETE | Remove um professor a lista de favoritos         |

## links para visualização das rotas:
➤ [GET /api/alunos/professores-favoritos](#rota-get-alunos-professores-favoritos) </br>
➤ [POST /api/alunos/professores-favoritos/{professor_id}](#rota-post-api-alunos-professores-favoritos) </br>
➤ [DELETE /api/alunos/professores-favoritos/{professor_id}](#rota-delete-api-alunos-professores-favoritos)

<a id="rota-get-alunos-professores-favoritos"></a>

## Rota GET /api/alunos/professores-favoritos

### Requisição

**Query Parameters**

Não se aplica

**Headers**

| Campo         | Tipo   | Descrição       | Exemplo                                              |
| ------------- | ------ | --------------- | ---------------------------------------------------- |
| Authorization | string | Token de acesso | "Bearer 303Xs5g4co7glr4xtJHXHvbNI4Pl0y1hgyZZWOENHMx" |

**Body**

Não se Aplica

### Resposta

**Status Code**

| Status Code | Descrição                        |
| ----------- | -------------------------------- |
| 200         | Professores favoritos retornados |
| 401         | Token inválido                   |

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
GET /api/alunos/professores-favoritos HTTP/1.1
Host: localhost:3000
Content-Type: application/json
Accept: application/json
Authorization: Bearer 303Xs5g4co7glr4xtJHXHvbNI4Pl0y1hgyZZWOENHMx
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

**Resposta se naõ tiverem professores favoritados**

```
HTTP/1.1 404 Not Found
Content-Type: application/json

{
	"message": "Nenhum professor favorito encontrado."
}
```

<a id="rota-post-api-alunos-professores-favoritos"></a>

## Rota POST /api/alunos/professores-favoritos/{professor_id}

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

| Status Code | Descrição                         |
| ----------- | --------------------------------- |
| 200         | Aula retornada com sucesso        |
| 401         | Token inválido                    |

**Body**

{
	"message": "Professor adicionado aos favoritos."
}

### Exemplos

**Requisição**

```
POST /api/alunos/professores-favoritos/1 HTTP/1.1
Host: localhost:3000
Content-Type: multipart/form-data
Accept: application/json
Authorization: Bearer 303Xs5g4co7glr4xtJHXHvbNI4Pl0y1hgyZZWOENHMx
```

**Resposta com sucesso**

```
HTTP/1.1 200 OK
Content-Type: application/json


{
	"message": "Professor adicionado aos favoritos."
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

**Resposta se o professor não for encontrado**

```
HTTP/1.1 404 Not Found
Content-Type: application/json

{
	"message": "Professor não encontrado."
}
```

<a id="rota-delete-api-alunos-professores-favoritos"></a>

## Rota DELETE /api/alunos/professores-favoritos/{professor_id}

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

| Status Code | Descrição                         |
| ----------- | --------------------------------- |
| 200         | Aula retornada com sucesso        |
| 401         | Token inválido                    |

**Body**

{
	"message": "Professor removido aos favoritos."
}

### Exemplos

**Requisição**

```
DELETE /api/alunos/professores-favoritos/1 HTTP/1.1
Host: localhost:3000
Content-Type: multipart/form-data
Accept: application/json
Authorization: Bearer 303Xs5g4co7glr4xtJHXHvbNI4Pl0y1hgyZZWOENHMx
```

**Resposta com sucesso**

```
HTTP/1.1 200 OK
Content-Type: application/json


{
	"message": "Professor removido aos favoritos."
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

**Resposta se o professor não for encontrado**

```
HTTP/1.1 404 Not Found
Content-Type: application/json

{
	"message": "Professor não encontrado."
}
```

**Resposta se o professor não estiver na lista de favoritos**

```
HTTP/1.1 404 Not Found
Content-Type: application/json

{
	"message": "Professor não está na lista de favoritos."
}
```