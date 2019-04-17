# Cursos

## Atributos de curso

Alguns campos do curso possuem atributos com um conjunto restrito de valores válidos (_enumeration_). Esta seção aborda estes campos.

### Modalidade `(kind)`

O atributo `kind` indica a modalidade do curso.

De uma forma geral, a modalidade informa a forma que o aluno irá fazer o curso.

Segue a tabela com possíveis valores para esse campo:

| Valor |
| ----- |
| Presencial |
| EaD |
| EaD Mais |
| Flex |
| SEPI |
| Semipresencial |

### Grau `(level)`

O atributo `level` indica o grau do curso.

O grau é o nível do curso oferecido, ou seja, é referente ao título que o aluno irá obter após concluir o curso.

Segue a tabela com possíveis valores para esse campo:

| Valor |
| ----- |
| Licenciatura (graduação) |
| Bacharelado (graduação) |
| Bacharelado + Licenciatura (graduação) |
| Tecnólogo (graduação) |
| Pós-graduação Lato Sensu |
| Mestrado |
| Doutorado |
| Pós-doutorado |
| Técnico |
| Profissionalizante |
| Curso Livre |
| Pré-vestibular |
| Ensino Fundamental |
| Ensino Infantil |
| Ensino Médio |
| Sequencial |
| Segunda Graduação |
| Bootcamp |

### Turno `(shift)`

O atributo `shift` indica o turno do curso.

O turno do curso é o período de dia que o aluno estará cursando.

Segue a tabela com possíveis valores para esse campo:

| Valor |
| ----- |
| Manhã |
| Tarde |
| Noite |
| Integral |
| Virtual |
| Outro |

### Periodicidade `(period_kind)`

O atributo `period_kind` indica a periodicidade do curso.

A peridicidade é a forma como o curso está dividido e também serve para informar a duração do mesmo quando combinado com o campo `max_periods`, que indica a quantidade dessa periodicidade. Por exemplo: se uma entidade de curso possui o valor `6` no atributo `max_periods` e `semestre` em `period_kind`, isso quer dizer que é um curso com duração de 6 semestres.

Segue a tabela com possíveis valores para esse campo:

| Valor |
| ----- |
| hora |
| dia |
| modulo |
| semanal |
| quinzenal |
| mes |
| trimestre |
| quadrimestre |
| semestre |
| ano |

## Listar cursos

> Exemplo de requisição

```shell
curl "https://stock.querobolsa.com.br/api/universities/1001/courses" \
  -H 'Authorization: Bearer ##########' \
  -H 'Content-Type: application/json'
```

> Exemplo de retorno JSON para esta requisição

```json
{
  "has_more": false,
  "items": [
    {
      "id": 253,
      "campus": {
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
      "name": "MBA em Auditoria",
      "level": "Pós-graduação Lato Sensu",
      "kind": "EaD",
      "shift": "Virtual",
      "period_kind": "mes",
      "max_periods": 6,
      "enrollment_semester": "2019.1",
      "full_price": 299.99,
      "discount_percentage": 50.00,
      "price_with_discount": 149.99,
      "fixed_commercial_discount": 20.00,
      "end_date": "2019-06-30",
      "number_of_installments": 12,
      "extra_warning": "* &bull; Após garantir a bolsa, o aluno deverá entrar em contato com a faculdade pelo número (00) 0000-0000",
      "extra_benefit": "* &bull; Primeira parcela grátis"
    },
    {
      "id": 809,
      "campus": {
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
      },
      "name": "Direito",
      "level": "Bacharelado (graduação)",
      "kind": "Presencial",
      "shift": "Noite",
      "period_kind": "semestre",
      "max_periods": 10,
      "enrollment_semester": "2019.1",
      "full_price": 649.00,
      "discount_percentage": 25.00,
      "price_with_discount": 486.75,
      "regressive_commercial_discount": 10.00,
      "end_date": "2019-03-31",
      "number_of_installments": 60,
      "extra_warning": "* &bull; Após garantir a bolsa, o aluno deverá entrar em contato com a faculdade pelo número (00) 0000-0000",
      "extra_benefit": "* &bull; Primeira mensalidade grátis"
    }
  ]
}
```

