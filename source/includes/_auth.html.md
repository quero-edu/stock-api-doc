# Autenticação

## Modo de autenticação

A autenticação será feita por sessão de login. O sessão é feita por uma combinação de nome de usuário e senha, cuja é fornecida pelo Quero Bolsa.

Para mais informações, visite a [documentação de login](#login).

## Requisição sem token

```
Ausência de Token
Status Code: 401 Unauthorized
www-authenticate: 'Token realm="StockIntegration"'
```

Em caso de requisição sem o envio do token será retornado status `401 - Unauthorized`.

## Requisição com token inválido

```
Formato de token inválido
Status Code: 400 Bad Request
```

Em caso de token em formato inválido será retornado status `400 - Bad Request`.

## Requisição com token não autorizado

```
Não autorizado
Status Code: 403 Forbidden
```

Em caso de token não autorizado será retornado erro `403 - Forbidden`.

## Requisição com token sem permissão

```
Sem permissão
Status Code: 200 OK
```

```json
{
  "error": true,
  "errors": [{
    "title": "Invalid Permission",
    "detail": "You are not authorized to access this resource with these parameters"
  }]
}
```

Em caso de token válido mas sem permissão de acesso ao recurso específico, retornará o status `200 - OK` com mensagem de erro no payload.

# Login

A sessão é criada por meio de um usuário e senha, ela retornará um token que ficará válido por 4 horas, após esse período ele será expirado.

Será necessário enviar esse token no cabeçalho das requisições para conseguir fazer as ações da API.

## Criar uma sessão

> Requisição

```shell
curl -X POST "https://querobolsa.com.br/api/sessions" \
  -H 'Content-Type: application/json' \
  -d '{
    "session": {
      "username": "teste@teste.com",
      "password": "teste123!"
    }
  }'
```

> O comando acima retorna uma estrutura JSON como essa:

```json
{
  "access_token": "qPWFZr3CSX52SLeUWdP9XXL5"
}
```

É necessário enviar uma requisição com o `username` e `password` para criar uma sessão.

A resposta da requisição traz o token da sessão, que ficará válido por 4 horas. Esse token precisará estar presente no campo `Authorization` no cabeçalho das outras ações da API.

### Parâmetros para criar uma sessão

| Nome | Tipo | Descrição |
| ---- | ---- | --------- |
| session | object | Objeto com dados das credenciais para login |
| username | sting | Nome de usuário para login fornecido pelo Quero Bolsa |
| password | sting | Senha para login fornecido pelo Quero Bolsa |

<aside class="notice">Lembrete - Troque o <code>username</code> e <code>password</code> pelas credenciais fornecidas pelo Quero Bolsa.</aside>

### Parâmetros da resposta

| Nome | Tipo | Descrição |
| ---- | ---- | --------- |
| access_token | sting | Token de acesso da sessão |
