# AL04 - Exclusão de Aluno logado

## Rotas

| Rota                            | Método | Descrição                         |
| ------------------------------- | ------ | --------------------------------- |
| /api/alunos                     | DELETE | Atualizar os dados de um aluno    |

## Rota DELETE /api/alunos

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

| Status Code | Descrição                        |
| ----------- | -------------------------------- |
| 204         | Aluno cadastrado com sucesso     |
| 400         | Erro de validação                |
| 401         | Token inválido                   |

**Body**

Não se aplica

### Exemplos

**Requisição**

```
DELETE /api/alunos HTTP/1.1
Host: localhost:3000
Content-Type: application/json
Accept: application/json
Authorization: Bearer 303Xs5g4co7glr4xtJHXHvbNI4Pl0y1hgyZZWOENHMx
```

**Resposta com sucesso**

```
HTTP/1.1 204 No Content
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