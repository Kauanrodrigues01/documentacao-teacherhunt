# USER02 - Listar Máterias

## Rotas

| Rota                            | Método | Descrição             |
| ------------------------------- | ------ | --------------------- |
| /api/materias                   | GET    | Listagem de materias  |

## Rota GET /api/materias

### Requisição

**Query Parameters**

| Nome   | Tipo   | Descrição                         | Exemplo    |
| ------ | ------ | --------------------------------- | ---------- |
| nome   | string | Busca pelo nome da materia        | matematica |

**Headers**

Não se aplica

**Body**

Não se aplica

### Resposta

**Status Code**

| Status Code | Descrição                        |
| ----------- | -------------------------------- |
| 200         | Listagem de materias com sucesso |

**Body**

Não se aplica

### Exemplos

**Requisição**

```
GET /api/materias HTTP/1.1
Host: localhost:3000
Content-Type: application/json
Accept: application/json
```

**Resposta com sucesso**

```
HTTP/1.1 200 OK
Content-Type: application/json

[
	{
		"id": 1,
		"nome": "Matemática"
	},
	{
		"id": 2,
		"nome": "Química"
	},
	{
		"id": 3,
		"nome": "Programação Web"
	},
	{
		"id": 4,
		"nome": "Física"
	}
]
```
