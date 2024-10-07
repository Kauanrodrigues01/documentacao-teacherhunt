# AL08 - Listagem de aulas de um aluno

## Rotas

| Rota                            | Método | Descrição                         |
| ------------------------------- | ------ | --------------------------------- |
| /api/alunos/aulas               | GET    | Lista as aulas de um aluno        |
| /api/alunos/aulas/{aula_id}     | GET    | Detahes de uma aula               |

## links para visualização das rotas:
➤ [GET /api/alunos/aulas](#rota-get-api-alunos-aulas) </br>
➤ [GET /api/alunos/aulas/{aula_id}](#rota-get-api-alunos-aulas-detail)

<a id="rota-get-api-alunos-aulas"></a>

## Rota GET /api/alunos/aulas

### Requisição

**Query Parameters**

| Nome   | Tipo   | Descrição                         | Exemplo    |
| ------ | ------ | --------------------------------- | ---------- |
| status | string | Busca pelo status da aula         | pendente   |

- valores aceitos:
- "pendente"
- "aceita"
- "cancelada"

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
| 200         | Aulas retornadas com sucesso     |
| 401         | Token inválido                   |

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
GET /api/alunos/aulas HTTP/1.1
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
        "id": 1,
        "aluno": 1,
        "professor": 1,
        "nome_aluno": "João da Silva",
        "nome_professor": "Carlos Augusto",
        "dia_da_aula": "16/09/2024",
        "horario_de_inicio": "19:00:00",
        "horario_de_termino": "21:00:00",
        "numero_de_horas": 2,
        "preco": 100.0,
        "status": "Pendente",
        "descricao_da_aula": "Aula de função afim",
        "created_at": "2024-09-15T22:48:57.797808Z",
        "updated_at": "2024-09-15T22:48:57.813858Z"
    },
    {
        "id": 2,
        "aluno": 1,
        "professor": 5,
        "nome_aluno": "João da Silva",
        "nome_professor": "Antonio Carlos",
        "dia_da_aula": "17/09/2024",
        "horario_de_inicio": "18:00:00",
        "horario_de_termino": "20:00:00",
        "numero_de_horas": 2,
        "preco": 200.0,
        "status": "Cancelada",
        "descricao_da_aula": "Aula de função afim",
        "created_at": "2024-09-15T22:48:57.797808Z",
        "updated_at": "2024-09-15T22:48:57.813858Z"
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

<a id="rota-get-api-alunos-aulas-detail"></a>

## Rota GET /api/alunos/aulas/{aula_id}

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
GET /api/alunos/aulas/3 HTTP/1.1
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
    "id": 3,
    "aluno": 5,
    "professor": 22,
    "nome_aluno": "João da Silva",
    "nome_professor": "Carlos Augusto",
    "dia_da_aula": "22/10/2024",
    "horario_de_inicio": 07:00:00",
    "horario_de_termino": "09:00:00",
    "numero_de_horas": 2,
    "preco": 100.0,
    "status": "Aceita",
    "descricao_da_aula": "Aula de função afim",
    "created_at": "2024-09-15T22:48:57.797808Z",
    "updated_at": "2024-09-15T22:48:57.813858Z"
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