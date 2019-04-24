# Paginação

## Exemplo de paginação

> Exemplo de requisição

```shell
curl "https://stock.querobolsa.com.br/api/universities/65605bf0-cad2-4dc2-ae11-65c77bc36508/campuses" \
  -H 'Authorization: Bearer ##########' \
  -H 'Content-Type: application/json'
```

> Exemplo de retorno JSON para esta requisição

```json
{
  "has_more": true,
  "items": [
    {
      "id": "30fe7edb-ef73-4538-912a-26d5126a81a9",
      "university": {
        "id": "65605bf0-cad2-4dc2-ae11-65c77bc36508",
        "name": "UniQuero",
      },
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
      "id": "6cc4aa4f-ef6d-48d0-b73c-cf5c5126fd1c",
      "university": {
        "id": "65605bf0-cad2-4dc2-ae11-65c77bc36508",
        "name": "UniQuero",
      },
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

A API de integração de estoque possui requisições de listagem de dados que podem resgatar quantidades massivas de informação. É utilizada paginação para evitar com que essas requisições não sobrecarreguem o banco de dados.

A API utiliza paginação baseada em cursor atráves dos parâmetros `starting_after` e `ending_before`. Ambos recebem um ID de um dado existente e retorna uma lista com até 1000 elementos no máximo.

Os objetos são retornados ordenados pela data de criação decrescentemente. O parâmetro `ending_before` faz a requisição retornar elementos criados anteriormente ao dado cujo ID foi indicado pelo parâmetro. Em contrapartida, o parâmetro `starting_after` faz a requisição retornar elementos listados criados após o dado cujo ID foi indicado.

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

## Uso do cursor ending_before

> Exemplo de requisição

```shell
curl "https://stock.querobolsa.com.br/api/universities/65605bf0-cad2-4dc2-ae11-65c77bc36508/campuses?ending_before=6cc4aa4f-ef6d-48d0-b73c-cf5c5126fd1c" \
  -H 'Authorization: Bearer ##########' \
  -H 'Content-Type: application/json'
```

> Retorno

```json
{
  "has_more": false,
  "items": [
    {
      "id": "7c11e1d0-1b96-412d-98db-db5fee90492d",
      "university": {
        "id": "65605bf0-cad2-4dc2-ae11-65c77bc36508",
        "name": "UniQuero",
      },
      "name": "São Paulo",
      "address": "Rua Henri Dunant, 203",
      "neighborhood": "Chácara Santo Amaro",
      "city": "São Paulo",
      "state": "SP",
      "zip_code": "04709-110",
      "phone": "(00) 00000000",
      "latitude": -23.198976,
      "longitude": -45.901692
    },
    ...,
    {
      "id": "4ba0104a-fbac-4c67-942c-3fcd96b77a83",
      "university": {
        "id": "65605bf0-cad2-4dc2-ae11-65c77bc36508",
        "name": "UniQuero",
      },
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

## Uso do cursor starting_after

> Exemplo de requisição

```shell
curl "https://stock.querobolsa.com.br/api/universities/65605bf0-cad2-4dc2-ae11-65c77bc36508/campuses?starting_after=7c11e1d0-1b96-412d-98db-db5fee90492d" \
  -H 'Authorization: Bearer ##########' \
  -H 'Content-Type: application/json'
```

> Retorno

```json
{
  "has_more": false,
  "items": [
    {
      "id": "30fe7edb-ef73-4538-912a-26d5126a81a9",
      "university": {
        "id": "65605bf0-cad2-4dc2-ae11-65c77bc36508",
        "name": "UniQuero",
      },
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
      "id": "6cc4aa4f-ef6d-48d0-b73c-cf5c5126fd1c",
      "university": {
        "id": "65605bf0-cad2-4dc2-ae11-65c77bc36508",
        "name": "UniQuero",
      },
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

Assim como avançamos uma página, é possível facilmente retornar a dados anteriores à página atual. Para fazer isso, na próxima requisição o parâmetro `starting_after` precisa ter o ID do primeiro elemento da lista `items`. A requisição e retorno ao lado são referentes ao exemplo [acima](#uso-do-cursor-ending_before).

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
