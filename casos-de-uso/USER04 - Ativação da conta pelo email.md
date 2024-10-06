# USER02 - Ativação da conta pelo email

## Rotas

| Rota                                       | Método | Descrição                                         |
| ------------------------------------------ | ------ | ------------------------------------------------- |
| /api/auth/send-request-active-user         | POST   | Manda uma requisição com link para o email        |
| /api/auth/active-user/{uidb64}/{token}     | GET    | Ativa a conta do usuário passando o uidb64 e token|

## Rota POST /api/auth/send-request-active-user

### Requisição

**Query Parameters**

Não se aplica

**Headers**

Não se aplica

**Body**

| Campo                 | Tipo   | Descrição                                  | Exemplo                   |
| --------------------- | ------ | -------------------------------------------| ------------------------- |
| email                 | string | Email do usuario                           | "joao@mail.com"           |

### Resposta

**Status Code**

| Status Code | Descrição                        |
| ----------- | -------------------------------- |
| 200         | Email enviado com sucesso        |
| 400         | Erro de validação                |

**Body**

{
	"message": "Foi enviado um email com link para ativação da conta."
}

### Exemplos

**Requisição**

```
POST /api/auth/send-request-active-user HTTP/1.1
Host: localhost:3000
Content-Type: application/json
Accept: application/json

{
	"email": "joao@gmail.com"
}
```

**Resposta com sucesso**

```
HTTP/1.1 200 OK
Content-Type: application/json

{
	"message": "Foi enviado um email com link para ativação da conta."
}
```

**Respostas com erro de validação**

```
HTTP/1.1 400 Bad Request
Content-Type: application/json

{
    "message": "Erro de validação",
    "status": 400,
    "error": "Bad Request",
    "cause": "ValidationError",
    "errors": {
        "email": [
            "Email não encontrado"
        ]
    }
}
```

```
HTTP/1.1 400 Bad Request
Content-Type: application/json

{
	"message": "Erro de validação",
	"status": 400,
	"error": "Bad Request",
	"cause": "ValidationError",
	"errors": {
		"email": [
			"Insira um endereço de email válido."
		]
	}
}
```

## Rota GET /api/auth/active-user/{uidb64}/{token}

### Requisição

**Query Parameters**

Não se aplica

**Headers**

Não se aplica

**Body**

Não se aplica

### Resposta

**Status Code**

| Status Code | Descrição                            |
| ----------- | ------------------------------------ |
| 200         | As credenciais são validas           |
| 401         | O token passado na url não é valido  |

**Body**

Não se aplica

### Exemplos

**Requisição**

```
GET /api/auth/active-user/{uidb64}/{token}  HTTP/1.1
Host: localhost:3000
Content-Type: application/json
Accept: application/json
```

**Resposta com sucesso**

```
HTTP/1.1 200 OK
Content-Type: application/json

{
    "message": "Conta ativada com sucesso!"
}
```

**Respostas com erro de autorização**

```
HTTP/1.1 400 Bad Request
Content-Type: application/json

{
    "message": "Erro desconhecido",
    "status": 401,
    "error": "Unauthorized",
    "cause": "NotAuthenticated",
    "errors": {
        "error": "Token inválido, solicite um novo."
    }
}
```