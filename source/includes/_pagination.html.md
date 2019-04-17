# Paginação

## Exemplo de paginação

> Exemplo de requisição

```shell
curl "https://stock.querobolsa.com.br/api/universities/1001/campuses" \
  -H 'Authorization: Bearer ##########' \
  -H 'Content-Type: application/json'
```

> Exemplo de retorno JSON para esta requisição

```json
{
  "has_more": true,
  "items": [
    {
      "id": 12563,
      "name": "Caxias",
      "address": "Rua Araão Reis, 1789, Bloco 1",
      "neighborhood": "Centro",
      "city": "Caxias",
      "state": "MA",
      "zip_code": "65604-060",
      "phone": "(00) 00000000",
      "latitude": -23.198976,
      "longitude": -45.901692
    },
    ...,
    {
      "id": 13563,
      "name": "Sorocaba",
      "address": "Av. Independência, 210",
      "neighborhood": "Éden",
      "city": "Sorocaba",
      "state": "SP",
      "zip_code": "18087-101",
      "phone": "(00) 00000000",
      "latitude": -23.198976,
      "longitude": -45.901692
    }
  ]
}
```

A API utiliza paginação baseada em cursor atráves dos parâmetros `starting_after` e `ending_before`. Ambos recebem um ID de um dado existente e retorna uma lista com até 1000 elementos no máximo.
O parâmetro `ending_before` faz a requisição retornar elementos cujo ID é maior que o indicado pelo parâmetro. Em contrapartida, o parâmetro `starting_after` faz a requisição retornar elementos listados após o dado cujo ID foi indicado.
O atributo `has_more` da resposta indica se há mais dados disponíveis depois dessa página. Se for `false`, significa que é o fim da lista e não há mais dados. Se for `true`, significa que há mais dados a serem resgatados. Após uma requisição utilizando o parâmetro `ending_before`, o atributo `has_more` se refere a possibilidade de retornar mais dados anteriores à página atual.

### Parâmetros de paginação

| Nome | Tipo | Descrição |
| ---- | ---- | --------- |
| starting_after | cursor | Cursor para uso em paginação. Retorna elementos listados após o dado cujo ID foi indicado |
| ending_before | cursor | Cursor para uso em paginação. Retorna elementos listados antes do dado cujo ID foi indicado |

### Informações de resultado de dados com paginação

| Nome | Tipo | Descrição |
| ---- | ---- | --------- |
| has_more | boolean | Indica se há mais elementos disponíveis antes ou após essa página |
| items | array | Lista dos elementos retornados pela requisição |

## Uso do cursor starting_after

> Exemplo de requisição

```shell
curl "https://stock.querobolsa.com.br/api/universities/1001/campuses?starting_after=13562" \
  -H 'Authorization: Bearer ##########' \
  -H 'Content-Type: application/json'
```

> Retorno

```json
{
  "has_more": false,
  "items": [
    {
      "id": 13563,
      "name": "Sorocaba",
      "address": "Av. Independência, 210",
      "neighborhood": "Éden",
      "city": "Sorocaba",
      "state": "SP",
      "zip_code": "18087-101",
      "phone": "(00) 00000000",
      "latitude": -23.198976,
      "longitude": -45.901692
    },
    ...,
    {
      "id": 14202,
      "name": "SP",
      "address": "Av. Marquês de São Vicente, 2900",
      "neighborhood": "Água Branca",
      "city": "São Paulo",
      "state": "SP",
      "zip_code": "05036-040",
      "phone": "(00) 00000000",
      "latitude": -23.198976,
      "longitude": -45.901692
    }
  ]
}
```

No exemplo acima, vimos que `has_more` retornou `true`, portanto existem mais dados a serem resgatados após essa página. Para poder consultá-los, na próxima requisição o parâmetro `starting_after` precisa ter o ID do último elemento da lista `items`. A requisição e retorno ao lado são referentes ao exemplo [acima](#exemplo-de-paginacao).

### Parâmetros de paginação

| Nome | Tipo | Descrição |
| ---- | ---- | --------- |
| starting_after | cursor | Cursor para uso em paginação. Retorna elementos listados após o dado cujo ID foi indicado |
| ending_before | cursor | Cursor para uso em paginação. Retorna elementos listados antes do dado cujo ID foi indicado |

### Informações de resultado de dados com paginação

| Nome | Tipo | Descrição |
| ---- | ---- | --------- |
| has_more | boolean | Indica se há mais elementos disponíveis antes ou após essa página |
| items | array | Lista dos elementos retornados pela requisição |

## Uso do cursor ending_before

> Exemplo de requisição

> Exemplo de requisição

```shell
curl "https://stock.querobolsa.com.br/api/universities/1001/campuses?ending_before=14202" \
  -H 'Authorization: Bearer ##########' \
  -H 'Content-Type: application/json'
```

> Retorno

```json
{
  "has_more": true,
  "items": [
    {
      "id": 13201,
      "name": "BH",
      "address": "Rua Intersindical, 218",
      "neighborhood": "Flávio de Oliveira",
      "city": "Belo Horizonte",
      "state": "MG",
      "zip_code": "18087-101",
      "phone": "(00) 00000000",
      "latitude": -23.198976,
      "longitude": -45.901692
    },
    ...,
    {
      "id": 14201,
      "name": "Campinas",
      "address": "Av. Itatiba, 1427",
      "neighborhood": "Jardim Novo Campos Elíseos",
      "city": "Campinas",
      "state": "SP",
      "zip_code": "13050-545",
      "phone": "(00) 00000000",
      "latitude": -23.198976,
      "longitude": -45.901692
    }
  ]
}
```

Assim como avançamos uma página, é possível facilmente retornar a dados anteriores à página atual. Para fazer isso, na próxima requisição o parâmetro `ending_before` precisa ter o ID do primeiro elemento da lista `items`. A requisição e retorno ao lado são referentes ao exemplo [acima](#uso-do-cursor-starting_after).

### Parâmetros de paginação

| Nome | Tipo | Descrição |
| ---- | ---- | --------- |
| starting_after | cursor | Cursor para uso em paginação. Retorna elementos listados após o dado cujo ID foi indicado |
| ending_before | cursor | Cursor para uso em paginação. Retorna elementos listados antes do dado cujo ID foi indicado |

### Informações de resultado de dados com paginação

| Nome | Tipo | Descrição |
| ---- | ---- | --------- |
| has_more | boolean | Indica se há mais elementos disponíveis antes ou após essa página |
| items | array | Lista dos elementos retornados pela requisição |
