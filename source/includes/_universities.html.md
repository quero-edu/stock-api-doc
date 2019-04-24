# Universidades

## Listar universidades

> Exemplo de requisição

```shell
curl "https://stock.querobolsa.com.br/api/universities" \
  -H 'Authorization: Bearer ##########' \
  -H 'Content-Type: application/json'
```

> Exemplo de retorno JSON para esta requisição

```json
{
  "has_more": false,
  "items": [
    {
      "id": "65605bf0-cad2-4dc2-ae11-65c77bc36508",
      "name": "UniQuero",
    },
    {
      "id": "f21d030e-b40d-4ecf-a0a3-fd7d2cbd06e5",
      "name": "Faculdade Quero",
    }
  ]
}
```

Lista todas as universidades associadas ao usuário que possui o token de autenticação enviado na requisição.

Universidades são retornadas em páginas de até 1000 elementos, ordenadas pela última criação realizada. Se houver mais resultados, `has_more` retorna `true` indicando que é possível usar o parâmetro `ending_before` para consultar objetos antecessores à lista atual. Para mais informações, consulte a [seção de paginação](#paginacao).

### Requisição HTTP

`GET https://stock.querobolsa.com.br/api/universities`

### Parâmetros da resposta

| Nome | Tipo | Descrição |
| ---- | ---- | --------- |
| id | string | Identificador único de universidade |
| name | string | Nome da universidade |
