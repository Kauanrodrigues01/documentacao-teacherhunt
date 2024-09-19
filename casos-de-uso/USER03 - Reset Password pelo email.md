# USER02 - Reset Password by email

## Rotas

| Rota                                       | Método | Descrição                                         |
| ------------------------------------------ | ------ | ------------------------------------------------- |
| /api/auth/password-reset-request           | POST   | Manda uma requisição com link para o email        |
| /api/auth/password-reset/<uidb64>/<token>  | GET    | Checa se o token enviado é válido, retorna o token|
| /api/auth/password-reset-complete          | PATCH  | Redefine a senha passando o token e o uidb64      |

## Rota POST /api/auth/password-reset-request

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
	"sucesso": "Foi enviado um email com o link de redefinição de senha."
}

### Exemplos

**Requisição**

```
POST /api/auth/password-reset-request HTTP/1.1
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
	"sucesso": "Foi enviado um email com o link de redefinição de senha."
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

## Rota GET /api/auth/password-reset/<uidb64>/<token>

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

{
    "message": "Credenciais válidas",
    "uidb64": "MjI",
    "token": "cdlgrx-e80b2978d2eef8f33e9248b7e20808dd"
}

### Exemplos

**Requisição**

```
GET /api/auth/password-reset-request/<uidb64>/<token>  HTTP/1.1
Host: localhost:3000
Content-Type: application/json
Accept: application/json
```

**Resposta com sucesso**

```
HTTP/1.1 200 OK
Content-Type: application/json

{
    "message": "Credenciais válidas",
    "uidb64": "MjI",
    "token": "cdlgrx-e80b2978d2eef8f33e9248b7e20808dd"
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

## Rota PATCH /api/auth/password-complete

### Requisição

**Query Parameters**

Não se aplica

**Headers**

Não se aplica

**Body**

| Campo                 | Tipo   | Descrição                                            | Exemplo                   |
| --------------------- | ------ | -------------------------------------------          | ------------------------- |
| password              | string | Nova senha                                           | "@NewPassword44"          |
| password_confirmation | string | Confirmação de senha                                 | "@NewPassword44"          |
| uidb64                | string | id codificado, retonado no email e na rota anterior  | "MjI"                     |
| token                 | string | Token retornado no email e na rota anterior          | "cdlgpx-095861c7c854f..." |

### Resposta

**Status Code**

| Status Code | Descrição                            |
| ----------- | ------------------------------------ |
| 200         | Senha redefinida com sucesso         |
| 401         | Erro de validação                    |

**Body**

{
	"password": "@Teste111",
	"password_confirmation": "@Teste111",
	"uidb64": "MjI",
	"token": "cdlgpx-095861c7c854f..."
}

### Exemplos

**Requisição**

```
PATCH /api/auth/password-reset-complete  HTTP/1.1
Host: localhost:3000
Content-Type: application/json
Accept: application/json
```

**Resposta com sucesso**

```
HTTP/1.1 200 OK
Content-Type: application/json

{
	"message": "Senha redefinida com sucesso."
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
		"password": [
			"As senhas não conferem.",
			"A senha deve ter no mínimo 8 caracteres.",
			"A senha deve conter pelo menos uma letra maiúscula.",
			"A senha deve conter pelo menos um caractere especial (@, #, $, %, etc.)."
		]
	}
}
```

HTTP/1.1 400 Bad Request
Content-Type: application/json

{
	"message": "Erro de validação",
	"status": 400,
	"error": "Bad Request",
	"cause": "ValidationError",
	"errors": {
		"token": [
			"Token inválido, solicite um novo."
		]
	}
}
```