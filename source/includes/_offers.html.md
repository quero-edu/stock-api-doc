# Ofertas

## Listar ofertas

> Exemplo de requisição

```shell
curl "https://querobolsa.com.br/api/offers" \
  -H 'Authorization: Bearer ##########' \
  -H 'Content-Type: application/json'
```

> Exemplo de retorno JSON para esta requisição:

```json
{
  "offers": [
    {
      "id": 1215,
      "course_id": 253,
      "full_price": 299.99,
      "discount_percentage": "50%",
      "price_with_discount": 149.99,
      "enrollment_semester": "2019.1",
      "end_date": "2019-06-30",
      "number_of_installments": 12
    },
    {
      "id": 4984,
      "course_id": 809,
      "full_price": 649.00,
      "discount_percentage": "25%",
      "price_with_discount": 486.75,
      "enrollment_semester": "2019.1",
      "end_date": "2019-03-31",
      "number_of_installments": 60
    }
  ]
}
```

Esse endpoint lista todas as ofertas.

### Requisição HTTP

`GET https://querobolsa.com.br/api/offers`

### Parâmetros da resposta

| Nome | Tipo | Descrição |
| ---- | ---- | --------- |
| offers | object array | Arranjo de objetos com dados de oferta |
| [offers] id | integer | Código identificador de oferta |
| [offers] course_id | integer | Código identificador de curso |
| [offers] full_price | float | Preço do curso sem desconto |
| [offers] discount_percentage | string | Porcentagem de desconto do Quero Bolsa |
| [offers] price_with_discount | float | Preço do curso aplicando o desconto do Quero Bolsa |
| [offers] enrollment_semester | string | Semestre de matrícula do curso |
| [offers] end_date | string | Data de fim da oferta |
| [offers] number_of_installments | integer | Número de parcelas que o curso será pago |

## Listar ofertas de um campus

> Exemplo de requisição

```shell
curl "https://querobolsa.com.br/api/offers?campus_id=102" \
  -H 'Authorization: Bearer ##########' \
  -H 'Content-Type: application/json'
```

> Exemplo de retorno JSON para esta requisição:

```json
{
  "offers": [
    {
      "id": 1215,
      "course_id": 253,
      "full_price": 299.99,
      "discount_percentage": "50%",
      "price_with_discount": 149.99,
      "enrollment_semester": "2019.1",
      "end_date": "2019-06-30",
      "number_of_installments": 12
    }
  ]
}
```

Esse endpoint lista todos os ofertas de um determinado campus, cujo é enviado o ID como parâmetro da requisição.

### Requisição HTTP

`GET https://querobolsa.com.br/api/offers?campus_id=<CAMPUS_ID>`

### Parâmetros da requisição

| Nome | Tipo | Descrição |
| ---- | ---- | --------- |
| CAMPUS_ID | query | ID do campus onde deseja resgatar ofertas |

### Parâmetros da resposta

| Nome | Tipo | Descrição |
| ---- | ---- | --------- |
| offers | object array | Arranjo de objetos com dados de oferta |
| [offers] id | integer | Código identificador de oferta |
| [offers] course_id | integer | Código identificador de curso |
| [offers] full_price | float | Preço do curso sem desconto |
| [offers] discount_percentage | string | Porcentagem de desconto do Quero Bolsa |
| [offers] price_with_discount | float | Preço do curso aplicando o desconto do Quero Bolsa |
| [offers] enrollment_semester | string | Semestre de matrícula do curso |
| [offers] end_date | string | Data de fim da oferta |
| [offers] number_of_installments | integer | Número de parcelas que o curso será pago |

## Informações de uma oferta específica

> Exemplo de requisição

```shell
curl "https://querobolsa.com.br/api/offers/1215" \
  -H 'Authorization: Bearer ##########' \
  -H 'Content-Type: application/json'
```

> Exemplo de retorno JSON para esta requisição:

```json
{
  "id": 1215,
  "course_id": 253,
  "full_price": 299.99,
  "discount_percentage": "50%",
  "price_with_discount": 149.99,
  "enrollment_semester": "2019.1",
  "end_date": "2019-06-30",
  "number_of_installments": 12
}
```

Esse endpoint traz informações de uma oferta específica.

### Requisição HTTP

`GET https://querobolsa.com.br/api/offers/<ID>`

### Parâmetros da requisição

| Nome | Tipo | Descrição |
| ---- | ---- | --------- |
| ID | path | ID da oferta que deseja resgatar informações |

### Parâmetros da resposta

| Nome | Tipo | Descrição |
| ---- | ---- | --------- |
| id | integer | Código identificador de oferta |
| course_id | integer | Código identificador de curso |
| full_price | float | Preço do curso sem desconto |
| discount_percentage | string | Porcentagem de desconto do Quero Bolsa |
| price_with_discount | float | Preço do curso aplicando o desconto do Quero Bolsa |
| enrollment_semester | string | Semestre de matrícula do curso |
| end_date | string | Data de fim da oferta |
| number_of_installments | integer | Número de parcelas que o curso será pago |

## Inserir ofertas

> Exemplo de requisição

```shell
curl -X POST "https://querobolsa.com.br/api/offers" \
  -H 'Authorization: Bearer ##########' \
  -H 'Content-Type: application/json' \
  -d @offer_data.json
```

> Exemplo da estrutura JSON esperada:

```json
{
  "offers": [
    {
      "course_id": 253,
      "full_price": 299.99,
      "discount_percentage": "50%",
      "price_with_discount": 149.99,
      "enrollment_semester": "2019.1",
      "end_date": "2019-06-30",
      "number_of_installments": 12
    },
    {
      "course_id": 809,
      "full_price": 649.00,
      "discount_percentage": "25%",
      "price_with_discount": 486.75,
      "enrollment_semester": "2019.1",
      "end_date": "2019-03-31",
      "number_of_installments": 60
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

Esse endpoint cria ofertas em lote com informações enviadas em JSON.

### Requisição HTTP

`POST https://querobolsa.com.br/api/offers/`

<aside class="notice">
  A resposta da requisição carrega o campo <code>operation_id</code>.

  Para mais informações, acesse a <a href="#operacoes-de-estoque">documentação de operações de estoque</a>.
</aside>

### Parâmetros da requisição

| Nome | Tipo | Descrição |
| ---- | ---- | --------- |
| offers | object array | Arranjo de objetos com dados de oferta |
| [offers] course_id | integer | Código identificador de curso |
| [offers] full_price | float | Preço do curso sem desconto |
| [offers] discount_percentage | string | Porcentagem de desconto do Quero Bolsa |
| [offers] price_with_discount | float | Preço do curso aplicando o desconto do Quero Bolsa |
| [offers] enrollment_semester | string | Semestre de matrícula do curso |
| [offers] end_date | string | Data de fim da oferta |
| [offers] number_of_installments | integer | Número de parcelas que o curso será pago |

### Parâmetros da resposta

| Nome | Tipo | Descrição |
| ---- | ---- | --------- |
| error | boolean | Indicador de ocorrência de erro na operação |
| operation_id | string | ID da operação de estoque criada |
