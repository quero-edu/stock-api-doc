# Campi

## Listar campi

```shell
curl "https://querobolsa.com.br/api/campuses"
  -H "Authorization: ##########"
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

| Nome | Tipo | Descrição
| ---- | ---- | ---------
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

```shell
curl "https://querobolsa.com.br/api/campuses/102"
  -H "Authorization: ##########"
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

| Nome | Tipo | Descrição
| ---- | ---- | ---------
| ID | path | ID do campus que deseja resgatar informações |

### Parâmetros da resposta

| Nome | Tipo | Descrição
| ---- | ---- | ---------
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


