# Autenticação

## Modo de autenticação

A autenticação é realizada por meio de uma combinação de usuário e senha. Caso a autenticação seja realizada com sucesso, o cliente receberá um token válido para a sessão por um tempo determinado, conforme descrito na [documentação de login](#login) 

O nome do usuário e a senha são gerados através de um cadastro feito junto à Quero Educação. Para mais informações, contate seu Key Account Manager.


## Requisição sem token

```
Ausência de Token
Status Code: 401 Unauthorized
www-authenticate: 'Token realm="StockIntegration"'
```

Em caso de requisição sem o envio do token, é retornado status `401 - Unauthorized`.

## Requisição com token inválido

```
Formato de token inválido
Status Code: 400 Bad Request
```

Em caso de token em formato inválido, é retornado status `400 - Bad Request`.

## Requisição com token não autorizado

```
Não autorizado
Status Code: 403 Forbidden
```

Em caso de token não autorizado, é retornado erro `403 - Forbidden`.

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

Em caso de token válido mas sem permissão de acesso ao recurso específico, é retornado o status `200 - OK` com mensagem de erro no payload.

# Login

A sessão é criada por meio da autenticação utilizando uma combinação de usuário e senha. Caso seja autenticado com sucesso, o cliente recebe um _token_ válido por 4 horas. Após este período, o _token_ expira e um novo _token_ deve ser solicitado.

É necessário enviar este _token_  no cabeçalho das requisições para ter permissão de executar as solicitações desta API.

## Iniciar uma sessão

> Exemplo de requisição

```shell
curl -X POST "https://querobolsa.com.br/api/sessions" \
  -H 'Content-Type: application/json' \
  -d '{
    "authentication": {
      "username": "teste@teste.com",
      "password": "teste123!"
    }
  }'
```

> Exemplo de retorno JSON para esta requisição:

```json
{
  "access_token": "qPWFZr3CSX52SLeUWdP9XXL5"
}
```

É necessário enviar uma requisição com o `username` e `password` para iniciar uma sessão.

A resposta da requisição traz o token da sessão, que ficará válido por 4 horas. Esse token precisará estar presente no campo `Authorization` no cabeçalho das outras ações da API.

### Parâmetros para criar uma sessão

| Nome | Tipo | Descrição |
| ---- | ---- | --------- |
| session | object | Objeto com dados das credenciais para login |
| username | sting | Nome de usuário para login fornecido pelo Quero Bolsa |
| password | sting | Senha para login fornecido pelo Quero Bolsa |

<aside class="notice">Lembrete - Troque o <code>username</code> e <code>password</code> pelas credenciais fornecidas pela Quero Educação.</aside>

### Parâmetros da resposta

| Nome | Tipo | Descrição |
| ---- | ---- | --------- |
| access_token | sting | Token de acesso da sessão |
