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
curl "https://querobolsa.com.br/api/courses" \
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
      "campus_id": 102,
      "name": "MBA em Auditoria",
      "level": "Pós-graduação Lato Sensu",
      "kind": "EaD",
      "shift": "Virtual",
      "period_kind": "mes",
      "max_periods": 6
    },
    {
      "id": 809,
      "campus_id": 7024,
      "name": "Direito",
      "level": "Bacharelado (graduação)",
      "kind": "Presencial",
      "shift": "Noite",
      "period_kind": "semestre",
      "max_periods": 10
    }
  ]
}
```

Lista todos os cursos disponibilizados pela universidade.

Cursos são retornados em páginas de até 1000 elementos, ordenadas pela última criação realizada. Se houver mais resultados, `has_more` retorna `true` indicando que é possível usar o parâmetro `ending_before` para consultar objetos antecessores à lista atual. Para mais informações, consulte a [seção de paginação](#paginacao).

### Requisição HTTP

`GET https://querobolsa.com.br/api/courses`

### Parâmetros da resposta

| Nome | Tipo | Descrição |
| ---- | ---- | --------- |
| has_more | boolean | Indica se há mais elementos disponíveis antes ou após essa página |
| items | object array | Arranjo de objetos com dados de curso |
| id | integer | Código identificador de curso |
| campus_id | integer | Código identificador de campus |
| name | string | Nome do curso |
| level | string | Grau do curso. Mais informações sobre esse atributo [aqui](#grau-level) |
| kind | string | Modalidade do curso. Mais informações sobre esse atributo [aqui](#modalidade-kind) |
| shift | string | Turno do curso. Mais informações sobre esse atributo [aqui](#turno-shift) |
| period_kind | string | Periodicidade do curso. Mais informações sobre esse atributo [aqui](#periodicidade-period_kind) |
| max_periods | string | Quantidade de periodicidade. Mais informações sobre esse atributo [aqui](#periodicidade-period_kind) |

## Listar cursos de um campus

> Exemplo de requisição

```shell
curl "https://querobolsa.com.br/api/courses?campus_id=102" \
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
      "campus_id": 102,
      "name": "MBA em Auditoria",
      "level": "Pós-graduação Lato Sensu",
      "kind": "EaD",
      "shift": "Virtual",
      "period_kind": "mes",
      "max_periods": 6
    }
  ]
}
```

Esse endpoint lista todos os cursos de um determinado campus, cujo é enviado o ID como parâmetro da requisição.

Cursos são retornados em páginas de até 1000 elementos, ordenadas pela última criação realizada. Se houver mais resultados, `has_more` retorna `true` indicando que é possível usar o parâmetro `ending_before` para consultar objetos antecessores à lista atual. Para mais informações, consulte a [seção de paginação](#paginacao).

### Requisição HTTP

`GET https://querobolsa.com.br/api/courses?campus_id=<CAMPUS_ID>`

### Parâmetros da requisição

| Nome | Tipo | Descrição |
| ---- | ---- | --------- |
| CAMPUS_ID | query | ID do campus onde deseja resgatar cursos |

### Parâmetros da resposta

| Nome | Tipo | Descrição |
| ---- | ---- | --------- |
| has_more | boolean | Indica se há mais elementos disponíveis antes ou após essa página |
| items | object array | Arranjo de objetos com dados de curso |
| id | integer | Código identificador de curso |
| campus_id | integer | Código identificador de campus |
| name | string | Nome do curso |
| level | string | Grau do curso. Mais informações sobre esse atributo [aqui](#grau-level) |
| kind | string | Modalidade do curso. Mais informações sobre esse atributo [aqui](#modalidade-kind) |
| shift | string | Turno do curso. Mais informações sobre esse atributo [aqui](#turno-shift) |
| period_kind | string | Periodicidade do curso. Mais informações sobre esse atributo [aqui](#periodicidade-period_kind) |
| max_periods | string | Quantidade de periodicidade. Mais informações sobre esse atributo [aqui](#periodicidade-period_kind) |

## Informações de um curso específico

> Exemplo de requisição

```shell
curl "https://querobolsa.com.br/api/courses/253" \
  -H 'Authorization: Bearer ##########' \
  -H 'Content-Type: application/json'
```

> Exemplo de retorno JSON para esta requisição

```json
{
  "id": 253,
  "campus_id": 102,
  "name": "MBA em Auditoria",
  "level": "Pós-graduação Lato Sensu",
  "kind": "EaD",
  "shift": "Virtual",
  "period_kind": "mes",
  "max_periods": 6
}
```

Esse endpoint traz informações de um curso específico.

### Requisição HTTP

`GET https://querobolsa.com.br/api/courses/<ID>`

### Parâmetros da requisição

| Nome | Tipo | Descrição |
| ---- | ---- | --------- |
| ID | path | ID do curso que deseja resgatar informações |

### Parâmetros da resposta

| Nome | Tipo | Descrição
| ---- | ---- | --------- |
| id | integer | Código identificador de curso |
| campus_id | integer | Código identificador de campus |
| name | string | Nome do curso |
| level | string | Grau do curso. Mais informações sobre esse atributo [aqui](#grau-level) |
| kind | string | Modalidade do curso. Mais informações sobre esse atributo [aqui](#modalidade-kind) |
| shift | string | Turno do curso. Mais informações sobre esse atributo [aqui](#turno-shift) |
| period_kind | string | Periodicidade do curso. Mais informações sobre esse atributo [aqui](#periodicidade-period_kind) |
| max_periods | string | Quantidade de periodicidade. Mais informações sobre esse atributo [aqui](#periodicidade-period_kind) |

## Inserir cursos

> Exemplo de requisição

```shell
curl -X POST "https://querobolsa.com.br/api/courses" \
  -H 'Authorization: Bearer ##########' \
  -H 'Content-Type: application/json' \
  -d @course_data.json
```

> Exemplo da estrutura JSON esperada:

```json
{
  "courses": [
    {
      "campus_id": 7024,
      "name": "Direito",
      "level": "Bacharelado (graduação)",
      "kind": "Presencial",
      "shift": "Noite",
      "period_kind": "semestre",
      "max_periods": 10
    },
    {
      "campus_id": 102,
      "name": "MBA em Auditoria",
      "level": "Pós-graduação Lato Sensu",
      "kind": "EaD",
      "shift": "Virtual",
      "period_kind": "mes",
      "max_periods": 6
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

### Requisição HTTP

`POST https://querobolsa.com.br/api/courses/`

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

### Parâmetros da resposta

| Nome | Tipo | Descrição |
| ---- | ---- | --------- |
| error | boolean | Indicador de ocorrência de erro na operação |
| operation_id | string | ID da operação de estoque criada |
