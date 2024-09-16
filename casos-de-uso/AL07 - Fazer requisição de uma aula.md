# AL03 - Requisição de uma aula

Abaixo você encontrará todas as informações necessárias para a implementação do caso de uso **Cadastro de Aula**.

## Rotas

| Rota                                   | Método | Descrição                        |
| -------------------------------------- | ------ | -------------------------------- |
| /api/alunos/agendar-aulas              | POST   | Cadastra uma solicitação de aula |

## Rota POST /api/alunos/agendar-aulas

### Requisição

**Query Parameters**

Não se aplica

**Headers**

| Campo         | Tipo   | Descrição       | Exemplo                                              |
| ------------- | ------ | --------------- | ---------------------------------------------------- |
| Authorization | string | Token de acesso | "Bearer 303Xs5g4co7glr4xtJHXHvbNI4Pl0y1hgyZZWOENHMx" |

**Body**

| Campo              | Tipo   | Descrição           | Exemplo                    |
| ----------------   | ------ | ------------------- | -------------------------- |
| professor          | int    | ID do professor     | 1                          |
| dia_da_aula        | string | Data da aula        | "16/09/2024"               |
| horario_de_inicio  | string | Hórario de inicio   | "14:00:00"                 |
| numero_de_horas    | int    | duração da aua      | 1                          |
| descricao_da_aula  | string | descricao da aula   | "Aula de função afim"      |

Regras de validação:

- `professor`: obrigatório, ID de um professor válido
- `dia_da_aula`: obrigatório, Dia que o usuário deseja ter a aula
- `horario_de_inicio`: obrigatório, os horarios que são válidos: ['07:00', '08:00', '09:00', '10:00', '11:00', '12:00', '13:00', '14:00', '15:00', '16:00', '17:00', '18:00', '19:00']
- `numero_de_horas`: obrigatório, deve ser um número inteiro positivo, de no máximo 4
- `descricao_da_aula`: Opcional

### Resposta

**Status Code**

| Status Code | Descrição                    |
| ----------- | ---------------------------- |
| 201         | Aula requisitada com sucesso |
| 400         | Erro de validação            |

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
POST /api/alunos/agendar-aulas HTTP/1.1
Host: localhost:3000
Content-Type: application/json
Accept: application/json

{
	"professor": 1,
	"dia_da_aula": "2024-09-16",
	"horario_de_inicio": "19:00",
	"numero_de_horas": 2,
  "descricao_da_aula": "Aula de função afim"
}
```

**Resposta com sucesso**

```
HTTP/1.1 201 Created
Content-Type: application/json

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
    "horario_de_inicio": [
      "Horário inválido. Os horários permitidos são de 07:00 até 19:00 com um intervalo de uma hora."
    ],
    "dia_da_aula": [
      "A data da aula não pode ser no passado."
    ],
    "numero_de_horas": [
      "O número de horas deve ser maior que 0."
    ]
  }
}
```

**Resposta com professor não encontrado**

```
HTTP/1.1 404 Not Found
Content-Type: application/json

{
  "message": "Validation fails",
  "status": 400,
  "error": "Bad Request",
  "cause": "ValidationError",
  "errors": {
    "professor": [
      "Pk inválido \"100\" - objeto não existe."
    ]
  }
}
```
