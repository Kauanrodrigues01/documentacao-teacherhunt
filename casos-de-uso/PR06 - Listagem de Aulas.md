# PR04 - Listagem de Aulas

## Rotas

| Rota                            | Método | Descrição                                         |
| ------------------------------  | ------ | ------------------------------------------------- |
| /api/professores/aulas          | GET    | Lista as solicitações de aula do professor logado |
| /api/professores/aulas/{aula_id}| GET    | Detalhes de solitação de aula                     |

## links para visualização das rotas:
➤ [GET /api/professores/aulas](#rota-get-api-professores-aulas) </br>
➤ [GET /api/professores/aulas/{aula_id}](#rota-get-api-professores-aulas-aula-id)

<a id="rota-get-api-professores-aulas"></a>
## Rota GET /api/professores/aulas

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

| Status Code | Descrição                      |
| ----------- | ------------------------------ |
| 200         | Listagem realizada com sucesso |
| 401         | Token inválido                 |

**Body**

| Campo              | Tipo   | Descrição           | Exemplo                    |
| ----------------   | ------ | ------------------- | -------------------------- |
| id                 | int    | ID da aula          | 1                          |
| aluno              | int    | ID do aluno         | 2                          |
| professor          | int    | ID do professor     | 1                          |
| nome_aluno         | string | Nome do aluno       | 'Carlos Souza'             |
| nome_professor     | int    | Nome do professor   | 'João Silva'               |
| dia_da_aula        | string | Data da aula        | "16/09/2024"               |
| horario_de_inicio  | string | Hórario de inicio   | "14:00:00"                 |
| horario_de_termino | string | Hórario de termino  | "15:00:00"                 |
| numero_de_horas    | int    | duração da aua      | 1                          |
| preco              | float  | preco da aula       | 60.00                      |
| status             | string | status da aula      | "Pendente"                 |
| descricao_da_aula  | string | descricao da aula   | "Aula de função afim"      |
| created_at         | string | Data de criação     | "2020-10-10T10:00:00.000Z" |
| updated_at         | string | Data de atualização | "2020-10-10T10:00:00.000Z" |

### Exemplos

**Requisição**

```
GET /api/professores/aulas HTTP/1.1
Host: localhost:3000
Accept: application/json
Authorization: Bearer 303Xs5g4co7glr4xtJHXHvbNI4Pl0y1hgyZZWOENHMx
```

**Resposta com sucesso**

```
HTTP/1.1 200 OK
Content-Type: application/json

[
  {
		"id": 1,
		"aluno": 1,
		"professor": 2,
		"nome_aluno": "Carlos Silva",
		"nome_professor": "João Paulo",
		"dia_da_aula": "02/10/2024",
		"horario_de_inicio": "14:00:00",
		"horario_de_termino": "15:00:00",
		"numero_de_horas": 1,
		"preco": 60.0,
		"status": "Aceita",
		"descricao_da_aula": "aula de Matemática, especificamente Progressão Aritmética",
		"created_at": "2024-09-14T16:24:36.567641Z",
		"updated_at": "2024-09-14T16:25:09.933616Z"
	},
	{
		"id": 2,
		"aluno": 2,
		"professor": 3,
		"nome_aluno": "Jhonatan Rodrigues",
		"nome_professor": "Lucas Souza",
		"dia_da_aula": "03/10/2024",
		"horario_de_inicio": "17:00:00",
		"horario_de_termino": "19:00:00",
		"numero_de_horas": 2,
		"preco": 60.0,
		"status": "Aceita",
		"descricao_da_aula": "aula de Matemática, especificamente Progressão Aritmética",
		"created_at": "2024-09-14T17:07:47.250685Z",
		"updated_at": "2024-09-14T17:07:47.278354Z"
	}
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
<a id="rota-get-api-professores-aulas-aula-id"></a>

## Rota GET /api/professores/aulas/{aula_id}

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

| Status Code | Descrição                      |
| ----------- | ------------------------------ |
| 200         | Listagem realizada com sucesso |
| 401         | Token inválido                 |

**Body**

| Campo              | Tipo   | Descrição           | Exemplo                    |
| ----------------   | ------ | ------------------- | -------------------------- |
| id                 | int    | ID da aula          | 1                          |
| aluno              | int    | ID do aluno         | 2                          |
| professor          | int    | ID do professor     | 1                          |
| aluno_nome         | string | Nome do aluno       | 'Carlos Souza'             |
| professor          | int    | Nome do professor   | 'João Silva'               |
| dia_da_aula        | string | Data da aula        | "16/09/2024"               |
| horario_de_inicio  | string | Hórario de inicio   | "14:00:00"                 |
| horario_de_termino | string | Hórario de termino  | "15:00:00"                 |
| numero_de_horas    | int    | duração da aua      | 1                          |
| preco              | float  | preco da aula       | 60.00                      |
| status             | string | status da aula      | "Pendente"                 |
| descricao_da_aula  | string | descricao da aula   | "Aula de função afim"      |
| created_at         | string | Data de criação     | "2020-10-10T10:00:00.000Z" |
| updated_at         | string | Data de atualização | "2020-10-10T10:00:00.000Z" |

### Exemplos

**Requisição**

```
GET /api/professores/aulas/1 HTTP/1.1
Host: localhost:3000
Accept: application/json
Authorization: Bearer 303Xs5g4co7glr4xtJHXHvbNI4Pl0y1hgyZZWOENHMx
```

**Resposta com sucesso**

```
HTTP/1.1 200 OK
Content-Type: application/json


{
	"id": 1,
	"aluno": 1,
	"professor": 2,
	"nome_estudante": "Carlos Silva",
	"nome_professor": "João Paulo",
	"dia_da_aula": "02/10/2024",
	"horario_de_inicio": "14:00:00",
	"horario_de_termino": "15:00:00",
	"numero_de_horas": 1,
	"preco": 60.0,
	"status": "Aceita",
	"descricao_da_aula": "aula de Matemática, especificamente Progressão Aritmética",
	"created_at": "2024-09-14T16:24:36.567641Z",
	"updated_at": "2024-09-14T16:25:09.933616Z"
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