Lista todos os cursos disponibilizados pela universidade.

Cursos são retornados em páginas de até 1000 elementos, ordenadas pela última criação realizada. Se houver mais resultados, `has_more` retorna `true` indicando que é possível usar o parâmetro `ending_before` para consultar objetos antecessores à lista atual. Para mais informações, consulte a [seção de paginação](#paginacao).

### Requisição HTTP

`GET https://stock.querobolsa.com.br/api/universities/<UNIVERSITY_ID>/courses`

### Parâmetros da requisição

| Nome | Tipo | Descrição |
| ---- | ---- | --------- |
| UNIVERSITY_ID | query | ID da universidade onde deseja realizar a ação |

### Parâmetros da resposta

| Nome | Tipo | Descrição |
| ---- | ---- | --------- |
| has_more | boolean | Indica se há mais elementos disponíveis antes ou após essa página |
| items | object array | Arranjo de objetos com dados de curso |
| id | integer | Código identificador de curso |
| campus | object | Objeto com dados de campus do curso |
| [campus] id | integer | Código identificador de campus |
| [campus] name | string | Nome do campus |
| [campus] address | string | Endereço do campus |
| [campus] neighborhood | string | Bairro do campus |
| [campus] city | string | Cidade do campus |
| [campus] state | string | Estado do campus |
| [campus] zip_code | string | Código CEP do campus |
| [campus] phone | string | Telefone do campus |
| [campus] latitude | float | Coordenada de latitude do campus |
| [campus] longitude | float | Coordenada de longitude do campus || name | string | Nome do curso |
| level | string | Grau do curso. Mais informações sobre esse atributo [aqui](#grau-level) |
| kind | string | Modalidade do curso. Mais informações sobre esse atributo [aqui](#modalidade-kind) |
| shift | string | Turno do curso. Mais informações sobre esse atributo [aqui](#turno-shift) |
| period_kind | string | Periodicidade do curso. Mais informações sobre esse atributo [aqui](#periodicidade-period_kind) |
| max_periods | string | Quantidade de periodicidade. Mais informações sobre esse atributo [aqui](#periodicidade-period_kind) |
| enrollment_semester | string | Semestre de matrícula do curso |
| full_price | float | Preço do curso sem desconto |
| discount_percentage | float | Porcentagem de desconto do Quero Bolsa |
| price_with_discount | float | Preço do curso com desconto |
| regressive_commercial_discount | float | Desconto regressivo disponibilizado pela universidade. Esta parcela do desconto pode ser alterada ao longo do curso. Quando não fornecido, assume-se 0 |
| fixed_commercial_discount | float | Desconto fixo disponibilizado pela instituição no seu balcão. Esta parcela do desconto não é alterado ao longo do curso. Quando não fornecido, assume-se 0 |
| end_date | string | Data de término da validade da oferta |
| number_of_installments | integer | Número de parcelas que o curso será pago. Caso não informado, será considerado que o curso é pago em mensalidades e na mesma duração do mesmo. |
| extra_warning | string | Avisos sobre a bolsa. Essa informação é adquirida diretamente dos meios de comunicação da faculdade por um time da Quero Educação |
| extra_benefit | string | Benefícios adicionais da bolsa. Essa informação é adquirida diretamente dos meios de comunicação da faculdade por um time da Quero Educação |

## Listar cursos de um campus

> Exemplo de requisição

```shell
curl "https://stock.querobolsa.com.br/api/universities/1001/courses?campus_id=102" \
  -H 'Authorization: Bearer ##########' \
  -H 'Content-Type: application/json'
```

> Exemplo de retorno JSON para esta requisição

```json
{
  "has_more": false,
  "items": [
    {
      "id": 253,
      "campus": {
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
      "name": "MBA em Auditoria",
      "level": "Pós-graduação Lato Sensu",
      "kind": "EaD",
      "shift": "Virtual",
      "period_kind": "mes",
      "max_periods": 6,
      "enrollment_semester": "2019.1",
      "full_price": 299.99,
      "discount_percentage": 50.00,
      "price_with_discount": 149.99,
      "fixed_commercial_discount": 20.00,
      "end_date": "2019-06-30",
      "number_of_installments": 12,
      "extra_warning": "* &bull; Após garantir a bolsa, o aluno deverá entrar em contato com a faculdade pelo número (00) 0000-0000",
      "extra_benefit": "* &bull; Primeira parcela grátis"
    }
  ]
}
```

Esse endpoint lista todos os cursos de um determinado campus, cujo é enviado o ID como parâmetro da requisição.

Cursos são retornados em páginas de até 1000 elementos, ordenadas pela última criação realizada. Se houver mais resultados, `has_more` retorna `true` indicando que é possível usar o parâmetro `ending_before` para consultar objetos antecessores à lista atual. Para mais informações, consulte a [seção de paginação](#paginacao).

### Requisição HTTP

`GET https://stock.querobolsa.com.br/api/universities/<UNIVERSITY_ID>/courses?campus_id=<CAMPUS_ID>`

### Parâmetros da requisição

| Nome | Tipo | Descrição |
| ---- | ---- | --------- |
| UNIVERSITY_ID | query | ID da universidade onde deseja realizar a ação |
| CAMPUS_ID | query | ID do campus onde deseja resgatar cursos |

### Parâmetros da resposta

| Nome | Tipo | Descrição |
| ---- | ---- | --------- |
| has_more | boolean | Indica se há mais elementos disponíveis antes ou após essa página |
| items | object array | Arranjo de objetos com dados de curso |
| id | integer | Código identificador de curso |
| campus | object | Objeto com dados de campus do curso |
| [campus] id | integer | Código identificador de campus |
| [campus] name | string | Nome do campus |
| [campus] address | string | Endereço do campus |
| [campus] neighborhood | string | Bairro do campus |
| [campus] city | string | Cidade do campus |
| [campus] state | string | Estado do campus |
| [campus] zip_code | string | Código CEP do campus |
| [campus] phone | string | Telefone do campus |
| [campus] latitude | float | Coordenada de latitude do campus |
| [campus] longitude | float | Coordenada de longitude do campus |
| name | string | Nome do curso |
| level | string | Grau do curso. Mais informações sobre esse atributo [aqui](#grau-level) |
| kind | string | Modalidade do curso. Mais informações sobre esse atributo [aqui](#modalidade-kind) |
| shift | string | Turno do curso. Mais informações sobre esse atributo [aqui](#turno-shift) |
| period_kind | string | Periodicidade do curso. Mais informações sobre esse atributo [aqui](#periodicidade-period_kind) |
| max_periods | string | Quantidade de periodicidade. Mais informações sobre esse atributo [aqui](#periodicidade-period_kind) |
| enrollment_semester | string | Semestre de matrícula do curso |
| full_price | float | Preço do curso sem desconto |
| discount_percentage | float | Porcentagem de desconto do Quero Bolsa |
| price_with_discount | float | Preço do curso com desconto |
| regressive_commercial_discount | float | Desconto regressivo disponibilizado pela universidade. Esta parcela do desconto pode ser alterada ao longo do curso. Quando não fornecido, assume-se 0 |
| fixed_commercial_discount | float | Desconto fixo disponibilizado pela instituição no seu balcão. Esta parcela do desconto não é alterado ao longo do curso. Quando não fornecido, assume-se 0 |
| end_date | string | Data de término da validade da oferta |
| number_of_installments | integer | Número de parcelas que o curso será pago. Caso não informado, será considerado que o curso é pago em mensalidades e na mesma duração do mesmo. |
| extra_warning | string | Avisos sobre a bolsa. Essa informação é adquirida diretamente dos meios de comunicação da faculdade por um time da Quero Educação |
| extra_benefit | string | Benefícios adicionais da bolsa. Essa informação é adquirida diretamente dos meios de comunicação da faculdade por um time da Quero Educação |

## Informações de um curso específico

> Exemplo de requisição

```shell
curl "https://stock.querobolsa.com.br/api/courses/253" \
  -H 'Authorization: Bearer ##########' \
  -H 'Content-Type: application/json'
```

> Exemplo de retorno JSON para esta requisição

```json
{
  "id": 253,
  "campus": {
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
  "name": "MBA em Auditoria",
  "level": "Pós-graduação Lato Sensu",
  "kind": "EaD",
  "shift": "Virtual",
  "period_kind": "mes",
  "max_periods": 6,
  "enrollment_semester": "2019.1",
  "full_price": 299.99,
  "discount_percentage": 50.00,
  "price_with_discount": 149.99,
  "fixed_commercial_discount": 20.00,
  "end_date": "2019-06-30",
  "number_of_installments": 12,
  "extra_warning": "* &bull; Após garantir a bolsa, o aluno deverá entrar em contato com a faculdade pelo número (00) 0000-0000",
  "extra_benefit": "* &bull; Primeira parcela grátis"
}
```

Esse endpoint traz informações de um curso específico.

### Requisição HTTP

`GET https://stock.querobolsa.com.br/api/universities/<UNIVERSITY_ID>/courses/<COURSE_ID>`

### Parâmetros da requisição

| Nome | Tipo | Descrição |
| ---- | ---- | --------- |
| UNIVERSITY_ID | query | ID da universidade onde deseja realizar a ação |
| COURSE_ID | path | ID do curso que deseja resgatar informações |

### Parâmetros da resposta

| Nome | Tipo | Descrição
| ---- | ---- | --------- |
| id | integer | Código identificador de curso |
| campus | object | Objeto com dados de campus do curso |
| [campus] id | integer | Código identificador de campus |
| [campus] name | string | Nome do campus |
| [campus] address | string | Endereço do campus |
| [campus] neighborhood | string | Bairro do campus |
| [campus] city | string | Cidade do campus |
| [campus] state | string | Estado do campus |
| [campus] zip_code | string | Código CEP do campus |
| [campus] phone | string | Telefone do campus |
| [campus] latitude | float | Coordenada de latitude do campus |
| [campus] longitude | float | Coordenada de longitude do campus || name | string | Nome do curso |
| level | string | Grau do curso. Mais informações sobre esse atributo [aqui](#grau-level) |
| kind | string | Modalidade do curso. Mais informações sobre esse atributo [aqui](#modalidade-kind) |
| shift | string | Turno do curso. Mais informações sobre esse atributo [aqui](#turno-shift) |
| period_kind | string | Periodicidade do curso. Mais informações sobre esse atributo [aqui](#periodicidade-period_kind) |
| max_periods | string | Quantidade de periodicidade. Mais informações sobre esse atributo [aqui](#periodicidade-period_kind) |
| enrollment_semester | string | Semestre de matrícula do curso |
| full_price | float | Preço do curso sem desconto |
| discount_percentage | float | Porcentagem de desconto do Quero Bolsa |
| price_with_discount | float | Preço do curso com desconto |
| regressive_commercial_discount | float | Desconto regressivo disponibilizado pela universidade. Esta parcela do desconto pode ser alterada ao longo do curso. Quando não fornecido, assume-se 0 |
| fixed_commercial_discount | float | Desconto fixo disponibilizado pela instituição no seu balcão. Esta parcela do desconto não é alterado ao longo do curso. Quando não fornecido, assume-se 0 |
| end_date | string | Data de término da validade da oferta |
| number_of_installments | integer | Número de parcelas que o curso será pago. Caso não informado, será considerado que o curso é pago em mensalidades e na mesma duração do mesmo. |
| extra_warning | string | Avisos sobre a bolsa. Essa informação é adquirida diretamente dos meios de comunicação da faculdade por um time da Quero Educação |
| extra_benefit | string | Benefícios adicionais da bolsa. Essa informação é adquirida diretamente dos meios de comunicação da faculdade por um time da Quero Educação |

## Inserir cursos

> Exemplo de requisição

```shell
curl -X POST "https://stock.querobolsa.com.br/api/universities/1001/courses" \
  -H 'Authorization: Bearer ##########' \
  -H 'Content-Type: application/json' \
  -d @course_data.json
```

> Exemplo da estrutura JSON esperada:

```json
{
  "courses": [
    {
      "campus_id": 102,
      "name": "MBA em Auditoria",
      "level": "Pós-graduação Lato Sensu",
      "kind": "EaD",
      "shift": "Virtual",
      "period_kind": "mes",
      "max_periods": 6,
      "enrollment_semester": "2019.1",
      "full_price": 299.99,
      "discount_percentage": 50.00,
      "fixed_commercial_discount": 20.00,
      "regressive_commercial_discount": 10.00,
      "end_date": "2019-06-30",
      "number_of_installments": 12
    },
    {
      "campus_id": 7024,
      "name": "Direito",
      "level": "Bacharelado (graduação)",
      "kind": "Presencial",
      "shift": "Noite",
      "period_kind": "semestre",
      "max_periods": 10,
      "enrollment_semester": "2019.1",
      "full_price": 649.00,
      "price_with_discount": 486.75,
      "regressive_commercial_discount": 10.00,
      "end_date": "2019-03-31"
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

Esse endpoint cria cursos em lote com informações enviadas em JSON.

**Observação:** Na hora da inserção, apenas um dos campos `discount_percentage` ou `price_with_discount` pode ser enviado no mesmo objeto.

### Requisição HTTP

`POST https://stock.querobolsa.com.br/api/universities/<UNIVERSITY_ID>/courses`

### Parâmetros da requisição

| Nome | Tipo | Descrição |
| ---- | ---- | --------- |
| UNIVERSITY_ID | query | ID da universidade onde deseja realizar a ação |

<aside class="notice">
  A resposta da requisição carrega o campo <code>operation_id</code>.

  Para mais informações, acesse a <a href="#operacoes-de-estoque">documentação de operações de estoque</a>.
</aside>

### Parâmetros da requisição

| Nome | Tipo | Descrição |
| ---- | ---- | --------- |
| courses | object array | Arranjo de objetos com dados de curso |
| [courses] campus_id | integer | Código identificador de campus |
| [courses] name | string | Nome do curso |
| [courses] level | string | Grau do curso. Mais informações sobre esse atributo [aqui](#grau-level) |
| [courses] kind | string | Modalidade do curso. Mais informações sobre esse atributo [aqui](#modalidade-kind) |
| [courses] shift | string | Turno do curso. Mais informações sobre esse atributo [aqui](#turno-shift) |
| [courses] period_kind | string | Periodicidade do curso. Mais informações sobre esse atributo [aqui](#periodicidade-period_kind) |
| [courses] max_periods | string | Quantidade de periodicidade. Mais informações sobre esse atributo [aqui](#periodicidade-period_kind) |
| [courses] enrollment_semester | string | Semestre de matrícula do curso |
| [courses] full_price | float | Preço do curso sem desconto |
| [courses] discount_percentage | float | Porcentagem de desconto do Quero Bolsa. |
| [courses] price_with_discount | float | Preço do curso com desconto |
| [courses] regressive_commercial_discount | float | Desconto regressivo disponibilizado pela universidade. Esta parcela do desconto pode ser alterada ao longo do curso. Quando não fornecido, assume-se 0 |
| [courses] fixed_commercial_discount | float | Desconto fixo disponibilizado pela instituição no seu balcão. Esta parcela do desconto não é alterado ao longo do curso. Quando não fornecido, assume-se 0 |
| [courses] end_date | string | Data de término da validade da oferta |
| [courses] number_of_installments | integer | Número de parcelas que o curso será pago. Caso não informado, será considerado que o curso é pago em mensalidades e na mesma duração do mesmo. |

### Parâmetros da resposta

| Nome | Tipo | Descrição |
| ---- | ---- | --------- |
| error | boolean | Indicador de ocorrência de erro na operação |
| operation_id | string | ID da operação de estoque criada |
