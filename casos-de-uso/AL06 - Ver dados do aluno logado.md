# AL04 - Ver dados do aluno logado

## Rotas

| Rota                            | Método | Descrição                    |
| ------------------------------- | ------ | ---------------------------- |
| /api/alunos/me                  | GET    | Ver dados do aluno logado    |

## Rota GET /api/alunos/me

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
| nome             | string | Nome do aluno                             | "João da Silva"                                     |
| email            | string | Email do aluno                            | "joao@mail.com                                      |
| foto_perfil      | string | Foto de perfil do aluno                   | "https://github.com/joao_silva.png"                 |
| created_at       | string | Data de criação                           | "2020-10-10T00:00:00.000Z"                          |
| updated_at       | string | Data de atualização                       | "2020-10-10T00:00:00.000Z"                          |

### Exemplos

**Requisição**

```
GET /api/alunos/me HTTP/1.1
Host: localhost:3000
Content-Type: application/json
Accept: application/json
```

**Resposta com sucesso**

```
HTTP/1.1 200 OK
Content-Type: application/json

{
	"id": 1,
	"nome": "João da Silva",
	"email": "joao@gmail.com",
	"foto_perfil": "/media/students_image/image_2_jT6ooQi.jpeg",
	"created_at": "2024-09-14T14:35:58.710917Z",
	"updated_at": "2024-09-14T21:43:07.606220Z"
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