# AL10 - Avaliar Professor

## Rotas

| Rota                                            | Método | Descrição                                        |
| ----------------------------------------------- | ------ | ------------------------------------------------ |
| /api/alunos/avaliar-professor                   | POST   | Cria uma avaliação sobre aquele professor        |

## Rota POST /api/alunos/avaliar-professor

### Requisição

**Query Parameters**

Não se aplica

**Headers**

| Campo         | Tipo   | Descrição       | Exemplo                                              |
| ------------- | ------ | --------------- | ---------------------------------------------------- |
| Authorization | string | Token de acesso | "Bearer 303Xs5g4co7glr4xtJHXHvbNI4Pl0y1hgyZZWOENHMx" |

**Body**

| Campo            | Tipo   | Descrição                                 | Exemplo                                             |
| ---------------- | ------ | ----------------------------------------- | -----------------------------------                 |
| professor        | int    | ID do professor a ser avaliado            | 1                                                   |
| avaliacao        | float  | avaliacao do professor                    | 4.3                                                 |
| comentario       | string | Comentário sobre o professor              | "Um ótimo professor, didática perfeita"             |

**Regras de validação:**
`professor`: Obrigatório, Deve ser um id valido de um professor
`avaliacao`: Obrigatório, Um numero entre 0 e 5
`comentario`: Obrigatório, Não pode ser nulo, nem vazio, mínimo 10 caracteres

### Resposta

**Status Code**

| Status Code | Descrição                        |
| ----------- | -------------------------------- |
| 200         | Avaliacao adicionada com sucesso |
| 401         | Token inválido                   |
| 400         | Erro de validação                |

**Body**

{
	"message": "Professor avaliado com sucesso."
}

### Exemplos

**Requisição**

```
POST /api/alunos/avaliar-professor HTTP/1.1
Host: localhost:3000
Content-Type: application/json
Accept: application/json
Authorization: Bearer 303Xs5g4co7glr4xtJHXHvbNI4Pl0y1hgyZZWOENHMx

{
	"professor": 2,
	"avaliacao": 5,
	"comentario": "Um ótimo professor"
}
```

**Resposta com sucesso**

```
HTTP/1.1 200 OK
Content-Type: application/json

{
	"message": "Professor avaliado com sucesso."
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

**Resposta com erro de validação:**

```
HTTP/1.1 400 Bad Request
Content-Type: application/json

{
	"message": "Erro de validação",
	"status": 400,
	"error": "Bad Request",
	"cause": "ValidationError",
	"errors": {
		"error": [
			"Você já avaliou este professor."
		],
		"avaliacao": [
			"A nota deve ser um valor entre 0 e 5."
		],
		"comentario": [
			"O comentário deve ter no mínimo 10 caracteres."
		]
	}
}
```

