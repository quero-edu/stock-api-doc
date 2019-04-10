# Campi

## Listar campi

> Requisição

```shell
curl "https://querobolsa.com.br/api/campuses"
  -H 'Authorization: ##########' \
  -H 'Content-Type: application/json'
```

> O comando acima retorna uma estrutura JSON como essa:

```json
[
  {
    "id": 102,
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
  {
    "id": 7024,
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
```

Esse endpoint lista todos os campi.

### Requisição HTTP

`GET https://querobolsa.com.br/api/campuses`

### Parâmetros da resposta

| Nome | Tipo | Descrição |
| ---- | ---- | --------- |
| id | integer | Código identificador de campus |
| name | string | Nome do campus |
| address | string | Endereço do campus |
| neighborhood | string | Bairro do campus |
| city | string | Cidade do campus |
| state | string | Estado do campus |
| zip_code | string | Código CEP do campus |
| phone | string | Telefone do campus |
| latitude | integer | Coordenada de latitude do campus |
| longitude | integer | Coordenada de longitude do campus |

## Informações de um campus específico

> Requisição

```shell
curl "https://querobolsa.com.br/api/campuses/102"
  -H 'Authorization: ##########' \
  -H 'Content-Type: application/json'
```

> O comando acima retorna uma estrutura JSON como essa:

```json
{
  "id": 102,
  "name": "Caxias",
  "address": "Rua Araão Reis, 1789, Bloco 1",
  "neighborhood": "Centro",
  "city": "Caxias",
  "state": "MA",
  "zip_code": "65604-060",
  "phone": "(00) 00000000",
  "latitude": -23.198976,
  "longitude": -45.901692
}
```

Esse endpoint traz informações de um campus específico.

### Requisição HTTP

`GET https://querobolsa.com.br/api/campuses/<ID>`

### Parâmetros da requisição

| Nome | Tipo | Descrição |
| ---- | ---- | --------- |
| ID | path | ID do campus que deseja resgatar informações |

### Parâmetros da resposta

| Nome | Tipo | Descrição
| ---- | ---- | --------- |
| id | integer | Código identificador de campus |
| name | string | Nome do campus |
| address | string | Endereço do campus |
| neighborhood | string | Bairro do campus |
| city | string | Cidade do campus |
| state | string | Estado do campus |
| zip_code | string | Código CEP do campus |
| phone | string | Telefone do campus |
| latitude | integer | Coordenada de latitude do campus |
| longitude | integer | Coordenada de longitude do campus |

## Inserir campi

> Requisição

```shell
curl -X POST "https://querobolsa.com.br/api/campuses" \
  -H "Authorization: ##########" \
  -H 'Content-Type: application/json' \
  -d @campus_data.json
```

> Exemplo da estrutura JSON esperada:

```json
{
  "campuses": [
    {
      "university_id": 61,
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
    {
      "university_id": 61,
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

> Resposta

```
Status Code: 200 OK
```

```json
{
  "error": false,
  "operation_id": "4e8c23c3-fab1-486d-9c0e-c49301305d94"
}
```

Esse endpoint traz informações de um campus específico.

### Requisição HTTP

`POST https://querobolsa.com.br/api/campuses/`

<aside class="notice">
  A resposta da requisição carrega o campo <code>operation_id</code>.

  Para mais informações, acesse a <a href="#operacoes-de-estoque">documentação de operações de estoque</a>.
</aside>

### Parâmetros da requisição

| Nome | Tipo | Descrição |
| ---- | ---- | --------- |
| campuses | object array | Arranjo de objetos com dados de campus |
| university_id | integer | Código identificador da universidade |
| name | string | Nome do campus |
| address | string | Endereço do campus |
| neighborhood | string | Bairro do campus |
| city | string | Cidade do campus |
| state | string | Estado do campus |
| zip_code | string | Código CEP do campus |
| phone | string | Telefone do campus |
| latitude | integer | Coordenada de latitude do campus |
| longitude | integer | Coordenada de longitude do campus |

### Parâmetros da resposta

| Nome | Tipo | Descrição |
| ---- | ---- | --------- |
| error | boolean | Indicador de ocorrência de erro na operação |
| operation_id | string | ID da operação de estoque criada |
