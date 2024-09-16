# PR04 - Aceitar ou cancelar uma solicitação de aula

Abaixo você encontrará todas as informações necessárias para a implementação do caso de uso **Listagem de Alunos**.

## Rotas

| Rota                                         | Método | Descrição                                         |
| -------------------------------------------- | ------ | ------------------------------------------------- |
| /api/professores/aulas/aceitar/{aula_id}     | POST   | Aceitar uma solicitação de aula                   |
| /api/professores/aulas/cancelar/{aula_id}    | POST   | Cancelar/Recusar uma solicitação de aula          |

## Rota POST /api/professores/aulas/aceitar/{aula_id}

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
| 200         | Aula aceita com sucesso        |
| 401         | Token inválido                 |

**Body**

Não se aplica

### Exemplos

**Requisição**

```
POST /api/professores/aulas/aceitar/1 HTTP/1.1
Host: localhost:3000
Accept: application/json
Authorization: Bearer 303Xs5g4co7glr4xtJHXHvbNI4Pl0y1hgyZZWOENHMx
```

**Resposta com sucesso**

```
HTTP/1.1 200 OK
Content-Type: application/json

{
	"message": "Aula aceita com sucesso."
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


## Rota POST /api/professores/aulas/cancelar/{aula_id}

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
| 200         | Aula cancelada com sucesso     |
| 401         | Token inválido                 |

**Body**

Não se aplica

### Exemplos

**Requisição**

```
POST /api/professores/aulas/cancelar/1 HTTP/1.1
Host: localhost:3000
Accept: application/json
Authorization: Bearer 303Xs5g4co7glr4xtJHXHvbNI4Pl0y1hgyZZWOENHMx
```

**Resposta com sucesso**

```
HTTP/1.1 200 OK
Content-Type: application/json

{
	"message": "Aula recusada com sucesso."
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
